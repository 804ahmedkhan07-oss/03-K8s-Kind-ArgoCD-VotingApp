
#  Project Commands (Terraform + ArgoCD)

## 1. Terraform (Infrastructure)

# Initialize (Plugins download 
terraform init

# Preview changes 
terraform plan

# Deploy infrastructure (Creation)
terraform apply -auto-approve

# Delete infrastructure (Thanos move)
terraform destroy -auto-approve

# ArgoCD (GitOps Deployment)

# Master Application deploy karna
kubectl apply -f root-app/root-application.yaml -n argocd

# checking application status 
argocd app list

# Force manual sync (if webhook not present)
argocd app sync root-master-application


# Debugging & K8s Commands

# Pods checking 
kubectl get pods -n <namespace>
# Error  Logs checking
kubectl logs <pod-name> -n <namespace>

# Pod details (CrashLoopBackOff or other errors finding )
kubectl describe pod <pod-name> -n <namespace>
