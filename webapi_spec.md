# type

- [register_address](#register_address)
- [balance](#balance)
- [outgoing_tx](#outgoing_tx)
- [transaction_error](#transaction_error)
- [txstate](#txstate)
- [txhistory](#txhistory)
- [protocol_stats](#protocol_stats)

<a id="register_address"></a>

# register_address

## method

POST

## format

```json
{
  "id": "1898272544408",
    "type": "register_address",
    "deviceTokenId": deviceTokenId,
    "timestamp": timestamp,
    "address": checksumAddress
};
```

<a id="balance"></a>

# balance

## method

GET

## format

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

<a id="outgoing_tx"></a>

# outgoing_tx

## method

POST

## format

```json
{
  "type": "outgoing_tx",
  "signed_tx": "0xf8890485147d35700083062cc7945d3a536e4d6dbd6114cc1ead35777bab948e364380a4a0712d6800000000000000000000000000000000000000000000002bdd586116b52b000026a01c125c2cb31d38ae8300d3d3434c7a2ef842a172fa6b3cce0e4f2b9e20dfa261a00e9dc555d73d9c308891806cfa428e4694a7a3fa138845284437275dc94ad53c",
  "nonce": "4"
}
```

<a id="transaction_error"></a>

# transaction_error

## method

GET

## format

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

<a id="txstate"></a>

# txstate

## method

GET

## format

```json
{
  "id": "1598271744680",
  "type": "txstate",
  "tx": {
    "d76f64ed3d4a4c9790da678b6255d8d6819e7f73e51fc797915a22ba3f2090b1": [
      // tx hash
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69", // from address
      "5d3a536e4d6dbd6114cc1ead35777bab948e3643", // to address
      "051f6b", // gas limit or gas used in hex
      "147d357000", // gas price in hex wei
      "00", // value in hex wei
      4, // nonce
      "1598271743", // timestamp
      2, // state. 2 is included. 3 is confirmed.
      {
        "compound_dai": {
          // contract name
          "mint": [
            // event name
            [
              "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
              "2bdd586116b52b0000",
              "039235b6b0cd"
            ]
          ]
        }
      },
      1
    ]
  }
}
```

## a list of a contract name and event name

### dai

- approve
- transfer

### cdai

- approve
- transfer

### pldai

- approve
- transfer

### compound_dai

- mint

### pooltogether_v3_weekly_dai

### uniswap_v2

- swap

<a id="txhistory"></a>

# txhistory

## method

GET

## format

```json
{
  "id": "4598272544408",
  "type": "txhistory",
  "txes": {
    "11a6a52a3eef386105a9445987c06c0654b0ce12b033a745401abbedc94575b7": [
      "9c19b0497997fe9e75862688a295168070456951",
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "5208",
      "10e74c1600",
      "011c37937e080000",
      "61955",
      1596355220,
      3,
      {},
      1
    ],
    "98558a490cead5385cd773b2ac2dc8a96eea05f904cee05a084d1aee69930ed5": [
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "6b175474e89094c44da98b954eedeac495271d0f",
      "ad46",
      "0f9982de00",
      "00",
      "1",
      1596356920,
      3,
      {
        "dai": {
          "appr": [
            [
              "5d3a536e4d6dbd6114cc1ead35777bab948e3643",
              "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
              "ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff"
            ]
          ]
        }
      },
      1
    ],
    "9c99489a88d1d95d2b707fb5e3d6b136859ad49689fab4603b8ee66121f3c8b8": [
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "7a250d5630b4cf539739df2c5dacb4c659f2488d",
      "01e972",
      "0f9982de00",
      "02d07041ffe42800",
      "0",
      1596356832,
      3,
      {
        "uniswap2ethdai": {
          "U2swap": [
            [
              "7a250d5630b4cf539739df2c5dacb4c659f2488d",
              "00",
              "02d07041ffe42800",
              "041ef64b939afcbb76",
              "00",
              "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69"
            ]
          ]
        }
      },
      1
    ],
    "a0ccafd057346a4d20eef3944eae950c09726cd8c367d133e4172f2b045ef619": [
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "5d3a536e4d6dbd6114cc1ead35777bab948e3643",
      "05059f",
      "0f9982de00",
      "00",
      "2",
      1596356920,
      3,
      {
        "cdai": {
          "mint": [
            [
              "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
              "041ef6303d47a50000",
              "56174a5176"
            ]
          ]
        }
      },
      1
    ],
    "bdacafd91630bb2d3abad806523d9ed1054fe48e161266f34e940c0e4d408476": [
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "7a250d5630b4cf539739df2c5dacb4c659f2488d",
      "01aeda",
      "0861c46800",
      "1dcd1ffc1cbd9200",
      "3",
      1596433699,
      3,
      {
        "uniswap2ethdai": {
          "U2swap": [
            [
              "7a250d5630b4cf539739df2c5dacb4c659f2488d",
              "00",
              "1dcd1ffc1cbd9200",
              "2bdd5849feec3ed2b7",
              "00",
              "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69"
            ]
          ]
        }
      },
      1
    ],
    "efdb6e7e6252347457611ee29e6a9b791bf841952298e3c72801727624974f6b": [
      "e89943ec20d856f064a87349a00ef6ab00aed042",
      "e9cd8cf5011f57a88e31cbaa7d2d1f3578958e69",
      "5208",
      "10ff239a00",
      "1dc984ded468dc00",
      "190593",
      1596433159,
      3,
      {},
      1
    ],
    "contracts": [
      // a list of contracts an address is associated with
      "7a250d5630b4cf539739df2c5dacb4c659f2488d",
      "5d3a536e4d6dbd6114cc1ead35777bab948e3643"
    ]
  }
}
```

<a id="protocol_stats"></a>

# protocol_stats

## method

GET

## format

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
