## HTTP request to a service or pod

### Service

```bash
kubectl get --raw "/api/v1/namespaces/<namespaceName>/services/<serviceName>:<port>/proxy/<path>"
```

Example of an a request to the Prometheus metrics endpoint VTGate:

```bash
 kubectl get --raw "/api/v1/namespaces/default/services/mydb-primary-vtgate-0867c40b:15000/proxy/metrics"
```

### Pod

```bash
kubectl get --raw "/api/v1/namespaces/<namespaceName>/pod/<podName>:<port>/proxy/<path>"
```

Example of an HTTP request directly to one of the VTGate pods:

```bash
kubectl get --raw "/api/v1/namespaces/default/pods/mydb-primary-vtgate-0867c40b-755585b47b-94ptr:15000/proxy/metrics"
```

## Filter on fields not availble in `--field-selector`

The `--field-selector` option only supports a small number of fields for filtering results and generally doesn't work for CRDs. An alternative is to use the `jsonpath` output option, for example:

```
# List pods whose restartPolicy is not `Always`
kubectl get pods --output=jsonpath='{range .items[?(.spec.restartPolicy!="Always")]}{.metadata.name}{"\n"}{end}'
```

## Get cluster component statuses

```
kubectl get componentstatuses
```

Example:

```
$> kubectl get componentstatuses
NAME                 STATUS    MESSAGE             ERROR
controller-manager   Healthy   ok
scheduler            Healthy   ok
etcd-0               Healthy   {"health":"true"}
etcd-1               Healthy   {"health":"true"}
```

Alternatively, `get cs`.

## Create resources imparatively (e.g. one-off resources)

### Pod

Syntax:

```
kubectl run [name] --image=[name] --command -- [command] [arg1] [arg2]...
```

Example:

```
kubectl run testing --attach --image=alpine --rm --stdin --tty --command -- ash
```

### Deployment

```
kubectl create deployment --image nginx --replicas 3 nginx
```

### Service

```
kubectl expose deployment nginx --port=80 --target-port=8000
```

## List all resources in the cluster

`kubectl get all` only shows specific resources and doesn't show any CRDs. Instead, use this:

```
kubectl api-resources --verbs=list --namespaced -o name  --context [KUBECTL_CONTEXT] \
  | xargs -n 1 kubectl get --show-kind --ignore-not-found --namespace NAMESPACE --context [KUBECTL_CONTEXT]
```

## Selector with multiple values

To match where `app=filebeat` OR `app=logstash`:

```
kubectl get pods --selector 'app in (filebeat,logstash)'
```

## Set the namespace (or other options) for a context

```
kubectl config set-context <NAME_OF_CONTEXT> --namespace <NAME_OF_NAMESPACE>
```

## `kubectl convert`

Convert config files between different API versions.

## `kubectl explain [RESOURCE]`

Documents a resource and it's fields.

## Global Options

`-v=N` - `N` is the log level. 6 and higher will show the API requests that are being made

## Resources

* Jordan Liggitt's [Stupid Kubectl Tricks](https://schd.ws/hosted_files/kccncna17/de/Stupid%20Kubectl%20Tricks.pdf)
* [kubectx](https://github.com/ahmetb/kubectx) - a fast way to switch between clusters and namespaces in kubectl
