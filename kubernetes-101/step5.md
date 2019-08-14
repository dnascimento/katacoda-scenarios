## Services

- A *service* is a stable endpoint to connect to "something"


- `kubectl get services`{{execute}}
- `kubectl get svc`{{execute}}


There is already at least one service on our cluster: the Kubernetes API itself.

---

## ClusterIP services

- A `ClusterIP` service is internal, available from the cluster only

- This is useful for introspection from within containers

## Listing running containers

- Containers are manipulated through *pods*
- A pod is a group of containers:
 - running together (on the same node)
 - sharing resources (RAM, CPU; but also network, volumes)

```
kubectl get pods
```

*Where are the pods that we saw just a moment earlier?!?*

---

## Namespaces

- Namespaces allow us to segregate resources

`kubectl get namespaces`{{execute}}
`kubectl get namespace`{{execute}}
`kubectl get ns`{{execute}}

--

*You know what ... This `kube-system` thing looks suspicious.*

*In fact, I'm pretty sure it showed up earlier, when we did:*

`kubectl describe node node01`{{execute}}

---

## Accessing namespaces

- By default, `kubectl` uses the `default` namespace
- We can see resources in all namespaces with `--all-namespaces`

- List the pods in all namespaces:

`kubectl get pods --all-namespaces`{{execute}}

*Here are our system pods!*

---

## What are all these control plane pods?

- `etcd` is our etcd server

- `kube-apiserver` is the API server

- `kube-controller-manager` and `kube-scheduler` are other control plane components

- `coredns` provides DNS-based service discovery

- `kube-proxy` is the (per-node) component managing port mappings and such

- the `READY` column indicates the number of containers in each pod

---

## Namespaces and other `kubectl` commands

- We can use `-n`/`--namespace` with almost every `kubectl` command

- Example:

  - `kubectl create --namespace=X` to create something in namespace X

- We can use `-A`/`--all-namespaces` with most commands that manipulate multiple objects

- Examples:

  - `kubectl delete` can delete resources across multiple namespaces

  - `kubectl label` can add/remove/update labels across multiple namespaces

## Scoping another namespace

- We can also look at a different namespace (other than `default`)

- List only the pods in the `kube-system` namespace:
-
`kubectl get pods --namespace=kube-system`{{execute}}
`kubectl get pods -n kube-system`{{execute}}
