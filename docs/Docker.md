## CLI command output formatting

Show all fields in JSON format:

```
docker image ls --format "{{json .}}"
```

Show specific fields for each image:

```
$> docker image ls --format "{{.ID}} {{ .Repository }}"
```


## Resources for people getting started

* [Docker Overview](https://docs.docker.com/engine/docker-overview/) - does a nice job of explaining the concepts

## Secrets during builds

* Temporary GitHub access tokens with [Fidelius](https://medium.com/verloop-engineering/fidelius-e4b2d8b6b1df).
