## Find out why there are unassigned shards

List all unassigned shards with a high level reason:

```
curl --silent http://localhost:9200/_cat/shards?h=index,shard,prirep,state,unassigned.reason| grep UNASSIGNED
```

Display explaination for the first unassigned shard the cluster finds:

```
curl http://localhost:9200/_cluster/allocation/explain?pretty
```

Display explaination on a specific unassigned shard:

```
curl --header "Content-type: application/json" --request GET http://localhost:9200/_cluster/allocation/explain?pretty -d '{ "index": "TODO", "shard": 0, "primary": true }'
```

* [cluster allocation explain API docs](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-allocation-explain.html) from Elastic
* [debugging tips and solutions](https://www.datadoghq.com/blog/elasticsearch-unassigned-shards/) from Datadog

## Disable read-only on all indices

```
curl --request PUT --header 'Content-type: application/json' http://localhost:9200/_all/_settings -d '{ "index": { "blocks":
{ "read_only_allow_delete": false } } }'
```

For a single index, replace `_all` with the index name.
