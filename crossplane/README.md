# IDP Setup with Port and Crossplane

This guide walks you through setting up an Internal Developer Platform (IDP) using Port and Crossplane.

## Prerequisites

Before you begin, ensure you have the following:

- **Port Actions Knowledge**: Prior understanding of Port Actions is required. [Learn more about Port Actions here](link-to-port-actions-docs).
- **Control Plane**: A control plane for creating clusters and infrastructure (we'll use Crossplane).
- **GitOps Operator**: For automated cluster operations based on manifest changes (we'll use ArgoCD).
- **Helm**: Package manager for Kubernetes. [Installation guide](https://helm.sh/docs/intro/install/).

## 1. Crossplane Setup

> **Note**: If you don't have a Kubernetes cluster, create one locally using [kind](https://kind.sigs.k8s.io/).

### Install Crossplane
First, install Crossplane in your management cluster:

```bash
helm repo add crossplane-stable https://charts.crossplane.io/stable

helm repo update

helm upgrade --install crossplane crossplane-stable/crossplane --namespace crossplane-system --create-namespace --wait
```

### Install Crossplane Compositions

```bash
kubectl apply --filename ./crossplane/crossplane-config/provider-kubernetes-incluster.yaml

kubectl apply --filename ./crossplane/crossplane-config/provider-helm-incluster.yaml

kubectl wait --for=condition=healthy provider.pkg.crossplane.io --all --timeout=300s
```

## 2. ArgoCD Setup

### Installation

Now, let's install ArgoCD into the cluster or use an existing one.

```bash
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get pods -n argocd
```

### Access Configuration

- **Default Username**: `admin`
- **Get Password**:

  ```bash
  kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
  ```

### Access the UI

To access the ArgoCD UI using port forwarding to connect to the API server without exposing the service:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443 --address 0.0.0.0
```

Access the UI at: https://localhost:8080

## 3. GitOps Setup

Now to add the final piece in our automation, create an ArgoCD application that will be responsible for syncing the GitHub repository state into the management cluster so that crossplane creates the resources.

```bash
kubectl apply -f ./argocd/apps.yaml
```


## 4. Testing the Setup

1. Navigate to the self-service page
2. Locate the "Create Cluster" action
3. Fill in the required cluster properties
4. Click "Execute" to trigger the creation process

### What Happens Behind the Scenes:
1. GitHub Actions generates a manifest
2. The manifest is copied to your repository's infra folder
3. ArgoCD synchronizes the manifest with the control plane cluster
4. Crossplane creates the cluster resources in the specified provider

✨ **Success!** You can now manage clusters directly from Port.

---

## Troubleshooting

If you encounter issues during setup, please check:
- All prerequisites are properly installed
- Kubernetes cluster is running and accessible
- Proper permissions are configured for all components

## Support

For additional support:
- [Crossplane Documentation](https://crossplane.io/docs/)
- [ArgoCD Documentation](https://argo-cd.readthedocs.io/)
- [Port Documentation](https://docs.getport.io/)