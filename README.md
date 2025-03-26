# test-prometheus

## Summary  
A simple hands-on guide to deploy Prometheus on Kubernetes and verify it's working correctly.

## Tool Installation  
Make sure the following tools are installed:

- [Install `kind`](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)  
- [Install `kubectl`](https://kubernetes.io/docs/tasks/tools/install-kubectl/)  
- [Install `helm`](https://helm.sh/docs/intro/install/)  
- [Install `helmfile`](https://github.com/helmfile/helmfile)

## Setup

### Create Cluster  
Create a Kubernetes cluster with Kind:
```bash
kind create cluster --name gumamon --config kind.yaml
```

Switch the current context to the new cluster:
```bash
kubectl config use-context kind-gumamon
```

Verify the current context:
```bash
kubectl config get-contexts
```

Check available namespaces:
```bash
kubectl get ns
```

### Deploy Manifests  
Preview what will be deployed:
```bash
helmfile template
```

Apply the manifests:
```bash
helmfile sync
```

### Name Resolution Settings  
Edit your `/etc/hosts` file:
```bash
sudo vim /etc/hosts
```

Add entries like:
```
# Example
127.0.0.1    prometheus-server.example.com
127.0.0.1    go-metrics-sample.example.com
```

> **Note**  
> - If Kind is running inside a virtual machine, use the VM’s IP address instead of `127.0.0.1`.  
> - The `/etc/hosts` path shown here is an example for macOS/Linux systems.

### Verify Operation  
Check if the sample application is running:  
- http://go-metrics-sample.example.com/ping

Access the Prometheus server to check configuration and metrics:  
- http://prometheus-server.example.com

### Clean Up the Test Environment  
To delete the Kind cluster:  
```bash
kind delete cluster --name gumamon
```

## Versions  
- Kind: v0.27.0  
- Helm: v3.17.2  
- Helmfile: v0.171.0  
- Kubernetes: v1.32.2  
- Kubectl: v1.32.2
