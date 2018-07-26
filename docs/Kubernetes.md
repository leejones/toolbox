Tools and Services for Kubernetes. Items are mostly in alphabetical order.

## Case Studies

* The [launch](https://cloudplatform.googleblog.com/2016/09/bringing-Pokemon-GO-to-life-on-Google-Cloud.html) of Pokemon Go to millions of users on GKE.

## Cluster Management

* [Techtonic](https://coreos.com/tectonic/) - automated cluster management with multi-cloud capabilities

## Delivery

Tools/Services that support continuous delivery and continuous deployment.

* [Shopify's kubernetes-deploy](https://github.com/Shopify/kubernetes-deploy) - a tool for managing automated deployments with support templating, encrypted secrets, and feedback when deploys fail ([video demo from Aug 2017 SIG Apps](https://youtu.be/hn23Z-vL_cM?list=PL69nYSiGNLP2LMq7vznITnpd2Fk1YIZF3&t=99))

## Development

* [Draft](https://github.com/Azure/draft) - Draft makes it easy to build applications that run on Kubernetes. Draft targets the "inner loop" of a developer's workflow: as they hack on code, but before code is committed to version control. It’s like heroku buildpacks + helm.
* [Telepresence](https://www.telepresence.io) - Local development experience of services running in Kubernetes - allows you to develop against a bunch of services without having to run them all on your laptop

## Disaster Recovery

* [Heptio Ark](https://github.com/heptio/ark) - tool for cluster disaster recovery

## Miscellaneous

* [Brigade](https://github.com/Azure/brigade) - Build event based workflows that use Kubernetes jobs
* [Kubeapps](https://kubeapps.com) - a tool that installs a helm, kubeless, sealed secrets, and a web UI for managing helm charts and kubeless functions.

## Operators

> An Operator is an application-specific controller that extends the Kubernetes API to create, configure and manage instances of complex stateful applications on behalf of a Kubernetes user... An Operator represents human operational knowledge in software to reliably manage an application.

-- https://coreos.com/operators/

## RBAC

* [audit2rbac](https://github.com/liggitt/audit2rbac) - converts audit logs into RBAC roles

## Secrets

* Bitnami’s [sealed-secrets](https://github.com/bitnami/sealed-secrets) - allow you to keep the encrypted secrets in git, adds a customer controller to the cluster to encrypt/decrypt
* Shopify’s [kubernetes-deploy](https://github.com/Shopify/kubernetes-deploy) uses [EJSON](https://github.com/Shopify/ejson) (encrypted JSON, also made by Shopfiy)

## Talks

* StackPointCloud has a great [YouTube channel](https://www.youtube.com/user/StackPointCloud/videos) with videos from various Kubernetes meetups and events

## Training

* Heptio [offers](https://heptio.com/services/training/) online and on-site training