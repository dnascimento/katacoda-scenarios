#### Install Kubernetes in your laptop

[Kubernetes in Docker](https://github.ai.cba/appinfra/kindest.node)

Please use **0.2.1**

- [Windows](https://github.com/kubernetes-sigs/kind/releases/download/0.2.1/kind-windows-amd64)
- [Linux](https://github.com/kubernetes-sigs/kind/releases/download/0.2.1/kind-linux-amd64)
- OSX:

```bash
curl -Lo ./kind-darwin-amd64 https://github.com/kubernetes-sigs/kind/releases/download/0.2.1/kind-darwin-amd64
chmod +x ./kind-darwin-amd64
mv ./kind-darwin-amd64 /usr/local/bin/kind
```

## Use it

```bash
kind create cluster --image docker.artifactory.ai.cba/dagosca/kindest.node:v1.13.4
```
