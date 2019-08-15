# Declarative vs imperative

- Our container orchestrator puts a very strong emphasis on being *declarative*

- Declarative:

  *I would like a cup of tea.*

- Imperative:

  *Boil some water. Pour it in a teapot. Add tea leaves. Steep for a while. Serve in a cup.*

- Declarative seems simpler at first ...
- ... As long as you know how to brew tea

---

Imperative systems:

  - simpler
  - if a task is interrupted, we have to restart from scratch

Declarative systems:

  - if a task is interrupted (or if we show up to the party half-way through),
    we can figure out what's missing and do only what's necessary

  - we need to be able to *observe* the system

  - ... and compute a "diff" between *what we have* and *what we want*



## Declarative vs imperative in Kubernetes

- With Kubernetes, we cannot say: "run this container"

- All we can do is write a *spec* and push it to the API server

  (by creating a resource like e.g. a Pod or a Deployment)

- The API server will validate that spec (and reject it if it's invalid)

- Then it will store it in etcd

- A *controller* will "notice" that spec and act upon it

---

## Reconciling state

- Watch for the `spec` fields in the YAML files later!

- The *spec* describes *how we want the thing to be*

- Kubernetes will *reconcile* the current state with the spec
  <br/>(technically, this is done by a number of *controllers*)

- When we want to change some resource, we update the *spec*

- Kubernetes will then *converge* that resource
