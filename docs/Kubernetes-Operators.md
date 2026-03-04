## Overview

Operators extend Kubernetes with custom controllers that manage application-specific resources via reconciliation loops.

Key libraries:

- [`sigs.k8s.io/controller-runtime`](https://pkg.go.dev/sigs.k8s.io/controller-runtime) — libraries for building controllers; used by Kubebuilder and Operator SDK
- [Kubebuilder book](https://book.kubebuilder.io/) — the canonical guide for building operators with Kubebuilder ([architecture overview](https://book.kubebuilder.io/architecture))

## Groups, Versions, and Kinds

-- https://book.kubebuilder.io/cronjob-tutorial/gvks

- **Group** — a collection of related Kinds
- **Version** — allows Kinds to evolve over time
- **Kind** — analogous to a type
- **Resource** — an instantiation of a Kind
- **GroupVersionKind (GVK)** — the full description of a Kind
- **Scheme** — maps Go types to GroupVersionKinds

## Reconciliation

-- https://book.kubebuilder.io/getting-started#reconciliation-process

The reconciliation process "functions as a loop, continuously checking conditions and performing necessary actions until the desired state is achieved. This process will keep running until all conditions in the system align with the desired state defined in our implementation."

Key rules from the [`controller-runtime` FAQ](https://github.com/kubernetes-sigs/controller-runtime/blob/main/FAQ.md):

- Each controller should only reconcile **one object type**.
- The `Reconcile` function should **not** branch on event type (create, update, delete, etc.). It should query the current state of resources and respond accordingly. This simplifies behavior and correctly handles skipped or coalesced events.

## Watching Resources to Trigger Reconciliation

The `Manager` sets up a `Cache` backed by `client-go` informers. The cache maintains a long-lived watch connection to the API server and keeps an in-memory index of objects. Controllers read from this cache rather than hitting the API server directly, which reduces load. When a watched resource changes, event handlers map the change to reconcile requests on the work queue.

There are three builder methods in `SetupWithManager` for wiring up watches:

- `For(&MyResource{})` — the primary resource this controller reconciles
- `Owns(&corev1.Pod{})` — child resources with an `ownerRef` pointing back to the primary resource; changes enqueue the owner for reconciliation
- `Watches(...)` — arbitrary resources with a custom event handler

`Watches` is used when your CR references a resource it doesn't own (no `ownerRef`). You provide a `MapFunc` that takes the event and returns the reconcile request(s) for the CR(s) that reference it.

For example, if your CR references a user-supplied `Secret`, you can use `Watches` to trigger a reconcile on the CR whenever that `Secret` changes. The `MapFunc` looks up which CR(s) reference the changed `Secret` and enqueues them.

**Predicates** can be attached to any watch to filter events and avoid unnecessary reconciliations — e.g. only trigger when the spec changes, not on every status update.

## Watching Child Resources

In `SetupWithManager`, configure the manager to watch child resources created by the operator (e.g. a `Deployment` created from a `Memcached` resource). If the child is accidentally deleted, this triggers a reconcile to re-create it. The manager only watches children owned by the parent resource.

The `ownerRef` attribute serves two purposes:

1. Tells the manager which child resources to watch.
2. Enables cascading deletes — deleting the owner resource also deletes all its children.

-- https://book.kubebuilder.io/getting-started
