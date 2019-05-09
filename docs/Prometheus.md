## Find the 20 biggest timeseries by metric name and job

```
topk(20, count by (__name__, job)({__name__=~".+"})).
```

-- https://www.robustperception.io/dropping-metrics-at-scrape-time-with-prometheus
