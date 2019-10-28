## Disable read-only on all indices

```
curl --request PUT --header 'Content-type: application/json' http://localhost:9200/_all/_settings -d '{ "index": { "blocks":
{ "read_only_allow_delete": false } } }'
```

For a single index, replace `_all` with the index name.
