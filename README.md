
# Artillery POC

Proof of concept for Artillery.

Artillery is a platform for production-grade load testing.

https://www.artillery.io/


## Installation

Pre-requisites: [NodeJs](https://nodejs.org/en) and [NPM](https://www.npmjs.com) installed.

Install:
- npm install -g artillery@latest
## Example

Create a YML file with next content:
````
config:
  target: http://asciiart.artillery.io:8080
  phases:
    - duration: 60
      arrivalRate: 1
    - duration: 300
      arrivalRate: 10
scenarios:
  - flow:
    - get:
        url: '/dino'
    - get:
        url: '/armadillo'
````
Save as test-script.yml
## Execution
Run a console and type:
```
artillery run test-script.yml
```
Or, if you want to save results:
```
artillery run test-script.yml --output report.json
```
## Results
Analize output (report.json, in this case):

Fragment
```
{
  "aggregate": {
    "counters": {
      "vusers.created_by_name.0": 3060,
      "vusers.created": 3060,
      "http.requests": 4323,
      "http.codes.200": 2526,
      "http.responses": 2526,
      "http.downloaded_bytes": 1221321,
      "plugins.metrics-by-endpoint./dino.codes.200": 1263,
      "plugins.metrics-by-endpoint./armadillo.codes.200": 1263,
      "vusers.failed": 1797,
      "vusers.completed": 1263,
      "plugins.metrics-by-endpoint./dino.errors.ETIMEDOUT": 1797,
      "errors.ETIMEDOUT": 1797
    },
    "rates": {
      "http.request_rate": 13
    },
    "firstCounterAt": 1737045325030,
    "firstHistogramAt": 1737045326009,
    "lastCounterAt": 1737045694150,
    "lastHistogramAt": 1737045516782,
    "firstMetricAt": 1737045325030,
    "lastMetricAt": 1737045694150,
    "period": 1737045690000,
    "summaries": {
      "http.response_time": {
        "min": 220,
        "max": 1120,
        "count": 2526,
        "mean": 242.2,
        "p50": 232.8,
        "median": 232.8,
        "p75": 247.2,
        "p90": 252.2,
        "p95": 257.3,
        "p99": 415.8,
        "p999": 620.3
      },
      "http.response_time.2xx": {
        "min": 220,
        "max": 1120,
        "count": 2526,
        "mean": 242.2,
        "p50": 232.8,
        "median": 232.8,
        "p75": 247.2,
        "p90": 252.2,
        "p95": 257.3,
        "p99": 415.8,
        "p999": 620.3
      },
      "plugins.metrics-by-endpoint.response_time./dino": {
        "min": 220,
        "max": 618,
        "count": 1263,
        "mean": 242.2,
        "p50": 232.8,
        "median": 232.8,
        "p75": 247.2,
        "p90": 252.2,
        "p95": 257.3,
        "p99": 415.8,
        "p999": 620.3
      },
      "plugins.metrics-by-endpoint.response_time./armadillo": {
        "min": 220,
        "max": 1120,
        "count": 1263,
        "mean": 242.3,
        "p50": 232.8,
        "median": 232.8,
        "p75": 247.2,
        "p90": 252.2,
        "p95": 257.3,
        "p99": 407.5,
        "p999": 1022.7
      },
...
}
```
## Author

- Versión 0.0.1 - Hernán Funes (hfunesdev at gmail) - [@hfunescom](https://hfunes.com)