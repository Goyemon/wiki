# Problem

1. **People Don’t Want to Use Volatile Currencies**

   Eth is not a friendly currency for most people as it is volatile. We are not used to using a currency that fluctuates in our daily lives. It's better if users could use a stable coin like Dai everywhere.

2. **It’s Confusing to Use Two Currencies in a Single Transaction**

   On top of that, some people have a hard time understanding why they need to use two different currencies to make a simple transaction. e.g. they need to use Eth to send Dai. They want to pay fees with the currency they are sending. It’s like paying with yuan when you transfer yen to your friend. If they transfer USDC, they’d want to pay with USDC. If they transfer DAI, they’d want to pay with DAI.

3. **Users Need to Continually Replenish Their ETH Balance**

   Users need to continually replenish their ETH balance to pay for network fees even if they have enough tokens. Let's say somebody gets some Eth in the wallet. She swaps that Eth with Dai using the use max button. Then she tried to deposit her Dai into Compound. But she can't. She doesn't have enough eth to pay for a network fee at this point. Another scenarios is when they have only Dai. They just want to deposit Dai to Compound and thus they purchased Dai somewhere. But when they try to deposit Dai, the realize that they need eth as well.

4. **Network Fees Are Expensive**
   Network fees can be ridiculously high especially when executing a contract.

# Solution

With a meta transaction, users can interact with the Ethereum blockchain without holding any Ether. If we integrate our wallet with another meta transaction system, they even pay a network fee for users.

Here is what we offer:

- our users will be able to **pay a network fee with any kind of ERC20 tokens we support**

* our users **don’t have to pay a network fee at all when the protocols we support pay the fees for users** with their meta transaction
  e.g. PoolTogether

In the first iteration, we can focus on paying a network fee with DAI.

# Architecture

[image:25E1E786-AFD9-47C4-AD90-B1D52B14ABEF-16332-00000783E20DE7A9/image.png]

Taken from [OpenZeppelin docs](https://docs.opengsn.org/learn/index.html#client).

- Client: signs & sends meta transaction to relay server
- Relay servers: one for all and all for one
- Paymaster: agrees to refund relay server for gas fees
- Trusted Forwarder: verifies sender signature and nonce
- Recipient contract: sees original sender
- RelayHub: connecting participants trustlessly

* we run our own relayer server but use another serve only when our supported protocols pay a network fee for users or when our server is down
* our smart contract receive transactions from the [Gas Station Network](https://gsn.openzeppelin.com/)
* Before the relay server pays for gas the contract verifies it will get refunded by a Paymaster contract.

- the RelayHub helps clients discover the best third-party relay server when our relay server is down

# Meta Transaction Flow

1. The sender sends parameter data and her signature of that to a relayer.
   _She sign messages (not transactions) containing information(e.g. amount, to address) about a transaction they would like to execute. Her data won’t be tempered with thanks to her signature._
2. The relayer sends the parameter data and the signature to a meta transaction contract.
   _they submit a transaction to the network as if they are the sender, and pay the gas fee._
3. The contract verifies the sender address by decoding the parameter and signature with [the ecrecover method](https://solidity.readthedocs.io/en/v0.6.1/units-and-global-variables.html#mathematical-and-cryptographic-functions) in Solidity.

```solidity
ecrecover(bytes32 hash, uint8 v, bytes32 r, bytes32 s) returns (address)
// recover the address associated with the public key from elliptic curve signature or return zero on error.
```

In this way, the contract can determine the original user. On top of that, it can understand their intent.

4. The meta transaction contract calls any other contract on the public Ethereum chain to process a transaction with the sender address and the data accordingly.

# Signer Implementation

Our goyemon wallet does this.

# Relayer Server Implementation

We want to use [the Gas Station Relayer Network](https://www.opengsn.org) instead of working as a single relayer for censorship resistance.

# Contract Implementation

As I described above, a meta transaction is powered by smart contracts. We will write our own contract. But we make the most out of open-sourced libraries like OpenZeppelin.

Since users interacts with the blockchain through our meta transaction contract as a proxy, no other smart contracts need to change to accept meta transactions. However, proper data needs to be passed to the contract method that is going to be called eventually, which should be done in the front-end.

Also, considering that some protocols pay gas for users in their meta transactions, we will integrate them as well.

_We need to make sure that we comply with EIP1344 to avoid replay attacks._

## Our Own Contract

This support all the transactions from our wallet except the ones that use protocol’s meta transaction.

### RelayHub Contract

There is a _single_ instance of a RelayHub contract in the whole network (we don’t need to deploy our own).

A gas tank of ETH. We have to deposit some. This can be risky considering the price volatility of eth.

At its core, a smart contract is responsible for keeping track of relayers, handling relayed transactions, charging their recipients, and generally ensuring all parties stay honest.

Relayers will advertise their services on this contract, and your users will query it to find the relayer that best suits their purposes.

The other key task RelayHub carries out is the actual relaying of transactions.

### Paymaster Contract

Access control and gas refund logic.
“A paymaster has a gas tank of ETH in the RelayHub and can implement any business logic to decide whether to accept or reject a meta transaction.”
For our access control, we can include only transactions that has a repayment in tokens to our Paymaster contract. OpenZeppelin has [an example contract](https://github.com/opengsn/gsn-paymasters/blob/master/contracts/TokenPaymaster.sol).

### TrustedForwarder Contract

This contract verifies the signature and nonce of the original sender.

### Recipient Contract

You must never use `msg.sender` or `msg.data` directly. On relayed calls, `msg.sender` will be `TrustedForwarder` instead of your user. Inherit from OpenZeppelin’s `BaseRelayRecipient` contract. Their `_msgSender()` method retrieves your original sender’s address.

## Protocol’s Contracts

We can use [the permit method](https://docs.makerdao.com/smart-contract-modules/dai-module/dai-detailed-documentation#built-in-meta-transaction-functionality-of-dai) in MakerDAO's contract.

Some protocols like [Uniswap](https://uniswap.org/docs/v2/technical-considerations/using-permit/) and [PoolTogether](https://docs.pooltogether.com/contracts/overview#gas-station-network) V3 have built-in meta transactions as well. We use their methods if they cover the gas cost. PoolTogether would deploy the “paymaster” smart contract that actually pays the cost of the txs for their contracts methods.

It shouldn’t be difficult to integrate with their contracts. We can use our own relayer to send a transaction to their contract. This way. we can keep track of a transaction state easily.

# Questions

- Can we use meta txes with all the contracts by writing our own?
- When can we use the native permit method of MakerDAO? Only for the transfer?
- How is the latency in meta txes?
- How does a relayer get paid?
- what happens when a contract execution fails?
- When is the final contract method called?
- Can we implement a meta transaction for contracts we’ve not written like the Compound?
- how do we calculate the amount to pay to relayers?

* do we need to have a pool of ETH?
* should we use the GSN or not
