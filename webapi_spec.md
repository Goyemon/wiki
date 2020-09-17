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

_\*only when there is the geth error_

```json
{
  "Id": "1598836349170",
  "Type": "TransactionError",
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
  "Events": [
    {
      "Contract": "ETH",
      "Action": "Send",
      "Amount": 100
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "DAIToken",
      "Action": "Send",
      "Amount": 100
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "CDAIToken",
      "Action": "Receive",
      "Amount": 100
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "PLDAIToken",
      "Action": "Send",
      "Amount": 100
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
  "Hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "Nonce": 5,
  "GasPrice": 102000000000,
  "GasLimit": 743061,
  "GasUsed": 615586,
  "Timestamp": 1596433159,
  "Status": "Waiting",
  "Events": [
    {
      "Contract": "DAIToken",
      "Action": "Approve",
      "Amount": 100
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "CompoundDAI",
      "Action": "Deposit",
      "Amount": 100
    },
    {
      "Contract": "COMPToken",
      "Action": "Receive",
      "Amount": 132.4
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "CompoundDAI",
      "Action": "Withdraw",
      "Amount": 100
    },
    {
      "Contract": "COMPToken",
      "Action": "Receive",
      "Amount": 132.4
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "PoolTogetherV2WeeklyDAI",
      "Action": "Approve",
      "Amount": 100
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "PoolTogetherV2WeeklyDAI",
      "Action": "Deposit",
      "Amount": 100
    }
  ]
}
```

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
  "Events": [
    {
      "Contract": "PoolTogetherV2WeeklyDAI",
      "Action": "Withdraw",
      "Amount": 100
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
  "Events": [
    {
      "Contract": "UniswapV2",
      "Action": "Swap",
      "ETHSold": 0.2,
      "TokenBought": 100
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
    "EstimatedInterestRate": "025a9386c7a226",
    "Supply": "57dcccd99fe50bcfbdd0",
    "CurrentDrawId": "24",
    "LastWinner": "0fda4ac09a12c10fae30e429f4d6b47c9a83c87e",
    "Winnings": "1add02461d9458875d"
  }
}
```
