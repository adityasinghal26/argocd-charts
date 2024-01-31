# argocd-charts
Helm charts for various OpenSource tools to manage using ArgoCD


## Argo-CD Installation using Helm

Add Argo Helm repository and verify that the repo is created.

```
helm repo add argo https://argoproj.github.io/argo-helm
helm repo list
```

Next, we install Argo-CD in `argo` namespace from the above added repository.

```
helm upgrade argocd argo/argo-cd --install --namespace argo --create-namespace
```

In addition to ArgoCD installation, we need to install argo CLI. The steps for CLI installation can be followed for official [ArgoCD CLI documentation](https://argo-cd.readthedocs.io/en/stable/cli_installation/).

