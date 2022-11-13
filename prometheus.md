# Prometheus

[Nice article](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/)  
[PromQL Cheat sheet](https://promlabs.com/promql-cheat-sheet/)  
[How does a Prometheus Counter work?](https://www.robustperception.io/how-does-a-prometheus-counter-work)  
[PromQL for humans](https://timber.io/blog/promql-for-humans/)  
[Awesome Prometheus](https://github.com/roaldnefs/awesome-prometheus)  


**Metrics** are kind of tables 
**Metrics** hold **labels** inside like `bicycle_distance_meters_total{brand="monark",gears="7"}`

Negation and regular expressions (in Google’s RE2-format) are supported by replacing = with either 
 `=` Equality  
`!=` Non-equality  
`=~` Regex match  
`!~` Negative regex match  

## Data types

* scalar 
* instant vector
* range vector
The simplest range vector query is an instant vector with a time selector, such as bicycle_distance_meters_total[1h]

## Metric Types

* Counters - can only increase
* Guage - arbitrary change
* Histogram
* Sumary

By convention, counters end with `_total`

To help keep you on the straight and narrow, remember this: 
The only mathematical operations you can safely directly apply to a counter's values are 
**rate, irate, increase, and resets** 
Anything else will cause you problems.

rate(x[35s]) = difference in value over 35 seconds / 35s

`rate(demo_api_request_duration_seconds_count[5m])` Per-second rate of increase, averaged over last 5 minutes


# rate()
```
rate(v range-vector) calculates the per-second average rate of increase of the time series in the range vector. Breaks in monotonicity (such as counter resets due to target restarts) are automatically adjusted for. Also, the calculation extrapolates to the ends of the time range, allowing for missed scrapes or imperfect alignment of scrape cycles with the range's time period.

The following example expression returns the per-second rate of HTTP requests as measured over the last 5 minutes, per time series in the range vector:

rate(http_requests_total{job="api-server"}[5m])
rate should only be used with counters. It is best suited for alerting, and for graphing of slow-moving counters.

Note that when combining rate() with an aggregation operator (e.g. sum()) or a function aggregating over time (any function ending in _over_time), always take a rate() first, then aggregate. Otherwise rate() cannot detect counter resets when your target restarts.
```

## Selecting series
```
Select latest sample for series with a given metric name:
node_cpu_seconds_total

Select 5-minute range of samples for series with a given metric name:
node_cpu_seconds_total[5m]

Only series with given label values:
node_cpu_seconds_total{cpu="0",mode="idle"}

Complex label matchers:
node_cpu_seconds_total{cpu!="0",mode=~"user|system"}
```

## Rates of increase for counters
```
Per-second rate of increase, averaged over last 5 minutes:
rate(demo_api_request_duration_seconds_count[5m])

Per-second rate of increase, calculated over last two samples in a 1-minute time window:
irate(demo_api_request_duration_seconds_count[1m])

Absolute increase over last hour:
increase(demo_api_request_duration_seconds_count[1h]
```

## Aggregating over multiple series
```
Sum over all series:
sum(node_filesystem_size_bytes)

Preserve the instance and job label dimensions:
sum by(job, instance) (node_filesystem_size_bytes)

Aggregate away the instance and job label dimensions:
sum without(instance, job) (node_filesystem_size_bytes)

Available aggregation operators: 
sum(), min(), max(), avg(), stddev(), stdvar(), count(), count_values(), group(), bottomk(), topk(), quantile()
```

## Changes in gauges
```
Per-second derivative using linear regression:
deriv(demo_disk_usage_bytes[1h])

Absolute change in value over last hour:
delta(demo_disk_usage_bytes[1h])

Predict value in 1 hour, based on last 4 hours:
predict_linear(demo_disk_usage_bytes[4h], 3600)
```
