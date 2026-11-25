🚖 Varun Cabs Bangalore - End-to-End DevOps Project
📌 Project Overview
This project demonstrates a complete DevOps implementation for deploying and managing a production-ready static website using AWS Cloud and modern DevOps practices.

The project started as a simple website deployment and evolved into a complete DevOps learning journey covering:

Linux Administration
AWS Cloud
Git & GitHub
Docker
Docker Hub
Route53 DNS
Nginx Reverse Proxy
SSL Certificates
GitHub Actions
Jenkins CI/CD
Kubernetes (K3s)
🌐 Live Project
Website
👉 https://varun-cabs.site

GitHub Repository
👉 https://github.com/santhosh2958-dot/varun-cabs

Docker Hub Repository
👉 https://hub.docker.com/r/santhosh2958/varun-cabs

🛠️ Technologies Used
Cloud
AWS EC2
Route53
Security Groups
Operating System
Ubuntu Linux
Version Control
Git
GitHub
Containerization
Docker
Docker Hub
Web Server
Nginx
SSL
Let's Encrypt
Certbot
CI/CD
GitHub Actions
Jenkins
Container Orchestration
Kubernetes (K3s)
🏗️ High-Level Architecture
Developer
    │
    ▼
GitHub Repository
    │
    ├───────────────┐
    │               │
    ▼               ▼
GitHub Actions   Jenkins
    │               │
    ▼               ▼
Docker Hub    Docker Build
                  │
                  ▼
            Docker Hub Push
                  │
                  ▼
             Kubernetes
                  │
                  ▼
               Ingress
                  │
                  ▼
           varun-cabs.site
🚦 Application Traffic Flow
Customer Browser
       │
       ▼
varun-cabs.site
       │
       ▼
Route53 DNS
       │
       ▼
AWS EC2
       │
       ▼
Nginx Reverse Proxy
       │
       ▼
Docker Container
       │
       ▼
Varun Cabs Website
☁️ Phase 1 - AWS EC2 Setup
Objective
Create a Linux server for hosting and deploying applications.

EC2 Configuration
Operating System
Ubuntu Linux
Security Group Rules
Port	Purpose
22	SSH
80	HTTP
443	HTTPS
9090	Jenkins
50000	Jenkins Agent
🐧 Phase 2 - Linux Administration
Commands Learned
pwd
ls -la
cd
cat
nano
vim
grep
find
free -h
df -h
top
Key Learning
Linux is the foundation of modern DevOps and Cloud Infrastructure.

🐳 Phase 3 - Docker
Dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
Build Docker Image
docker build -t varun-cabs:v1 .
Run Container
docker run -d \
--name varun-cabs-app \
-p 8080:80 \
varun-cabs:v2
Concepts Learned
Docker Images
Docker Containers
Docker Networking
Port Mapping
Dockerfile
Container Lifecycle
🧾 Phase 4 - Git and GitHub
Initialize Repository
git init
git add .
git commit -m "Initial Commit"
git push origin main
Concepts Learned
Repository
Commit
Push
Pull
Branching
Version Control
📦 Phase 5 - Docker Hub
Login
docker login
Push Image
docker push santhosh2958/varun-cabs:v2

docker push santhosh2958/varun-cabs:latest
Benefits
Central Image Registry
Image Versioning
Easy Deployments
Image Sharing
🌎 Phase 6 - Route53 DNS
Domain
varun-cabs.site
Purpose
Map Domain Name to AWS EC2 Instance.

Concepts Learned
DNS
A Records
Domain Resolution
🌐 Phase 7 - Nginx Reverse Proxy
Problem
Docker container was using:

Port 80
Nginx also required:

Port 80
Solution
Application moved to:

localhost:8080
Nginx forwards traffic to:

localhost:8080
Architecture
Internet
    │
    ▼
Nginx
    │
    ▼
Docker Container
🔒 Phase 8 - SSL Certificate
Tools Used
Certbot
Let's Encrypt
Command
sudo certbot --nginx
Results
✅ HTTPS Enabled

✅ SSL Certificate Installed

✅ Auto Renewal Enabled

Website:

https://varun-cabs.site
⚙️ Phase 9 - GitHub Actions
Workflow
Developer
      │
      ▼
Git Push
      │
      ▼
GitHub Actions
      │
      ▼
Docker Build
      │
      ▼
