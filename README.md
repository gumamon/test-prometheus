# test-prometheus

# Install
* [Install `KinD`](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)
* [Install `kubectl`](https://kubernetes.io/ja/docs/tasks/tools/install-kubectl-linux/#install-kubectl-binary-with-curl-on-linux)
* [Install `helm`](https://helm.sh/ja/docs/intro/install/)
* [Install helmfile](https://github.com/helmfile/helmfile)

# Setup
kind create cluster --name gumamon --config kind.yaml
kubectl config get-contexts 
kubectl get ns

# versions
* kind: version 0.27.0
* helm: v3.17.2
* helmfile: 0.171.0
* kubernetes: v1.32.2
* kubectl: v1.32.2
---
memo

# Test
* `kubectl config get-contexts` 
* `kubectl config use-context kind-gumamon `
* `kubectl get nodes`

# helm install
* `helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
* `helm repo list`
* `helm search repo prometheus-community`
* `helm dependency build`
* `helm upgrade prom ./ --install --namespace prometheus --create-namespace --dry-run`
* `helm upgrade prom ./ --install --namespace prometheus --create-namespace`
* `helm show values prometheus-community/prometheus"`


---

helmfile -f helmfile.yaml template
helmfile -f helmfile.yaml sync
