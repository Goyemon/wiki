# type

1. [AddressRegistration](#AddressRegistration)
2. [OutgoingTransaction](#OutgoingTransaction)
3. [Balance](#Balance)
4. [TransactionHistory](#TransactionHistory)
5. [ProtocolStats](#ProtocolStats)

<a id="AddressRegistration"></a>

# 1. AddressRegistration

## POST method

```json
{
  "Id": "1898272544408",
  "Type": "AddressRegistration",
  "DeviceId": "4598272544408",
  "Timestamp": 1595433159,
  "Address": "0x1A8026341cB5Ae8B210dD7373cbeD9B12D0F078D"
};
```

<a id="OutgoingTransaction"></a>

# 2. OutgoingTransaction

## POST method

```json
{
  "Type": "OutgoingTransaction",
  "SignedTx": "0xf8890485147d35700083062cc7945d3a536e4d6dbd6114cc1ead35777bab948e364380a4a0712d6800000000000000000000000000000000000000000000002bdd586116b52b000026a01c125c2cb31d38ae8300d3d3434c7a2ef842a172fa6b3cce0e4f2b9e20dfa261a00e9dc555d73d9c308891806cfa428e4694a7a3fa138845284437275dc94ad53c",
  "Nonce": "4"
}
```

## Response

Success:

```json
{
  "Id": "1598836349170",
  "Type": "OutgoingTransaction",
  "TxHash": "0x6ae48a0be3dbf9a8bab3afa42d28cf6e01437c12918483e5c06e15f5581b6cb6"
}
```

Error:

```json
{
  "Id": "1598836349170",
  "Type": "OutgoingTransaction",
  "Error": {
    "Code": -32000,
    "Message": "replacement transaction underpriced"
  },
  "Nonce": "5"
}
```

<a id="Balance"></a>

# 3. Balance

## GET method

```json
{
  "Id": "1498272544408",
  "Type": "Balance",
  "ETH": "fdca34836f1000",
  "DAI": "40b81b3435761c7b83",
  "CDAI": "3e84d010243",
  "PLDAI": "0"
}
```

<a id="TransactionHistory"></a>

# 4. TransactionHistory

## GET method

```json
{
  "Id": "4598272544408",
  "Type": "TransactionHistory",
  "Txes": [{}, {}, {}],
  "Contracts": [
    // a list of contracts an address is associated with
    "7a250d5630b4cf539739df2c5dacb4c659f2488d",
    "5d3a536e4d6dbd6114cc1ead35777bab948e3643"
  ]
}
```

## Transaction Type

- [Transfer](#transfer)
  - [ETHTransfer](#eth_transfer)
  - [DAITransfer](#DAI_transfer)
  - [CDAITransfer](#CDAI_transfer)
  - [PLDAITransfer](#PLDAI_transfer)
- [CompoundDAI](#compound_DAI)
  - [Approve](#approve)
  - [Deposit](#deposit)
  - [Withdraw](#withdraw)
- [PoolTogetherV2WeeklyDAI](#pool_together_v2_weekly_DAI)
  - [Approve](#approve)
  - [Deposit](#deposit)
  - [Withdraw](#withdraw)
- [UniswapV2](#uniswap_v2)
  - [SwapExactETHForTokens](#swap_exact_ETH_for_tokens)
- [Aave](#aave)
  - [Deposit](#deposit)
  - [Withdraw](#withdraw)

<a id="transfer"></a>

## Transfer

<a id="eth_transfer"></a>

### ETHTransfer

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "ETH",
  "Action": "Send",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0xb0ff4734ed5065b904464449719761779d0bb8ffe23a414de3e32455d723ad4c) is an example of the ETHTransfer tx in the mainnet.

<a id="DAI_transfer"></a>

### DAITransfer

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "DAIToken",
  "Action": "Send",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0x1386a3c354a078dc7d6e4c2c5261cc1f9401435e6589f85b1812f2fa3be972db) is an example of the DAITransfer tx in the mainnet.

<a id="CDAI_transfer"></a>

### CDAITransfer

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "CDAIToken",
  "Action": "Receive",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0x2998bbbd74ce820e0ebb362653170a6ddf93327e0f35cc6e36d81ac913d38c7c) is an example of the CDAITransfer tx in the mainnet.

<a id="PLDAI_transfer"></a>

### PLDAITransfer

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "PLDAIToken",
  "Action": "Send",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0x2a927f78f85cbdb55e287c314edd6f64ce64a9c2f294342729cdd375160ccac0) is an example of the PLDAITransfer tx in the mainnet.

<a id="compound_DAI"></a>

## CompoundDAI

<a id="approve"></a>

### Approve

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "DAIToken",
  "Action": "Approve",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0x7f2e54241687e210ddce9f0a3c997e3bdcb96c670a07563938f560fdb7e4a52b) is an example of the Approve tx in the mainnet.

<a id="deposit"></a>

### Deposit

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "CompoundDAI",
  "Action": "Deposit",
  "Amount": 100
}
```

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "COMPToken",
  "Action": "Receive",
  "Amount": 132.4
}
```

[This](https://etherscan.io/tx/0xe262822ffe5cc23adecf32fe2499e8546afb5f82291a7a867ed8646fc3746bea) is an example of the Deposit tx in the mainnet.

<a id="withdraw"></a>

### Withdraw

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Success",
  "Contract": "CompoundDAI",
  "Action": "Withdraw",
  "Amount": 100
}
```

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Success",
  "Contract": "COMPToken",
  "Action": "Receive",
  "Amount": 132.4
}
```

[This](https://etherscan.io/tx/0xf4fc657497d5ede050562cb030ebfeca701533de8604b150d96cf7b27c394e43) is an example of the Withdraw tx in the mainnet.

<a id="pool_together_v2_weekly_DAI"></a>

## PoolTogetherV2WeeklyDAI

<a id="approve"></a>

### Approve

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "PoolTogetherV2WeeklyDAI",
  "Action": "Approve",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0x1c66c185e86ec89f9f81005e34def9e4d5a89095182e391b9bd8a39260369a4a) is an example of the Approve tx in the mainnet.

<a id="deposit"></a>

### Deposit

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "PoolTogetherV2WeeklyDAI",
  "Action": "Deposit",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0xaf33ddf39bb7e870791c8236d8d6e81e18ded0b65729049d911f06381e8833ba) is an example of the Deposit tx in the mainnet.

<a id="withdraw"></a>

### Withdraw

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Contract": "PoolTogetherV2WeeklyDAI",
  "Action": "Withdraw",
  "Amount": 100
}
```

[This](https://etherscan.io/tx/0xde6ef97b0860899a128c28118148a3481a836c033c1beb5e186526d8c36a722e) is an example of the Withdraw tx in the mainnet.

## PoolTogetherV3WeeklyDAI

<a id="approve"></a>

### Approve

```json
{
  "Hash": "0x896046b79ddd418d996854a46da6e380e2925af1323d40a11bf60cee8a842eaa",
  "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "Nonce": 860,
  "GasPrice": 79000000000,
  "GasLimit": 404679,
  "GasUsed": 137662,
  "Amount": "",
  "Time": 1601510881,
  "Events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "DAITokenContract",
      "Eevnt": "Approve",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenOut": "DAI",
      "AmountOut": "100000000000000000000"
    }
  ]
}
```

<a id="deposit"></a>

### Deposit

```json
{
  "Hash": "0x896046b79ddd418d996854a46da6e380e2925af1323d40a11bf60cee8a842eaa",
  "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "Nonce": 860,
  "GasPrice": 79000000000,
  "GasLimit": 404679,
  "GasUsed": 137662,
  "Amount": "",
  "Time": 1601510881,
  "Events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "PoolTogetherV3WeeklyDAI",
      "Eevnt": "Deposited",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "PLDAI",
      "AmountIn": "100000000000000000000",
      "TokenOut": "DAI",
      "AmountOut": "100000000000000000000"
    }
  ]
}
```

<a id="withdraw"></a>

### Withdraw

```json
{
  "Hash": "0x896046b79ddd418d996854a46da6e380e2925af1323d40a11bf60cee8a842eaa",
  "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "Nonce": 860,
  "GasPrice": 79000000000,
  "GasLimit": 404679,
  "GasUsed": 137662,
  "Amount": "",
  "Time": 1601510881,
  "Events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "PoolTogetherV3WeeklyDAI",
      "Eevnt": "InstantWithdrawal",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "DAI",
      "AmountIn": "100000000000000000000",
      "TokenOut": "PLDAI",
      "AmountOut": "100000000000000000000"
    }
  ]
}
```

<a id="award"></a>

### Award

```json
{
  "Hash": "0x896046b79ddd418d996854a46da6e380e2925af1323d40a11bf60cee8a842eaa",
  "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "Nonce": 860,
  "GasPrice": 79000000000,
  "GasLimit": 404679,
  "GasUsed": 137662,
  "Amount": "",
  "Time": 1601510881,
  "Events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "PoolTogetherV3WeeklyDAI",
      "Eevnt": "Award",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "PLDAI",
      "AmountIn": "900000000000000000000"
    }
  ]
}
```

<a id="uniswap_v2"></a>

## UniswapV2

<a id="swap_exact_ETH_for_tokens"></a>

### SwapExactETHForTokens

```json
{
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Success",
  "Contract": "UniswapV2",
  "Action": "Swap",
  "TokenSold": "ETH",
  "SoldAmount": 0.2,
  "TokenBought": "DAI",
  "BoughtAmount": 100
}
```

[This](https://etherscan.io/tx/0xb3a5c1bb73d52679c7cdeb682e27922fbff2885ead4992cd9d1dfc8636ab9626) is an example of the SwapExactETHForTokens tx in the mainnet.

<a id="aave"></a>

## Aave

<a id="deposit"></a>

### Deposit

```json
{
  "Hash": "0x896046b79ddd418d996854a46da6e380e2925af1323d40a11bf60cee8a842eaa",
  "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "Nonce": 860,
  "GasPrice": 79000000000,
  "GasLimit": 404679,
  "GasUsed": 137662,
  "Amount": "",
  "Time": 1601510881,
  "Events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "Aave",
      "Eevnt": "Deposit",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "",
      "AmountIn": "100000000000000000000",
      "TokenOut": "DAI",
      "AmountOut": "100000000000000000000"
    }
  ]
}
```

<a id="withdraw"></a>

### Withdraw

```json
{
  "Hash": "0x896046b79ddd418d996854a46da6e380e2925af1323d40a11bf60cee8a842eaa",
  "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "Nonce": 860,
  "GasPrice": 79000000000,
  "GasLimit": 404679,
  "GasUsed": 137662,
  "Amount": "",
  "Time": 1601510881,
  "Events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "PoolTogetherV3WeeklyDAI",
      "Eevnt": "RedeemUnderlying",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "DAI",
      "AmountIn": "100000000000000000000",
      "TokenOut": "",
      "AmountOut": "100000000000000000000"
    }
  ]
}
```

<a id="ProtocolStats"></a>

# 5. ProtocolStats

## GET method

```json
{
  "Id": "1598272353408",
  "UniswapV2WETHxDAIReserve": {
    "WETHReserve": "23182c3558c93465acc77e",
    "DAIReserve": "15551a05a83ee707125b"
  },
  "CompoundDAILending": {
    "LifetimeEarned": "343691257544659324952969355138285373",
    "CurrentExchangeRate": "206114493664759872537853664",
    "YearlyInterestRate": "6138060200665175331936000"
  },
  "PoolTogetherV3DAIWeekly": {
    "TotalBalance": "aaa588dc84c87367b6a3",
    "EstimatedAwardAmount": "025a9386c7a226",
    "CurrentDrawId": "24",
    "LastWinner": "0x0fda4ac09a12c10fae30e429f4d6b47c9a83c87e",
    "LastAwardAmount": "100000000000000000000"
    // I might want to add some other key-value to calculate the exit fee
  }
}
```

_\*Some information here might be able to get from their API. I will look into it._
