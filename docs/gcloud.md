## Delete an image from Container Registry

The image revision must have all tags removed before it can be deleted.

```
$> gcloud container images list-tags gcr.io/<project-name>/<image-name> --format 'value("digest")' | sed -e 's/^/gcr.io\/<project-name>\/<image-name>@sha256:/' | xargs -P 4 -n 25 gcloud container images delete --force-delete-tags --quiet
```

`xargs` options:

* `-n 25` delete images in batches of 25
* `-P 4` run 4 parallel processes
