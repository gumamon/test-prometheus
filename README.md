# test-prometheus

# Setup
* Install [KinD](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)
* Create cluster `kind create cluster --name my-cluster --config kind.yaml`
* Install `kubectl`
* Install `helm`

# Test
* `kubectl config get-contexts` 
* `kubectl config use-context kind-my-cluster `
* `kubectl get nodes`

# helm install
* `helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
* `helm repo list`
* `helm search repo prometheus-community`
* `helm dependency build`
* `helm upgrade prom ./ --install --namespace prometheus --create-namespace --dry-run`
* `helm show values prometheus-community/prometheus"`
