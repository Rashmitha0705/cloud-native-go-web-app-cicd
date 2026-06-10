# Go Web Application

Overview

This project is a cloud-native CI/CD pipeline for a Go web application deployed on AWS EKS using modern DevOps tools.

It demonstrates an end-to-end workflow:

👉 Code → Build → Docker Image → Kubernetes → Helm → ArgoCD → Deployment

### Architecture

GitHub Repository
        │
        │  (GitHub Actions CI Pipeline)
        ▼
Docker Image (DockerHub: rashmitha0705/go-web-app)
        │
        ▼
AWS EKS Cluster (Kubernetes)
        │
        ├── Helm Chart Deployment
        │
        ▼
ArgoCD (GitOps Controller)
        │
        ▼
Go Web Application (Pods + Service)
        │
        ▼
Access via External IP (/home, /courses)

### Tech Stack

🐹 Go (Golang) – Web application
📦 Docker – Containerization
☸️ Kubernetes – Orchestration (EKS)
☁️ AWS EKS – Managed Kubernetes cluster
⛵ Helm – Deployment templating
🔄 ArgoCD – GitOps CD tool
⚙️ GitHub Actions – CI pipeline
🧰 eksctl – EKS cluster creation

### How to Access the Application

Once deployed on EKS, the application is exposed using a LoadBalancer service.

🔗 Application URLs:
http://<EXTERNAL-IP>/home
http://<EXTERNAL-IP>/courses

✔ Access is only possible via External IP (not localhost)

### GitHub Actions (CI Pipeline)
Where to see it:

### GitHub Repository → Actions tab

CI Pipeline does:
Checkout code
Build Go application
Build Docker image
Push image to DockerHub
Update Helm chart
Trigger ArgoCD sync

### Docker Commands
docker build -t rashmitha0705/go-web-app:v1 .
docker push rashmitha0705/go-web-app:v1
docker run -p 8080:8080 rashmitha0705/go-web-app:v1
### Kubernetes Commands
kubectl get pods
kubectl get svc
kubectl get nodes -o wide
kubectl describe pod <pod-name>
kubectl logs <pod-name>

### CI/CD Flow Explanation (Simple Understanding)
Developer pushes code to GitHub
GitHub Actions builds Docker image
Image is pushed to DockerHub
ArgoCD detects changes in Git repo
Helm deploys updated version to EKS
Application is automatically updated


### Key Learnings
Real-world CI/CD pipeline design
Kubernetes deployment on AWS EKS
GitOps workflow using ArgoCD
Helm-based application deployment
Docker image versioning and automation
Cloud-native architecture understanding
