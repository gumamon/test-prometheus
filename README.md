# test-prometheus
# Summary
A simple hands-on guide to deploy Prometheus on Kubernetes and verify it's working correctly.

# Tool installation
* [Install `kind`](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)
* [Install `kubectl`](https://kubernetes.io/ja/docs/tasks/tools/install-kubectl-linux/#install-kubectl-binary-with-curl-on-linux)
* [Install `helm`](https://helm.sh/ja/docs/intro/install/)
* [Install helmfile](https://github.com/helmfile/helmfile)

# Setup
## Create cluster
create cluster
```
kind create cluster --name gumamon --config kind.yaml
```
change context
```
kubectl config use-context kind-gumamon
```
check context
```
kubectl config get-contexts 
```
get namespace from cluster 
```
kubectl get ns
```

## Deploy manifests
dryrun
```
helmfile template
```
deploy
```
helmfile sync
```

## Name resolution settings
```
sudo vim /etc/hosts
```
```
# example
127.0.0.1    prometheus-server.example.com
127.0.0.1    go-metrics-sample.example.com
```
> [!NOTE]
> * If Kind is running on a virtual machine, please set the IP address of the virtual machine.
> * `/etc/hosts` is an example of a MAC, etc.


# versions
* kind: version 0.27.0
* helm: v3.17.2
* helmfile: 0.171.0
* kubernetes: v1.32.2
* kubectl: v1.32.2
