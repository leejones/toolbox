## Overview

Crossplane provides a control plane for the cloud — a reconciliation loop with an API, built on top of the Kubernetes control plane.

Since everything is a Kubernetes manifest, it integrates naturally with ArgoCD and other Kubernetes workflows.

## Terminology

- **Provider** - A collection of CRDs for managing cloud resources (e.g. GCP, AWS).
- **Managed Resource** - A CRD that maps 1:1 with a cloud resource (e.g. `StorageBucket`, `RDSInstance`).
- **Composite Resource / Composition** - A collection of Managed Resources.
- **Composite Resource Definition (XRD)** - A template that exposes settings for users to customize Composite Resources.
- **Functions** - Define how to converge resources. Can be written in Go, Python, or KCL.
- **Upjet** - A tool that generates Crossplane providers from Terraform providers.
- **UXP (Upbound Universal Crossplane)** - An enterprise-grade, drop-in replacement for Crossplane. Adds security hardening, a modern UI, and GitOps functionality. Free and open source with optional paid features. A distribution of Crossplane (as opposed to Upbound Spaces, which is a hosted platform).

## Resource Scoping

Resources with `.m` in the name are namespace-scoped; without `.m` they are cluster-scoped.

## Crossplane V2 Changes

- Introduced namespaced resources. Previously all resources were cluster-scoped, which made RBAC and isolation difficult.
- "Claims" were the prior workaround for namespaced resources — helpful but not fully namespace-isolated.
- Compositions can now include non-Crossplane resources directly (e.g. an `ExternalSecret`). Previously these had to be wrapped in a Crossplane `Object`.
