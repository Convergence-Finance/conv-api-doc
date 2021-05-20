# Conv Subgraph Endpoint

https://thegraph.com/explorer/subgraph/convergence-tech/convergence-x-mainnet

All pairs consist of two different tokens. As ETH is not a native currency, it is represented only by WETH in ConvergenceX.

The WETH address used in ConvergenceX is ``

## Exchange Data

### Pair and Tickers

Return 24-hour pricing and volume information on each market pair available on ConvergenceX

#### Request

```
{
  pairs {
    id
    token0 {
      symbol
    }
    token1 {
      symbol
    }
    pairPricesLasts(first:1, orderDirection:desc){
      token0Price
      token1Price
    }
    pairVolumeDays(first:1, orderDirection:desc){
      token0Volume
      token1Volume
    }
    pairPricesDays(first:1, orderDirection:desc){
      token0high
      token0low
      token1high
      token1low
    }
  }
}
```

#### Response

```
{
  "data": {
    "pairs": [
      {
        "id": "0x3af7a58d54cf014675af2b7ebc222c3166bf5692", // Pair address
        "pairPricesDays": [
          {
            "token0high": "0.0003059731752703139252688786987264262",
            "token0low": "0.000285442764917948182145634516661596",
            "token1high": "3503.329293658763910471340137482756",
            "token1low": "3268.260360133020527867399180581317"
          }
        ],
        "pairPricesLasts": [
          {
            "token0Price": "0.0003756782427262852139039457705014713",
            "token1Price": "2661.852314744211410053625713888405"
          }
        ],
        "pairVolumeDays": [
          {
            "token0Volume": "8.208415573862712142865081019659862",
            "token1Volume": "27780.65205112829878604513610685171"
          }
        ],
        ...
      }
    ]
  }
}
```

### Swap History

Return historical completed trades for a given market pair

#### Request

```
{
  swaps{
    pair{
        id
        token0 {
            symbol
        }
        token1 {
            symbol
        }
    }
    amount0In
    amount0Out
    amount1In
    amount1Out
  }
}
```

#### Response

```
{
  "data": {
    "swaps": [
      {
        "amount0In": "0",
        "amount0Out": "173064.362067374711025959",
        "amount1In": "10456.857863",
        "amount1Out": "0",
        "pair": {
          "id": "0xd5a547f21c2d76667c239e14f1fe65a5d9fd5d50",
          "token0": {
            "symbol": "CONV"
          },
          "token1": {
            "symbol": "USDT"
          }
        }
      },
      ...
    ]
  }
}
```

### Pools

Return data of staking pool on Convergence

#### Request

```
{
  pools{
    token
    stakingPair{
      token0Symbol
      token1Symbol
    }
    totalStakeAmount
    rewardPerBlock
  }
}
```

#### Response

```
{
  "data": {
    "pools": [
      {
        "rewardPerBlock": "56000000000000000000",
        "stakingPair": { // Available if it's a LP token
          "token0Symbol": "CONV",
          "token1Symbol": "WETH"
        },
        "token": "0x4a2b4f76ab77c7ee3820f16967741209d0a8779e", // Address of the token staked in the pool
        "totalStakeAmount": "255859603485716809595868"
      },
      ...
    ]
  }
}
```
