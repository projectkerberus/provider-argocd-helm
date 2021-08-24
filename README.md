# Provider ArgoCD Helm chart

This folder contains Helm charts that can easily create a Kubernetes deployment of the Crossplane Provider ArgoCD.

## Prerequisite

Since the Crossplane Provider ArgoCD container image, is in a private repository, it's mandatory to create a [personal access token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) and store as docker registry secret.

```sh
$ kubectl create secret docker-registry ghcr-cred \
	--namespace argo-system --docker-server=ghcr.io \
	--docker-password=$(GITHUB_TOKEN) --docker-username=projectkerberus
```

## Installation

Add this repository to Helm:

```sh
$ helm repo add provider-argocd https://projectkerberus.io/provider-argocd-helm
```

```sh
helm upgrade --install --namespace argo-system --create-namespace \
    provider-argocd provider-argocd/provider-argocd
```

