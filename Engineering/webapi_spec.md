# type

1. [AddressRegistration](#AddressRegistration)
2. [Login](#Login)
3. [OutgoingTransaction](#OutgoingTransaction)
4. [Balance](#Balance)
5. [TransactionHistory](#TransactionHistory)
6. [ProtocolStats](#ProtocolStats)

<a id="AddressRegistration"></a>

# 1. AddressRegistration

## POST method

```json
{
  "android_device_id": "android_device_id",
  "ios_device_id": "ios_device_id",
  "email": "stereophonics0215@gmail.com",
  "address": "0xCa7A91F3989c8E8CAd46E57ED3eDb3633eD2c31f",
  "network": "ropsten"
}
```

## Response

Success:

```json
{
  "id": "921f5c77-0cfb-11eb-a7dc-0242ac120003",
  "created_at": "2020-10-13T02:26:59.281871Z",
  "updated_at": "2020-10-13T02:26:59.281871Z",
  "android_device_id": "android_device_id",
  "ios_device_id": "ios_device_id",
  "email": "stereophonics0215@gmail.com",
  "roles": ["user"],
  "addresses": [
    {
      "address": "0x0B85edBd6ccA6Fc9689B6a5CF8a668856E77d753",
      "created_at": "2020-10-13T02:26:59.281871Z",
      "updated_at": "2020-10-13T02:26:59.281871Z",
      "network": "ropsten"
    }
  ]
}
```

Error:

```json
{
  "status": "Unprocessable Entity",
  "code": "invalid_request",
  "errors": "address already registered"
}
```

<a id="Login"></a>

# 2. Login

## POST method

```json
{
  "address": "0xCa7A91F3989c8E8CAd46E57ED3eDb3633eD2c31f",
  "signature": "test"
}
```

## Response

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhY2NvdW50X2lkIjoiZWEyOWU4MmItMDgzYi0xMWViLWE3ZGMtMDI0MmFjMTIwMDAzIiwicm9sZXMiOlsidXNlciJdLCJleHAiOjE2MDI1NjMzNjQsImlhdCI6MTYwMjU1NjE2NH0.4bUUwvr5x0G-ngdTyZN640MbzjCw_BUJdwSwHb4NtfE",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhY2NvdW50X2lkIjoiZWEyOWU4MmItMDgzYi0xMWViLWE3ZGMtMDI0MmFjMTIwMDAzIiwidG9rZW4iOiIwN2EzZGE3Zi1kY2YyLTQ5OTItODQ3ZS01N2QxOGVhZTIwZDQiLCJleHAiOjE2MDI1NjMzNjQsImlhdCI6MTYwMjU1NjE2NH0.5AqG4uod0XxQDM4Cz9SHoRDj1W-DYzeacUm5LoZx0Og"
}
```

<a id="OutgoingTransaction"></a>

# 3. OutgoingTransaction

## POST method

```json
{
  "signed_tx": "0xf88b820357851faa3b500083062cc7942b536482a01e620ee111747f8334b395a42a555e80a4a0712d680000000000000000000000000000000000000000000000000de0b6b3a764000029a054661f207be006dea2efb08af66c760ad74bef83ea6d8c93646e96d3c60b09d1a07611a982ab0337491d6dcb5bf22602d7da3fd37652a19cec08e0b463343c1b99"
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
  "status": "Unprocessable Entity",
  "code": "invalid_request",
  "errors": "nonce too low"
}
```

<a id="Balance"></a>

# 4. Balance

## GET method

```json
{
  "address": "0xCa7A91F3989c8E8CAd46E57ED3eDb3633eD2c31f",
  "network": "ropsten",
  "balance": {
    "CDAI": "0",
    "DAI": "0",
    "WEI": "0",
    "PLDAI": "o"
  }
}
```

<a id="TransactionHistory"></a>

# 5. TransactionHistory

## GET method

## Response

```json
[{}, {}, {}]
```

```json
null
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
  "hash": "0x982fba2b0e7559b9db7730d8869c102498d6a9c9d586e12edae9b7f7d98a69cd",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 818,
  "gas_price": 143000000000,
  "gas_limit": 688658,
  "gas_used": 28853,
  "amount": "10000000000000000",
  "time": 1600225514
}
```

[This](https://etherscan.io/tx/0xb0ff4734ed5065b904464449719761779d0bb8ffe23a414de3e32455d723ad4c) is an example of the ETHTransfer tx in the mainnet.

<a id="DAI_transfer"></a>

### DAITransfer

```json
{
  "hash": "0x5051f271809f99f0993479b7c8d6109b34cec965bd1693a83228491fb063f002",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
  "nonce": 826,
  "gas_price": 91000000000,
  "gas_limit": 67009,
  "gas_used": 51830,
  "amount": "0",
  "time": 1600232154,
  "events": [
    {
      "contract_address": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
      "contract_name": "DAI_TOKEN",
      "event_name": "Transfer",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x0C2cfA3C9d3f8248453b0B9D9c8C016F76F5DF5b",
      "token_in": "DAI",
      "amount_in": "10000000000000000000"
    }
  ]
}
```

[This](https://etherscan.io/tx/0x1386a3c354a078dc7d6e4c2c5261cc1f9401435e6589f85b1812f2fa3be972db) is an example of the DAITransfer tx in the mainnet.

<a id="CDAI_transfer"></a>

### CDAITransfer

```json
{
  "hash": "0x5051f271809f99f0993479b7c8d6109b34cec965bd1693a83228491fb063f002",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
  "nonce": 826,
  "gas_price": 91000000000,
  "gas_limit": 67009,
  "gas_used": 51830,
  "amount": "0",
  "time": 1600232154,
  "events": [
    {
      "contract_address": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
      "contract_name": "CDAI_TOKEN",
      "event_name": "Transfer",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x0C2cfA3C9d3f8248453b0B9D9c8C016F76F5DF5b",
      "token_in": "CDAI",
      "amount_in": "10000000000000000000"
    }
  ]
}
```

[This](https://etherscan.io/tx/0x2998bbbd74ce820e0ebb362653170a6ddf93327e0f35cc6e36d81ac913d38c7c) is an example of the CDAITransfer tx in the mainnet.

<a id="PLDAI_transfer"></a>

### PLDAITransfer

```json
{
  "hash": "0x5051f271809f99f0993479b7c8d6109b34cec965bd1693a83228491fb063f002",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
  "nonce": 826,
  "gas_price": 91000000000,
  "gas_limit": 67009,
  "gas_used": 51830,
  "amount": "0",
  "time": 1600232154,
  "events": [
    {
      "contract_address": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
      "contract_name": "PLDAI_TOKEN",
      "event_name": "Transfer",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x0C2cfA3C9d3f8248453b0B9D9c8C016F76F5DF5b",
      "token_in": "PLDAI",
      "amount_in": "10000000000000000000"
    }
  ]
}
```

[This](https://etherscan.io/tx/0x2a927f78f85cbdb55e287c314edd6f64ce64a9c2f294342729cdd375160ccac0) is an example of the PLDAITransfer tx in the mainnet.

<a id="compound_DAI"></a>

## CompoundDAI

<a id="approve"></a>

### Approve

```json
{
  "hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "nonce": 5,
  "gas_price": 102000000000,
  "gas_limit": 743061,
  "gas_used": 615586,
  "time": 1596433159,
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
  "hash": "0x97ba24901265144f7759b4c8242c90630a3c2b557e250483e668e3eef7799e23",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "nonce": 829,
  "gas_price": 103000000000,
  "gas_limit": 404679,
  "gas_used": 137650,
  "amount": "0",
  "time": 1600234813,
  "events": [
    {
      "contract_address": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "contract_name": "CDAI",
      "event_name": "Mint",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "token_in": "DAI",
      "amount_in": "10000000000000000000",
      "token_out": "CDAI",
      "amount_out": "31793626728"
    }
  ]
}
```

```json
{
  "hash": "0x5051f271809f99f0993479b7c8d6109b34cec965bd1693a83228491fb063f002",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
  "nonce": 826,
  "gas_price": 91000000000,
  "gas_limit": 67009,
  "gas_used": 51830,
  "amount": "0",
  "time": 1600232154,
  "events": [
    {
      "contract_address": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
      "contract_name": "COMP_TOKEN",
      "event_name": "Transfer",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x0C2cfA3C9d3f8248453b0B9D9c8C016F76F5DF5b",
      "token_in": "COMP",
      "amount_in": "10000000000000000000"
    }
  ]
}
```

[This](https://etherscan.io/tx/0xe262822ffe5cc23adecf32fe2499e8546afb5f82291a7a867ed8646fc3746bea) is an example of the Deposit tx in the mainnet.

<a id="withdraw"></a>

### Withdraw

```json
{
  "hash": "0x6b511183563ae3c75293600014dec3d5a9c37da4f06327633ecfe3f83f96c68d",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x2B536482a01E620eE111747F8334B395a42A555E",
  "nonce": 831,
  "gas_price": 115000000000,
  "gas_limit": 727455,
  "gas_used": 115792,
  "amount": "0",
  "time": 1600235936,
  "events": [
    {
      "contract_address": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "contract_name": "CDAI",
      "event_name": "Redeem",
      "from": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "to": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "token_in": "CDAI",
      "amount_in": "31793626341",
      "token_out": "DAI",
      "amount_out": "10000000000000000000"
    }
  ]
}
```

```json
{
  "hash": "0x5051f271809f99f0993479b7c8d6109b34cec965bd1693a83228491fb063f002",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
  "nonce": 826,
  "gas_price": 91000000000,
  "gas_limit": 67009,
  "gas_used": 51830,
  "amount": "0",
  "time": 1600232154,
  "events": [
    {
      "contract_address": "0xB5E5D0F8C0cbA267CD3D7035d6AdC8eBA7Df7Cdd",
      "contract_name": "COMP_TOKEN",
      "event_name": "Transfer",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x0C2cfA3C9d3f8248453b0B9D9c8C016F76F5DF5b",
      "token_in": "COMP",
      "amount_in": "10000000000000000000"
    }
  ]
}
```

[This](https://etherscan.io/tx/0xf4fc657497d5ede050562cb030ebfeca701533de8604b150d96cf7b27c394e43) is an example of the Withdraw tx in the mainnet.

<a id="pool_together_v2_weekly_DAI"></a>

## PoolTogetherV2WeeklyDAI

<a id="approve"></a>

### Approve

```json
{
  "hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "nonce": 5,
  "gas_price": 102000000000,
  "gas_limit": 743061,
  "gas_used": 615586,
  "time": 1596433159,
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
  "hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "nonce": 5,
  "gas_price": 102000000000,
  "gas_limit": 743061,
  "gas_used": 615586,
  "time": 1596433159,
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
  "hash": "0x9443d4fed1a3cd67985129d9bfb88af2b8d8b31e708947d0e844b705dcf52e5b",
  "nonce": 5,
  "gas_price": 102000000000,
  "gas_limit": 743061,
  "gas_used": 615586,
  "time": 1596433159,
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
    {
      "contract_address": "0x46C361C9191A2F7cA632e7A0B208702010d4a5Af",
      "contract_name": "UNISWAPV2WETHDAI",
      "event_name": "Swap",
      "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
      "token_in": "WETH",
      "amount_in": "1000000000000000",
      "token_out": "DAI",
      "amount_out": "80183074530213584"
    }
  ]
}
```

[This](https://etherscan.io/tx/0xb3a5c1bb73d52679c7cdeb682e27922fbff2885ead4992cd9d1dfc8636ab9626) is an example of the SwapExactETHForTokens tx in the mainnet.

<a id="aave"></a>

## Aave

<a id="approve"></a>

### Approve

```json
{
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "Aave",
      "Eevnt": "Deposit",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "ADAI",
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
  "hash": "0x28868ce95132ba55d6abc398a1a42ae5b55cbfc7391ca4fb0d4af2124ffd6cff",
  "from": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
  "to": "0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D",
  "nonce": 828,
  "gas_price": 91000000000,
  "gas_limit": 688658,
  "gas_used": 109963,
  "amount": "1000000000000000",
  "time": 1600234042,
  "events": [
    {
      "ContractAddress": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "ContractName": "PoolTogetherV3WeeklyDAI",
      "Eevnt": "RedeemUnderlying",
      "From": "0xa7D41F49dAdCA972958487391d4461a5d0E1c3e9",
      "To": "0x2B536482a01E620eE111747F8334B395a42A555E",
      "TokenIn": "DAI",
      "AmountIn": "100000000000000000000",
      "TokenOut": "ADAI",
      "AmountOut": "100000000000000000000"
    }
  ]
}
```

<a id="ProtocolStats"></a>

# 6. ProtocolStats

## GET method

```json
{
  "uniswap_v2_reserve": {
    "WETH_reserve": "1620681133713400414",
    "DAI_reserve": "131785857651475972534"
  },
  "PoolTogetherV2DAIWeekly": {
    "TotalBalance": "aaa588dc84c87367b6a3",
    "EstimatedAwardAmount": "025a9386c7a226",
    "CurrentDrawId": "24",
    "LastWinner": "0x0fda4ac09a12c10fae30e429f4d6b47c9a83c87e",
    "LastAwardAmount": "100000000000000000000"
  },
  "PoolTogetherV3DAIWeekly": {
    "TotalBalance": "aaa588dc84c87367b6a3", // we can get this with the _tokenTotalSupply?
    "EstimatedAwardAmount": "025a9386c7a226", // we can get this with the awardBalance function?
    "CurrentDrawId": "24", // they don't have a unique id for each round, but we can use the starting time.
    "LastWinner": "0x0fda4ac09a12c10fae30e429f4d6b47c9a83c87e", // can take this from Awarded event but what if a user doesn't win? we don't index it.
    "LastAwardAmount": "100000000000000000000" // can take this from Awarded event but what if a user doesn't win? we don't index it.
    // I might want to add some other key-value to calculate the exit fee
  }
}
```

_\*Some information here might be able to get from their API. I will look into it._
