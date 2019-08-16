# Expose your application

### Dev
`kubectl port-forward deployment/webapp1 8001:80`{{execute}}

### Within cluster
`kubectl expose deployment webapp1 --port=80`{{execute}}

### Outside cluster
[Expose Service in Public Clusters](https://github.source.internal.cba/pages/ApplicationInfrastructure/aws.appinfra.user.docs/4_kubernetes/loadbalancer-servicediscovery.html)


