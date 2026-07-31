Markdown
# 🛠️ Project Commands Reference

Here is the complete list of commands used to provision the infrastructure, install ArgoCD, and deploy the Cats vs Dogs Voting App.

### 1. Terraform (Infrastructure Provisioning)
Run these inside your terraform directory:

terraform init
terraform plan
terraform apply --auto-approve
2. ArgoCD Setup & Installation
Create the namespace and install ArgoCD (using server-side apply to avoid CRD size limits):


kubectl create namespace argocd
kubectl apply --server-side -n argocd -f [https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml](https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml)
3. Expose ArgoCD & Fix Lab Proxy Issues
Change the service type to NodePort and force HTTP mode to avoid the infinite redirect loop (ERR_TOO_MANY_REDIRECTS):


# Expose via NodePort
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'

# Bypass SSL/Proxy loop by running insecure mode
kubectl patch deployment argocd-server -n argocd --type='json' -p='[{"op": "add", "path": "/spec/template/spec/containers/0/command/-", "value": "--insecure"}]'
4. Get ArgoCD Credentials & Port

# Retrieve the auto-generated admin password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
echo ""

# Check which port ArgoCD is running on (Look for the 30xxx port)
kubectl get svc argocd-server -n argocd
5. Deploy the Application
Apply the ArgoCD application manifest to sync the GitHub repository with the cluster:


kubectl apply -f voting-app.yaml
6. Verify Deployment
Check if all the pods (db, redis, result, vote, worker) are running successfully:

Bash
kubectl get pods -n voting-app
kubectl get svc -n voting-app

***

Bhai tumhara GitHub repo ab ekdum professional lagega: ek taraf `README.md` jisme theory aur architecture hoga, aur doosri taraf `commands.md` jisme raw commands hongi. Copy-paste karo aur full marks lo!
