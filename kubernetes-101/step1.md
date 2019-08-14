## Basic things we can ask Kubernetes to do

- Start 5 containers using image `atseashop/api:v1.3`

- Place an internal load balancer in front of these containers

- Start 10 containers using image `atseashop/webfront:v1.3`

- Place a load balancer in front of these containers

- It's Black Friday (or Christmas), traffic spikes, grow our cluster and add containers

- New release! Replace my containers with the new image `atseashop/webfront:v1.4`

- Keep processing requests during the upgrade; update my containers one at a time

---

## Other things that Kubernetes can do for us

- Basic autoscaling

- Blue/green deployment, canary deployment

- Long running services, but also batch (one-off) jobs

- Overcommit our cluster and *evict* low-priority jobs

- Run services with *stateful* data (databases etc.)

- Fine-grained access control defining *what* can be done by *whom* on *which* resources

- Integrating third party services (*service catalog*)

- Automating complex tasks (*operators*)
