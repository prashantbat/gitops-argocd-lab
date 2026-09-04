# GitOps with Argo CD Lab

A hands-on lab for learning GitOps continuous delivery on a K3s cluster with Argo CD.

## Goal

Use Git as the source of truth for Kubernetes application configuration. Argo CD continuously compares the desired state stored in this repository with the live state in the cluster and reports or reconciles any difference.

## Lab environment

- Kubernetes: K3s on AWS EC2
- GitOps controller: Argo CD
- Manifest management: Kustomize
- Source control: GitHub

## Learning roadmap

1. Deploy a sample application from this repository with an Argo CD `Application`.
2. Observe manual synchronization and application health.
3. Add `dev` and `prod` Kustomize overlays.
4. Demonstrate configuration drift and Argo CD self-healing.
5. Use ApplicationSets to generate applications from templates.
6. Connect CI image builds to GitOps-based delivery.

## Architecture

```text
GitHub repository (desired state)
            |
            v
Argo CD repo-server renders manifests
            |
            v
Argo CD application-controller compares desired and live state
            |
            v
K3s cluster deploys and runs the application
```

## Repository layout

```text
apps/       # application manifests and environment overlays
argocd/     # Argo CD Application and ApplicationSet definitions
```

> This repository contains no secrets. Sensitive values should be managed through an approved secret-management solution, not committed to Git.

