# Global Metrics 

Returns the latest global cryptocurrency market metrics. Use the "convert" option to return market values in multiple fiat and cryptocurrency conversions in the same call.

#### import required libraries


```python
from requests import Request, Session
from requests.exceptions import ConnectionError, Timeout, TooManyRedirects
import json
```

#### setup the url, headers and parameters


```python
url = 'https://sandbox-api.coinmarketcap.com/v1/global-metrics/quotes/latest'

parameters = {
  'convert':'USD'
}

headers = {
  'Accepts': 'application/json',
  'X-CMC_PRO_API_KEY': '<<< YOUR API KEY >>>',
}

session = Session()
session.headers.update(headers)
```

#### get the response json


```python
try:
  response = session.get(url, params=parameters)
  res = response.json()
  data = json.dumps(res, sort_keys = True, indent = 4)
  print(data)
except (ConnectionError, Timeout, TooManyRedirects) as e:
  print(e)
```

    {
        "data": {
            "active_cryptocurrencies": 2475,
            "active_exchanges": 351,
            "active_market_pairs": 20236,
            "btc_dominance": 69.44,
            "eth_dominance": 7.3584,
            "last_updated": "2019-08-30T18:50:00.000Z",
            "quote": {
                "USD": {
                    "altcoin_market_cap": 75353479269.7539,
                    "altcoin_volume_24h": 33534327995.5604,
                    "altcoin_volume_24h_reported": 59696268416.2682,
                    "last_updated": "2019-08-30T18:50:00.000Z",
                    "total_market_cap": 246575218535.053,
                    "total_volume_24h": 47263740384.9739,
                    "total_volume_24h_reported": 76915954559.0052
                }
            }
        },
        "status": {
            "credit_count": 1,
            "elapsed": 6,
            "error_code": 0,
            "error_message": null,
            "timestamp": "2019-12-12T16:17:41.977Z"
        }
    }


#### print required data in friendly format


```python
active_crypto = res['data']['active_cryptocurrencies']
print('active_cryptocurrencies:', active_crypto)
```

    active_cryptocurrencies: 2475



```python
active_exchgs = res['data']['active_exchanges']
print('active_exchanges:', active_exchgs)
```

    active_exchanges: 351



```python
last_updated = res['status']['timestamp']
print('last_updated', last_updated)
```

    last_updated 2019-12-12T16:17:41.977Z


#### Thanks!