Docker Hub Push
Concepts Learned
Continuous Integration
Workflow Automation
GitHub Secrets
🤖 Phase 10 - Jenkins
Installation
docker run -d \
--name jenkins \
-p 9090:8080 \
-p 50000:50000 \
-v jenkins_home:/var/jenkins_home \
jenkins/jenkins:lts
Purpose
Automate CI/CD Pipelines.

🔗 Phase 11 - Jenkins GitHub Integration
Pipeline Flow
GitHub
    │
    ▼
Jenkins
    │
    ▼
Git Checkout
Result
✅ Repository cloned successfully

✅ Workspace created

✅ Files fetched from GitHub

🏭 Phase 12 - Jenkins Docker Build
Pipeline Flow
GitHub
    │
    ▼
Jenkins
    │
    ▼
Docker Build
Issues Solved
Error
docker: not found
Solution
Created custom Jenkins image including Docker CLI.

Error
permission denied docker.sock
Solution
Mounted Docker Socket:

-v /var/run/docker.sock:/var/run/docker.sock
🚀 Phase 13 - Jenkins Docker Hub Push
CI/CD Flow
GitHub
    │
    ▼
Jenkins
    │
    ▼
Docker Build
    │
    ▼
Docker Login
    │
    ▼
Docker Hub Push
Result
✅ Docker Image Built

✅ Docker Login Successful

✅ Docker Image Pushed

Repository:

santhosh2958/varun-cabs
☸️ Phase 14 - Kubernetes (K3s)
Installation
curl -sfL https://get.k3s.io | sh -
Verify:

kubectl get nodes
🔹 Kubernetes Components
Pod
kubectl run varun-cabs-pod \
--image=santhosh2958/varun-cabs:v2
Purpose
Smallest deployable unit in Kubernetes.

Deployment
kubectl create deployment varun-cabs \
--image=santhosh2958/varun-cabs:v2 \
--replicas=2
Purpose
Manage application pods.

ReplicaSet
Purpose
Provides:

Self-Healing
High Availability
Test
kubectl delete pod <pod-name>
Kubernetes automatically recreated the Pod.

Services
ClusterIP
Internal communication inside cluster.

NodePort
Expose Application outside cluster.

kubectl expose deployment varun-cabs \
--type=NodePort
Ingress
Traefik used as Ingress Controller.

Flow
Internet
    │
    ▼
Ingress
    │
    ▼
Service
    │
    ▼
Pods
✅ Problems Solved
502 Bad Gateway
Cause
Application Container Stopped
Resolution
docker start varun-cabs-app
Docker Containers Not Starting After EC2 Restart
Resolution
docker update --restart unless-stopped varun-cabs-app

docker update --restart unless-stopped jenkins
Jenkins Docker Integration
Errors
docker: not found

permission denied
Solution
Custom Jenkins Image
Docker Socket Mapping
📊 Current Project Status
✅ Linux

✅ AWS EC2

✅ Git

✅ GitHub

✅ Docker

✅ Docker Hub

✅ Route53

✅ Nginx

✅ SSL

✅ GitHub Actions

✅ Jenkins

✅ Jenkins GitHub Integration

✅ Jenkins Docker Build

✅ Jenkins Docker Hub Push

✅ Kubernetes

✅ Pod

✅ Deployment

✅ ReplicaSet

✅ Self-Healing

✅ Services

✅ NodePort

✅ ClusterIP

✅ Ingress

✅ Traefik

🎯 Future Enhancements
DevSecOps
SonarQube
Trivy
Kubernetes Advanced
ConfigMaps
Secrets
Persistent Volumes
HPA
Monitoring
Prometheus
Grafana
GitOps
ArgoCD
Infrastructure as Code
Terraform
🎓 Learning Outcome
This project provided practical experience with:

Linux Administration
AWS Cloud
Git & GitHub
Docker & Docker Hub
Nginx
SSL/TLS Certificates
GitHub Actions
Jenkins CI/CD
Kubernetes Orchestration
Troubleshooting Production Issues
🔗 Project Links
Website
https://varun-cabs.site

GitHub Repository
https://github.com/santhosh2958-dot/varun-cabs

Docker Hub
https://hub.docker.com/r/santhosh2958/varun-cabs

👨‍💻 Author
Santhosh Kumar

Project Type
End-to-End DevOps & Kubernetes Learning Project 🚀
