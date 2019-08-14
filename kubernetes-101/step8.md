# Running our first containers on Kubernetes

- First things first: we cannot run a container
- We are going to run a pod, and in that pod there will be a single container

- In that container in the pod, we are going to run a simple command

- Then we are going to start additional copies of the pod

## Create a deployment
One of the most common Kubernetes object is the deployment object. The deployment object defines the container spec required, along with the name and labels used by other parts of Kubernetes to discover and connect to the application.

### Task
Copy the following definition to the editor. The definition defines how to launch an application called webapp1 using the Docker Image katacoda/docker-http-server that runs on Port 80.

```
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: webapp1
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: webapp1
    spec:
      containers:
      - name: webapp1
        image: katacoda/docker-http-server:latest
        ports:
        - containerPort: 80
```

This is deployed to the cluster with the command
`kubectl apply -f deployment.yaml`

As it's a Deployment object, a list of all the deployed objects can be obtained via
`kubectl get deployment`

Details of individual deployments can be outputted with
`kubectl describe deployment webapp1`


## What are these different things?

- A *deployment* is a high-level construct

  - allows scaling, rolling updates, rollbacks

  - multiple deployments can be used together to implement a
    [canary deployment](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/#canary-deployments)

  - delegates pods management to *replica sets*

- A *replica set* is a low-level construct

  - makes sure that a given number of identical pods are running

  - allows scaling

  - rarely used directly

- A *replication controller* is the (deprecated) predecessor of a replica set

---

## Our `webapp1` deployment

- `kubectl apply` created a *deployment*, `deployment.apps/webapp1`

`kubectl get deployments`

```
NAME                       DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp1   1         1         1            1           10m
```

`kubectl get replicaset`
That deployment created a *replica set*, `replicaset.apps/webapp1-xxxxxxxxxx`
```
NAME                                  DESIRED   CURRENT   READY     AGE
replicaset.apps/webapp1-7c8bbcd9bc   1         1         1         10m
```

`kubectl get pods`
That replica set created a *pod*, `pod/webapp1-xxxxxxxxxx-yyyyy`

```
NAME                            READY     STATUS    RESTARTS   AGE
pod/webapp1-7c8bbcd9bc-6c9qz   1/1       Running   0          10m
```

We'll see later how these folks play together for scaling, high availability, rolling updates.

---

## Viewing container output

Let's use the `kubectl logs` command

- We will pass either a *pod name*, or a *type/name*

  (E.g. if we specify a deployment or replica set, it will get the first pod in it)

`kubectl logs deploy/webapp1`

#### Streaming logs in real time.

Just like `docker logs`, `kubectl logs` supports convenient options:

- `-f`/`--follow` to stream logs in real time (à la `tail -f`)
- `--tail` to indicate how many lines you want to see (from the end)
- `--since` to get logs only after a given timestamp

`kubectl logs deploy/webapp1 --tail 1 --follow`

---

## Scaling our application

- We can create additional copies of our container (I mean, our pod) with `kubectl scale`

Scale our `webapp1` deployment:

```bash
kubectl scale deployment webapp1 --replicas 3
```

## Resilience

- The *deployment* `webapp1` watches its *replica set*
- The *replica set* ensures that the right number of *pods* are running
- What happens if pods disappear?

```
kubectl get pods
kubectl delete pod webapp1
kubectl get pods
```
