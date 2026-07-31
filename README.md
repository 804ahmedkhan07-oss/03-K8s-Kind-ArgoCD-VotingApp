# 🐾 GitOps-Driven 3-Tier Voting App (Cats vs Dogs)

Welcome to my DevOps portfolio project! This project demonstrates a complete end-to-end GitOps workflow for a multi-tier microservices application (the classic "Cats vs. Dogs" voting app). 

The infrastructure is provisioned using **Terraform**, and the application lifecycle is managed automatically using **ArgoCD** on a **Kubernetes (K8s)** cluster.

## 📸 Project Screenshots

### The Voting App (Cats vs Dogs)
![Cats vs Dogs App](https://github.com/804ahmedkhan07-oss/03-K8s-Kind-ArgoCD-VotingApp/blob/main/catvsdog.jpg)
*Users can vote for their favorite pet, and the results are processed in real-time.*

### ArgoCD UI (Live Sync)
![ArgoCD UI](https://github.com/804ahmedkhan07-oss/03-K8s-Kind-ArgoCD-VotingApp/blob/main/ArgoCd.jpg)
*ArgoCD automatically syncing the K8s manifests from GitHub to the cluster.*

---

## 🏗️ Tech Stack
* **Infrastructure as Code:** Terraform
* **Container Orchestration:** Kubernetes (K8s)
* **GitOps Tooling:** ArgoCD
* **Microservices:** Python (Vote), Node.js (Result), .NET (Worker), Redis (Queue), PostgreSQL (DB)

---

## 🚀 How to Run (Step-by-Step)

### Step 1: Provision Infrastructure (Terraform)
First, we set up the baseline environment.
```bash
terraform init
terraform plan
terraform apply --auto-approve
