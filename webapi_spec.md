# type

1. [AddressRegistration](#address_registration)
2. [OutgoingTransaction](#outgoing_transaction)
3. [Balance](#balance)
4. [TransactionHistory](#transaction_history)
5. [ProtocolStats](#protocol_stats)

<a id="address_registration"></a>

# 1. AddressRegistration

## POST method

```json
{
  "id": "1898272544408",
  "type": "address_registration",
  "deviceId": "4598272544408",
  "timestamp": 1595433159,
  "address": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D"
};
```

<a id="outgoing_transaction"></a>

# 2. OutgoingTransaction

## POST method

```json
{
  "type": "outgoing_transaction",
  "signed_tx": "0xf8890485147d35700083062cc7945d3a536e4d6dbd6114cc1ead35777bab948e364380a4a0712d6800000000000000000000000000000000000000000000002bdd586116b52b000026a01c125c2cb31d38ae8300d3d3434c7a2ef842a172fa6b3cce0e4f2b9e20dfa261a00e9dc555d73d9c308891806cfa428e4694a7a3fa138845284437275dc94ad53c",
  "nonce": "4"
}
```

## Response

_\*only when there is the geth error_

```json
{
  "id": "1598836349170",
  "type": "transactionError",
  "error": {
    "code": -32000,
    "message": "replacement transaction underpriced"
  },
  "nonce": "5"
}
```

<a id="balance"></a>

# 3. Balance

## GET method

```json
{
  "id": "1498272544408",
  "type": "balance",
  "ETH": "fdca34836f1000",
  "DAI": "40b81b3435761c7b83",
  "CDAI": "3e84d010243",
  "PLDAI": "0"
}
```

<a id="transaction_history"></a>

# 4. TransactionHistory

## GET method

```json
{
  "id": "4598272544408",
  "type": "transaction_history",
  "Txes": [{}, {}, {}],
  "contracts": [
    // a list of contracts an address is associated with
    "7a250d5630b4cf539739df2c5dacb4c659f2488d",
    "5d3a536e4d6dbd6114cc1ead35777bab948e3643"
  ]
}
```

## Transaction Type

- [ETHTransfer](#eth_transfer)
- [TokenTransfer](#token_transfer)
  - [DAITransfer](#DAI_transfer)
  - [CDAITransfer](#CDAI_transfer)
  - [PLDAITransfer](#PLDAI_transfer)
- [CompoundDAI](#compound_DAI)
  - [Approve](#approve)
  - [Mint](#mint)
  - [redeemUnderlying](#redeem_underlying)
- [PoolTogetherV2WeeklyDAI](#pool_together_v2_weekly_DAI)
  - [Approve](#approve)
  - [DepositPool](#deposit_pool)
  - [Withdraw](#withdraw)
- [UniswapV2](#uniswap_v2)
  - [SwapExactETHForTokens](#swap_exact_ETH_for_tokens)

<a id="eth_transfer"></a>

## ETHTransfer

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0.34,
    "Timestamp": 1596433159
  },
  "Status": "Pending"
}
```

<a id="token_transfer"></a>

## TokenTransfer

<a id="DAI_transfer"></a>

### DAITransfer

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0,
    "Timestamp": 1596433159
  },
  "Status": "Pending",
  "Events": [
    {
      "Contract": "DAI_token",
      "Event": "Transfer",
      "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
      "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
      "Value": 1000000000000000000
    }
  ]
}
```

<a id="CDAI_transfer"></a>

### CDAITransfer

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0,
    "Timestamp": 1596433159
  },
  "Status": "Pending",
  "Events": [
    {
      "Contract": "CDAI_token",
      "Event": "Transfer",
      "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
      "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
      "Value": 1000000000000000000
    }
  ]
}
```

<a id="PLDAI_transfer"></a>

### PLDAITransfer

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0,
    "Timestamp": 1596433159
  },
  "Status": "Pending",
  "Events": [
    {
      "Contract": "PLDAI_token",
      "Event": "Transfer",
      "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
      "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
      "Value": 1000000000000000000
    }
  ]
}
```

<a id="compound_DAI"></a>

## CompoundDAI

<a id="approve"></a>

### Approve

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0,
    "Timestamp": 1596433159
  },
  "Status": "Pending",
  "Events": [
    {
      "Contract": "DAI_token",
      "Event": "Approve",
      "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
      "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
      "Value": 1000000000000000000
    }
  ]
}
```

<a id="mint"></a>

### Mint

<a id="redeem_underlying"></a>

### redeemUnderlying

<a id="pool_together_v2_weekly_DAI"></a>

## PoolTogetherV2WeeklyDAI

<a id="approve"></a>

### Approve

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0,
    "Timestamp": 1596433159
  },
  "Status": "Pending",
  "Events": [
    {
      "Contract": "DAI_token",
      "Event": "Approve",
      "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
      "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
      "Value": 1000000000000000000
    }
  ]
}
```

<a id="deposit_pool"></a>

### DepositPool

<a id="withdraw"></a>

### Withdraw

<a id="uniswap_v2"></a>

## UniswapV2

```json
{
  "Object": {
    "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
    "From": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D",
    "To": "0xCfCe97c17886600841fbd8f26Fd8Fa1eDFfe8E6F",
    "Nonce": 5,
    "GasPrice": 102000000000,
    "GasLimit": 743061,
    "GasUsed": 615586,
    "Value": 0,
    "Timestamp": 1596433159
  },
  "Status": "Included",
  "Events": [
    {
      "Contract": "UniswapV2",
      "Event": "Swap",
      "From": "0x5d3a536e4d6dbd6114cc1ead35777bab948e3643",
      "To": "0xe9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "Value": 1000000000000000000
    }
  ]
}
```

<a id="swap_exact_ETH_for_tokens"></a>

### SwapExactETHForTokens

<a id="protocol_stats"></a>

# 5. ProtocolStats

## GET method

```json
{
  "id": "1598272353408",
  "Uniswap_V2_WETHxDAI_reserve": {
    "WETH_reserve": "23182c3558c93465acc77e",
    "DAI_reserve": "15551a05a83ee707125b"
  },
  "Compound_DAI_lending": {
    "lifetime_earned": "343691257544659324952969355138285373",
    "current_exchange_rate": "206114493664759872537853664",
    "yearly_interest_rate": "6138060200665175331936000"
  },
  "PoolTogether_V3_DAI_weekly": {
    "total_balance": "aaa588dc84c87367b6a3",
    "estimated_interest_rate": "025a9386c7a226",
    "supply": "57dcccd99fe50bcfbdd0",
    "current_drawid": "24",
    "last_winner": "0fda4ac09a12c10fae30e429f4d6b47c9a83c87e",
    "winnings": "1add02461d9458875d"
  }
}
```
