## cluster component statuses

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

```
kubectl run --generator=run-pod/v1 --image=nginx nginx
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
