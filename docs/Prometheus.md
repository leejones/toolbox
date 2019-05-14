## Helpful Queries

### 20 biggest time series by metric name and job

```
topk(20, count by (__name__, job)({__name__=~".+"}))
```

-- https://www.robustperception.io/dropping-metrics-at-scrape-time-with-prometheus

### Number of metrics scraped

```
scrape_samples_scraped
```

This metric is a guage.

-- https://www.robustperception.io/using-sample_limit-to-avoid-overload
