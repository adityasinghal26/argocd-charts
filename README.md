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

## Setup Repository in ArgoCD

To setup [this](https://github.com/adityasinghal26/argocd-charts) repository in ArgoCD, the `argocd-repositories.yaml` file can be applied using `kubectl` as below.

```
kubectl apply -f argocd-repositories.yaml
```

## Setup Master App in ArgoCD

Master app is responsible for applying `argocd-appofapps`, which in turn, will apply all the apps in `apps` folder. Apply the `argocd-master-app` using below command. 

```
kubectl apply -f argocd-master-app.yaml
```

During the creation of `argocd-appofapps`, it will also create a dedicated project `argocd-charts-project` This project can be considered as an example for further usage.

As per the architecture, each ApplicationSet will have its own AppProject to define a safe-space for the applications. This increases the control over the set of applications in an ApplicationSet. 
