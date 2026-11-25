# 🚖 Varun Cabs Bangalore
## End-to-End DevOps Project

![Project](https://img.shields.io/badge/Project-Varun%20Cabs-blue)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-orange)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![Kubernetes](https://img.shields.io/badge/Kubernetes-K3s-326CE5)
![Status](https://img.shields.io/badge/Status-Learning%20%26%20Deployment-success)

A real-world DevOps learning project to deploy and manage the **Varun Cabs Bangalore** website using Linux, AWS, Git, Docker, CI/CD, Jenkins, and Kubernetes.

The purpose of this project is to understand how a website moves from source code to a production-style deployment, how infrastructure is managed, and how Kubernetes maintains application availability.

🌐 **Live Website:** https://varun-cabs.site  
🌐 **WWW Website:** https://www.varun-cabs.site  
📦 **GitHub Repository:** https://github.com/santhosh2958-dot/varun-cabs  
🐳 **Docker Hub:** https://hub.docker.com/r/santhosh2958/varun-cabs

---

## 📚 Table of Contents

1. [Project Overview](#-project-overview)
2. [Project Objectives](#-project-objectives)
3. [DevOps Architecture](#-devops-architecture)
4. [Technologies Used](#-technologies-used)
5. [Project Infrastructure](#-project-infrastructure)
6. [Linux and EC2 Setup](#-linux-and-ec2-setup)
7. [Git and GitHub](#-git-and-github)
8. [Docker and Docker Hub](#-docker-and-docker-hub)
9. [Nginx and SSL](#-nginx-and-ssl)
10. [GitHub Actions CI/CD](#-github-actions-cicd)
11. [Jenkins CI/CD](#-jenkins-cicd)
12. [Kubernetes with K3s](#-kubernetes-with-k3s)
13. [Kubernetes Commands](#-kubernetes-commands)
14. [Kubernetes Self-Healing](#-kubernetes-self-healing)
15. [Services and Ingress](#-services-and-ingress)
16. [Troubleshooting](#-troubleshooting)
17. [Security Best Practices](#-security-best-practices)
18. [Project Status](#-project-status)
19. [Future Enhancements](#-future-enhancements)
20. [DevOps Interview Questions](#-devops-interview-questions)
21. [Kubernetes Interview Questions](#-kubernetes-interview-questions)
22. [Useful Commands Cheat Sheet](#-useful-commands-cheat-sheet)

---

## 🚀 Project Overview

This project demonstrates the DevOps lifecycle of a website.

A developer updates the website source code and pushes the changes to GitHub. The application is built into a Docker image, pushed to Docker Hub, and deployed to an AWS EC2 server or Kubernetes cluster.

The project includes:

- Linux server administration
- AWS EC2 infrastructure
- Git and GitHub source-code management
- Docker image creation and container deployment
- Docker Hub image registry
- Nginx reverse proxy
- Domain configuration using Route 53
- HTTPS using SSL certificates
- GitHub Actions automation
- Jenkins CI/CD learning
- Kubernetes deployment using K3s
- Kubernetes Pods, Deployments, ReplicaSets, Services, and Ingress
- Kubernetes self-healing and scaling

## 🎯 Project Objectives

The main objective is to learn DevOps through a practical project instead of only studying theory.

By completing this project, I want to understand:

- How to deploy a website on AWS EC2
- How to manage Linux servers
- How to use Git and GitHub
- How to build and run Docker containers
- How to automate application builds
- How to create CI/CD pipelines
- How to deploy applications using Kubernetes
- How Kubernetes provides self-healing
- How to expose applications using Services and Ingress
- How to monitor and troubleshoot applications

---

## 🏗️ DevOps Architecture

### Application deployment flow

```text
                    Developer
                       |
                       v
                 Git / GitHub
                       |
          +------------+------------+
          |                         |
          v                         v
   GitHub Actions                Jenkins
          |                         |
          +------------+------------+
                       |
                       v
                 Docker Build
                       |
                       v
                  Docker Hub
                       |
                       v
                  AWS EC2
                       |
                       v
               Kubernetes (K3s)
                       |
                       v
                 Deployment
                       |
                       v
                ReplicaSet
                       |
             +---------+---------+
             |                   |
             v                   v
          Pod 1                Pod 2
             |                   |
             +---------+---------+
                       |
                       v
                Kubernetes Service
                       |
                       v
                  Traefik Ingress
                       |
                       v
             https://varun-cabs.site
```

### How the architecture works

1. Developer modifies the website source code.
2. Code is pushed to GitHub.
3. GitHub Actions or Jenkins runs the build pipeline.
4. Docker builds an image containing the website.
5. The image is pushed to Docker Hub.
6. Kubernetes pulls the image from Docker Hub.
7. A Deployment manages the required number of Pods.
8. A Service provides stable access to the Pods.
9. Traefik Ingress routes HTTP traffic to the application.
10. The website is accessible through the configured domain.

---

## 🧰 Technologies Used

| Technology | Purpose |
|---|---|
| Linux / Ubuntu | Operating system and server administration |
| AWS EC2 | Cloud virtual machines |
| Git | Version control |
| GitHub | Source-code repository |
| Docker | Application containerization |
| Docker Hub | Docker image registry |
| Nginx | Web server and reverse proxy |
| Route 53 | DNS management |
| Let's Encrypt | SSL certificate |
| GitHub Actions | CI/CD automation |
| Jenkins | CI/CD pipeline learning |
| Kubernetes | Container orchestration |
| K3s | Lightweight Kubernetes distribution |
| Traefik | Kubernetes Ingress controller |

---

## ☁️ Project Infrastructure

### EC2 servers

The project uses separate EC2 environments for the website and Kubernetes learning.

| Server | Purpose |
|---|---|
| Original EC2 | Docker website, Nginx, Jenkins |
| Kubernetes EC2 | K3s cluster and Kubernetes application |

### Kubernetes EC2

- Instance name: `varun-cabs-k8s-server`
- Instance ID: `i-0e7877ff62900ac28`
- Public IP: `13.127.104.20`
- Private IP: `172.31.2.182`
- CPU: 2 vCPU
- Memory: approximately 1.9 GiB
- Kubernetes distribution: K3s

> AWS resource details may change. Always verify the current instance IP, instance state, and security-group rules in the AWS Console.

---

## 🐧 Linux and EC2 Setup

Linux is used to manage the cloud servers, install software, run containers, and troubleshoot the application.

### Basic Linux commands

```bash
# Current directory
pwd

# List files
ls -l

# List hidden files
ls -la

# Create directory
mkdir devops-project

# Change directory
cd devops-project

# Create file
touch README.md

# View file
cat README.md

# Edit file
nano README.md

# Copy file
cp file.txt backup.txt

# Move or rename file
mv old.txt new.txt

# Remove file
rm file.txt

# Disk usage
df -h

# Memory usage
free -h

# CPU and processes
top

# Current user
whoami
```

### Useful system commands

```bash
# Check OS
cat /etc/os-release

# Check kernel
uname -r

# Check IP addresses
ip addr

# Check running services
systemctl list-units --type=service --state=running

# Check service status
sudo systemctl status nginx

# Start service
sudo systemctl start nginx

# Stop service
sudo systemctl stop nginx

# Restart service
sudo systemctl restart nginx

# Enable service at boot
sudo systemctl enable nginx
```

### EC2 connection

```bash
ssh -i my-key.pem ubuntu@<EC2-PUBLIC-IP>
```

Replace `<EC2-PUBLIC-IP>` with your current EC2 public IP.

---

## 🔧 Git and GitHub

Git tracks changes to the project source code. GitHub stores the repository remotely.

### Common Git commands

```bash
# Check Git version
git --version

# Initialize repository
git init

# Check repository status
git status

# Add all changes
git add .

# Commit changes
git commit -m "Update website"

# Add remote repository
git remote add origin git@github.com:santhosh2958-dot/varun-cabs.git

# Check remote
git remote -v

# Push code
git push origin main

# Pull latest code
git pull origin main
```

### Git workflow

```text
Modify Code
    |
    v
git add .
    |
    v
git commit
    |
    v
git push
    |
    v
GitHub Repository
```

### Safely update local repository

If GitHub contains commits that are not present locally:

```bash
git pull origin main --rebase
git push origin main
```

If a conflict occurs, resolve the conflict, stage the corrected file, and continue the rebase:

```bash
git add README.md
git rebase --continue
git push origin main
```

Do not use `git push --force` unless you fully understand the consequences.

---

## 🐳 Docker and Docker Hub

Docker packages an application and its dependencies into an image. A container is a running instance of an image.

### Dockerfile

The website uses an Nginx base image to serve the HTML page.

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

### Dockerfile explanation

| Instruction | Explanation |
|---|---|
| `FROM` | Selects the base image |
| `COPY` | Copies website content into the image |
| `EXPOSE` | Documents the container port |

### Build Docker image

```bash
docker build -t varun-cabs:v2 .
```

### Run container

```bash
docker run -d \
  --name varun-cabs-app \
  -p 8080:80 \
  --restart unless-stopped \
  varun-cabs:v2
```

### Docker commands

```bash
# List images
docker images

# List running containers
docker ps

# List all containers
docker ps -a

# View container logs
docker logs varun-cabs-app

# Follow logs
docker logs -f varun-cabs-app

# Stop container
docker stop varun-cabs-app

# Start container
docker start varun-cabs-app

# Restart container
docker restart varun-cabs-app

# Remove container
docker rm varun-cabs-app

# Remove image
docker rmi varun-cabs:v2

# Inspect container
docker inspect varun-cabs-app
```

### Push image to Docker Hub

```bash
docker login

docker tag varun-cabs:v2 santhosh2958/varun-cabs:v2

docker push santhosh2958/varun-cabs:v2
```

### Pull image

```bash
docker pull santhosh2958/varun-cabs:v2
```

---

## 🌐 Nginx and SSL

Nginx is used as a web server and reverse proxy.

A reverse proxy receives client requests and forwards them to the backend application.

### Example request flow

```text
Browser
   |
   v
Domain Name
   |
   v
Nginx :443
   |
   v
Docker Application :8080
   |
   v
Container Nginx :80
```

### Nginx service commands

```bash
# Check Nginx
sudo systemctl status nginx

# Test configuration
sudo nginx -t

# Reload configuration
sudo systemctl reload nginx

# Restart Nginx
sudo systemctl restart nginx
```

### SSL

SSL/TLS provides encrypted communication between the browser and the website.

The project uses a Let's Encrypt certificate for HTTPS.

Website:

- https://varun-cabs.site
- https://www.varun-cabs.site

---

## 🔄 GitHub Actions CI/CD

GitHub Actions automates the application build and image publishing process.

### Pipeline flow

```text
Git Push
   |
   v
GitHub Actions
   |
   v
Docker Build
   |
   v
Docker Hub Login
   |
   v
Docker Image Push
```

### What the pipeline does

1. Detects a code change pushed to GitHub.
2. Checks out the source code.
3. Builds the Docker image.
4. Authenticates with Docker Hub using GitHub Secrets.
5. Pushes the image to Docker Hub.

### GitHub Secrets

Store sensitive values in GitHub repository settings:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

Never hardcode Docker Hub passwords or tokens in the workflow file.

---

## 🧩 Jenkins CI/CD

Jenkins is used to learn continuous integration and continuous delivery.

### Jenkins pipeline flow

```text
Developer
   |
   v
GitHub
   |
   v
Jenkins
   |
   v
Git Checkout
   |
   v
Docker Build
   |
   v
Docker Hub Push
   |
   v
Deployment
```

### Jenkins container

The Jenkins container is configured to run on the original EC2 server.

Common commands:

```bash
# Check Jenkins container
docker ps

# Jenkins logs
docker logs jenkins

# Restart Jenkins
docker restart jenkins

# Open Jenkins container shell
docker exec -it jenkins bash

# Check Docker CLI inside Jenkins
docker exec -it jenkins docker --version
```

Jenkins web interface is available through the configured EC2 address and port.

> Mounting `/var/run/docker.sock` into Jenkins gives Jenkins powerful control over the Docker host. Use this only in a trusted learning environment and protect Jenkins credentials and access.

---

## ☸️ Kubernetes with K3s

Kubernetes manages containerized applications. K3s is a lightweight Kubernetes distribution suitable for learning and small environments.

### Kubernetes architecture

```text
Kubernetes Cluster
        |
        v
      Node
        |
        v
    Deployment
        |
        v
    ReplicaSet
        |
    +---+---+
    |       |
    v       v
   Pod 1   Pod 2
    |       |
    v       v
Container Container
```

### Important Kubernetes objects

| Object | Purpose |
|---|---|
| Node | Machine that runs Kubernetes workloads |
| Pod | Smallest deployable Kubernetes unit |
| Deployment | Manages application replicas and updates |
| ReplicaSet | Maintains the desired number of Pods |
| Service | Provides stable network access to Pods |
| ConfigMap | Stores non-sensitive configuration |
| Secret | Stores sensitive configuration data |
| Ingress | Routes HTTP/HTTPS traffic to Services |

### Check K3s

```bash
sudo systemctl status k3s

sudo systemctl start k3s

sudo systemctl restart k3s

sudo systemctl enable k3s
```

### Check Kubernetes node

```bash
kubectl get nodes
```

Expected status:

```text
NAME              STATUS   ROLES
ip-172-31-2-182   Ready    control-plane
```

---

## 📦 Kubernetes Deployment

The Varun Cabs application is managed by a Deployment named `varun-cabs`.

### Check Deployment

```bash
kubectl get deployments
```

Expected:

```text
NAME         READY   UP-TO-DATE   AVAILABLE
varun-cabs   2/2     2            2
```

### Check Pods

```bash
kubectl get pods

kubectl get pods -o wide
```

### Check ReplicaSets

```bash
kubectl get replicasets
```

### Deployment commands

```bash
# Describe Deployment
kubectl describe deployment varun-cabs

# Scale to 3 replicas
kubectl scale deployment varun-cabs --replicas=3

# Scale back to 2 replicas
kubectl scale deployment varun-cabs --replicas=2

# Check rollout
kubectl rollout status deployment varun-cabs

# View rollout history
kubectl rollout history deployment varun-cabs

# Restart Deployment
kubectl rollout restart deployment varun-cabs
```

---

## 🛠️ Kubernetes Commands

### Pods

```bash
# List Pods
kubectl get pods

# List Pods across all namespaces
kubectl get pods -A

# Detailed Pod information
kubectl describe pod <POD-NAME>

# View Pod logs
kubectl logs <POD-NAME>

# Follow logs
kubectl logs -f <POD-NAME>

# Execute command inside container
kubectl exec -it <POD-NAME> -- sh

# Delete Pod
kubectl delete pod <POD-NAME>
```

### Deployments

```bash
kubectl get deployments

kubectl describe deployment varun-cabs

kubectl edit deployment varun-cabs

kubectl scale deployment varun-cabs --replicas=3

kubectl rollout status deployment varun-cabs

kubectl rollout history deployment varun-cabs

kubectl rollout undo deployment varun-cabs
```

### Namespaces

```bash
# List namespaces
kubectl get namespaces

# Create namespace
kubectl create namespace dev

# List Pods in namespace
kubectl get pods -n dev

# Delete namespace
kubectl delete namespace dev
```

### Services

```bash
kubectl get services

kubectl describe service varun-cabs-service

kubectl get endpoints varun-cabs-service
```

### YAML deployment

Apply a Kubernetes YAML file:

```bash
kubectl apply -f deployment.yaml
```

Check resources:

```bash
kubectl get all
```

`kubectl get all` displays common resources in the current namespace; it does not display every Kubernetes resource.

---

## 🔁 Kubernetes Self-Healing

One of the most important Kubernetes features is self-healing.

### Practical test performed

The Deployment was running 2 Pods:

```text
varun-cabs-cb48c98f8-c6mb4
varun-cabs-cb48c98f8-lssz5
```

One Pod was deleted:

```bash
kubectl delete pod varun-cabs-cb48c98f8-c6mb4
```

Kubernetes automatically created a replacement Pod:

```text
varun-cabs-cb48c98f8-64r6j
```

The Deployment continued to maintain 2 replicas.

### What happened?

```text
Desired replicas = 2
        |
        v
One Pod deleted
        |
        v
ReplicaSet detects only 1 Pod
        |
        v
ReplicaSet creates replacement Pod
        |
        v
2 Pods Running
```

This demonstrates Kubernetes self-healing.

---

## 🔌 Kubernetes Services and Ingress

### ClusterIP Service

A ClusterIP Service provides internal communication within the Kubernetes cluster.

Current Service:

```text
varun-cabs-service
```

Check:

```bash
kubectl get services
```

### NodePort Service

The NodePort Service exposes the application on a port on the Kubernetes node.

Current configuration:

```text
Service name: varun-cabs-nodeport
Service port: 80
NodePort:     30080
```

Test locally on the EC2 server:

```bash
curl -I http://127.0.0.1:30080
```

Test through the EC2 public IP if the Security Group allows port 30080:

```bash
curl -I http://13.127.104.20:30080
```

### Ingress

Ingress routes HTTP requests based on hostnames and paths.

Current Ingress:

```text
varun-cabs-ingress
```

Ingress controller:

```text
Traefik
```

Hosts:

```text
varun-cabs.site
www.varun-cabs.site
```

Check:

```bash
kubectl get ingress

kubectl describe ingress varun-cabs-ingress
```

### Ingress request flow

```text
User Browser
     |
     v
Domain DNS
     |
     v
Kubernetes Node
     |
     v
Traefik Ingress Controller
     |
     v
varun-cabs-service
     |
     v
Application Pods
```

---

## 🐛 Troubleshooting

### Pod is not running

```bash
kubectl get pods -o wide

kubectl describe pod <POD-NAME>

kubectl logs <POD-NAME>
```

### Deployment is not ready

```bash
kubectl get deployment varun-cabs

kubectl describe deployment varun-cabs

kubectl get replicasets
```

### Website is not accessible

```bash
kubectl get pods

kubectl get services

kubectl get ingress

kubectl get endpoints varun-cabs-service
```

Test NodePort locally:

```bash
curl -I http://127.0.0.1:30080
```

### K3s is not running

```bash
sudo systemctl status k3s

sudo journalctl -u k3s -n 100 --no-pager

sudo systemctl restart k3s
```

### Docker container is not running

```bash
docker ps -a

docker logs varun-cabs-app

docker start varun-cabs-app
```

---

## 🔐 Security Best Practices

- Do not commit AWS access keys, private keys, passwords, or tokens to GitHub.
- Use GitHub Secrets for CI/CD credentials.
- Use IAM roles and least-privilege permissions where possible.
- Restrict EC2 Security Group access to required ports and trusted sources.
- Keep the operating system and container images updated.
- Protect Jenkins with strong authentication and restricted access.
- Treat Docker socket access as privileged host access.
- Do not expose Kubernetes API ports publicly without appropriate security controls.
- Kubernetes Secrets are base64-encoded by default; base64 is not encryption.
- Use RBAC and appropriate secret encryption/access controls.
- Back up important configuration files and Kubernetes manifests.

---

## 📊 Project Status

### Completed / Practiced

- [x] Linux fundamentals and server administration
- [x] AWS EC2 setup
- [x] Git and GitHub
- [x] Docker image build
- [x] Docker container deployment
- [x] Docker Hub push and pull
- [x] Nginx reverse proxy
- [x] Route 53 domain configuration
- [x] SSL / HTTPS
- [x] GitHub Actions Docker build and push
- [x] Jenkins installation and pipeline learning
- [x] Kubernetes K3s installation
- [x] Kubernetes Node Ready
- [x] Pod and Deployment
- [x] ReplicaSet
- [x] Kubernetes self-healing test
- [x] ClusterIP Service
- [x] NodePort Service
- [x] Traefik Ingress
- [x] Website accessible through domain

### Next Learning Topics

- [ ] ConfigMap
- [ ] Kubernetes Secret
- [ ] Persistent Volume and Persistent Volume Claim
- [ ] Horizontal Pod Autoscaler (HPA)
- [ ] Helm
- [ ] Prometheus
- [ ] Grafana
- [ ] Trivy container image scanning
- [ ] Argo CD / GitOps
- [ ] Terraform infrastructure as code

---

## 🎓 DevOps Interview Questions

### 1. What is DevOps?

DevOps is a culture and set of practices that combines development and operations to deliver software faster, reliably, and through automation.

### 2. What is CI/CD?

- **CI – Continuous Integration:** Frequently integrates code changes and validates them through automated builds and tests.
- **CD – Continuous Delivery/Deployment:** Automates the process of preparing or deploying application changes.

### 3. What is Git?

Git is a distributed version-control system used to track source-code changes.

### 4. What is Docker?

Docker is a platform used to package and run applications in containers.

### 5. What is the difference between an image and a container?

An image is the packaged application template. A container is a running instance of that image.

### 6. What is Docker Hub?

Docker Hub is a registry where Docker images can be stored and shared.

### 7. What is Jenkins?

Jenkins is an automation server commonly used to create CI/CD pipelines.

### 8. What is a reverse proxy?

A reverse proxy receives client requests and forwards them to backend servers or applications.

### 9. What is Kubernetes?

Kubernetes is a container-orchestration platform used to deploy, scale, and manage containerized applications.

### 10. What is K3s?

K3s is a lightweight Kubernetes distribution designed for simpler installation and lower resource usage.

---

## ☸️ Kubernetes Interview Questions

### 1. What is a Pod?

A Pod is the smallest deployable unit in Kubernetes. It can contain one or more containers that share networking and storage resources.

### 2. What is a Deployment?

A Deployment manages application Pods and supports scaling, rolling updates, and rollback.

### 3. What is a ReplicaSet?

A ReplicaSet ensures that the specified number of Pod replicas are running.

### 4. What is self-healing in Kubernetes?

Self-healing means Kubernetes replaces failed or deleted Pods when they are managed by a controller such as a Deployment.

### 5. What is a Service?

A Service provides a stable network endpoint for accessing a group of Pods.

### 6. What is the difference between ClusterIP and NodePort?

- **ClusterIP:** Exposes a Service internally within the cluster.
- **NodePort:** Exposes a Service through a port on the Kubernetes nodes.

### 7. What is Ingress?

Ingress defines HTTP/HTTPS routing rules that direct traffic to Kubernetes Services. An Ingress controller, such as Traefik, implements those rules.

### 8. What is ConfigMap?

ConfigMap stores non-sensitive configuration data such as environment variables or application settings.

### 9. What is Secret?

Secret stores sensitive configuration data such as credentials or tokens. Access must be controlled carefully.

### 10. What is HPA?

Horizontal Pod Autoscaler adjusts the number of Pod replicas based on configured metrics, such as CPU or memory utilization.

### 11. What is a namespace?

A namespace provides a logical separation of resources within a Kubernetes cluster.

### 12. How do you troubleshoot a Pod?

```bash
kubectl get pods

kubectl describe pod <POD-NAME>

kubectl logs <POD-NAME>

kubectl get events --sort-by=.metadata.creationTimestamp
```

---

## 📝 Useful Commands Cheat Sheet

### Linux

```bash
pwd
ls -la
cd
mkdir
touch
cat
nano
cp
mv
rm
df -h
free -h
top
```

### Git

```bash
git status
git add .
git commit -m "message"
git pull origin main --rebase
git push origin main
```

### Docker

```bash
docker images
docker ps
docker ps -a
docker build -t app:v1 .
docker run -d -p 8080:80 app:v1
docker logs <CONTAINER>
docker stop <CONTAINER>
```

### Kubernetes

```bash
kubectl get nodes
kubectl get pods -o wide
kubectl get deployments
kubectl get replicasets
kubectl get services
kubectl get ingress
kubectl describe pod <POD>
kubectl logs <POD>
kubectl scale deployment varun-cabs --replicas=3
kubectl rollout status deployment varun-cabs
```

---

## 👨‍💻 Author

**Santhosh Kumar**

DevOps Learning Project – Varun Cabs Bangalore

This project is built as a hands-on learning journey to understand Linux, AWS, Docker, CI/CD, and Kubernetes by deploying and managing a real website.

---

⭐ If you find this project useful, feel free to explore the repository and learn from the implementation.

**Learning by doing. Automating step by step. Building real DevOps skills.**
