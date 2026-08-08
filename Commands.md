#!/bin/bash

# =======================================================
# 🚀 DevOps Commands Reference
# Note: Copy and run individual commands as needed.
# =======================================================

# 🌍 1. TERRAFORM (Infrastructure as Code)
# -------------------------------------------------------
# Initialize the working directory (Downloads plugins)
terraform init

# Preview changes (Shows what will be created)
terraform plan

# Deploy infrastructure (Provisions resources on AWS)
terraform apply -auto-approve

# Delete infrastructure (Destroys all resources)
terraform destroy -auto-approve


# ⚙️ 2. ARGOCD (GitOps Deployment)
# -------------------------------------------------------
# Deploy the Master/Root Application (App-of-Apps pattern)
kubectl apply -f root-app/root-application.yaml -n argocd

# Check the sync and health status of all ArgoCD apps
argocd app list

# Force a manual sync (If webhooks are not configured)
argocd app sync root-master-application


# 🔍 3. KUBERNETES & DEBUGGING
# -------------------------------------------------------
# List all pods in a specific namespace
kubectl get pods -n <namespace>

# Fetch the logs of a specific pod
kubectl logs <pod-name> -n <namespace>

# Inspect detailed pod events (For CrashLoopBackOff etc.)
kubectl describe pod <pod-name> -n <namespace>
    
