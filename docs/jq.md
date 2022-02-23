# jq

## Transform nested fields in a flattened format (dot notation)

Transform the following:

```json
{
  "a": {
    "b": {
      "c": 1
    }
  }
}
```

To:

```json
{
  "a.b.c": 1
}
```

```
jq '. | [leaf_paths as $path | {"key": $path | join("."), "value": getpath($path)}] | from_entries'
```

source: https://stackoverflow.com/a/37555908
