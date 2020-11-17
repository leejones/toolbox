## Resources

* [Avoid time-of-measuerment bias with Prometheus](https://blog.lawrencejones.dev/incremental-measurement/) - shows how to get more helpful job duration measurements from long-running processes (e.g. background workers).
* [Phippy and Zee Go to the Mountains](https://phippygoestothemountains.github.io) - an illustrated explanation of Prometheus

## Concepts

* **sample** - a numerical measurement at a specific point in time
* **labels** - metadata about a sample
* **time series** - a collection of samples, can be displayed on a graph
* **(instant) vector** - a measurement at a specific time (usually now)
* **range vector** - all samples during a window of time
* **functions** - a way of combining time series, often used with range vectors

## Tooling

### Alertmanager

* Preview Slack alert notification changes: https://juliusv.com/promslack/

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
