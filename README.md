# 🚖 Varun Cabs Bangalore – End-to-End DevOps Project

## 📌 Project Overview

**Varun Cabs Bangalore** is an end-to-end DevOps learning project that demonstrates how to build, containerize, deploy, automate, and manage a website using modern DevOps and cloud technologies.

The project started with a simple static website and gradually evolved into a practical DevOps implementation using AWS, Linux, Docker, GitHub, Jenkins, and Kubernetes.

The main objective is to understand the complete application lifecycle:

- Source code development
- Version control
- Containerization
- Continuous Integration and Continuous Deployment
- Cloud infrastructure
- Web server and reverse proxy configuration
- SSL certificate management
- Kubernetes application deployment
- Application availability and troubleshooting

This project is designed for hands-on learning and demonstrates how different DevOps tools work together in a real-world-style deployment.

---

## 🌐 Live Project Links

| Resource | Link |
|---|---|
| Website | https://varun-cabs.site |
| Website with www | https://www.varun-cabs.site |
| GitHub Repository | https://github.com/santhosh2958-dot/varun-cabs |
| Docker Hub Repository | https://hub.docker.com/r/santhosh2958/varun-cabs |

---

## 🎯 Project Objectives

The major objectives of this project are:

1. Host a website on AWS EC2.
2. Learn Linux server administration.
3. Build and run Docker containers.
4. Store application images in Docker Hub.
5. Manage source code using Git and GitHub.
6. Configure a custom domain using Route 53.
7. Configure Nginx as a reverse proxy.
8. Enable HTTPS using Let's Encrypt and Certbot.
9. Automate Docker builds using GitHub Actions.
10. Automate CI/CD using Jenkins.
11. Deploy the application on Kubernetes.
12. Configure Kubernetes Services and Ingress.
13. Learn application troubleshooting and infrastructure management.
14. Extend the project with DevSecOps, monitoring, GitOps, and Infrastructure as Code.

---

# 🛠️ Technologies Used

## Cloud Infrastructure

- AWS EC2
- AWS Route 53
- AWS Security Groups

## Operating System

- Ubuntu Linux

## Version Control

- Git
- GitHub

## Containerization

- Docker
- Docker Hub

## Web Server and Reverse Proxy

- Nginx

## SSL / HTTPS

- Let's Encrypt
- Certbot

## CI/CD

- GitHub Actions
- Jenkins

## Container Orchestration

- Kubernetes
- K3s
- kubectl

## Ingress

- Traefik

## Future Technologies

- SonarQube
- Trivy
- Prometheus
- Grafana
- ArgoCD
- Terraform

---

# 🏗️ High-Level DevOps Architecture

The project uses GitHub for source code management, CI/CD tools for automation, Docker for containerization, and Kubernetes for application orchestration.

```text
                    Developer
                       |
                       v
                GitHub Repository
                       |
          +------------+------------+
          |                         |
          v                         v
    GitHub Actions               Jenkins
          |                         |
          v                         v
     Docker Build              Docker Build
          |                         |
          v                         v
     Docker Hub <-------------------+
          |
          v
      Kubernetes
          |
          v
       Ingress
          |
          v
   Varun Cabs Website
```

## Application Traffic Flow

```text
                 Customer Browser
                        |
                        v
                 varun-cabs.site
                        |
                        v
                   Route 53
                        |
                        v
                    AWS EC2
                        |
                        v
                Nginx / Ingress
                        |
                        v
                 Kubernetes Service
                        |
                        v
                  Kubernetes Pods
                        |
                        v
                 Varun Cabs Website
```

> The project has used Docker containers with Nginx reverse proxy and has also been deployed on K3s Kubernetes. The final production traffic path depends on the active Nginx and Ingress configuration.

---

# ☁️ Phase 1 – AWS EC2 Setup

## Objective

Create a cloud-based Linux server to host the website and run DevOps tools.

## EC2 Configuration

| Configuration | Details |
|---|---|
| Cloud Provider | AWS |
| Service | EC2 |
| Operating System | Ubuntu Linux |
| Instance Type | t3.small for the Kubernetes learning server |
| Region | ap-south-1 |
| Application | Varun Cabs Bangalore |

## Security Group Configuration

| Port | Purpose |
|---|---|
| 22 | SSH access |
| 80 | HTTP |
| 443 | HTTPS |
| 9090 | Jenkins web interface |
| 50000 | Jenkins agent communication |

Security groups control which network traffic can reach the EC2 instance.

### Important Security Note

For better security:

- Restrict SSH port 22 to your own IP address.
- Do not expose Jenkins publicly without access controls.
- Use HTTPS for Jenkins when possible.
- Do not expose the Docker daemon through an unauthenticated TCP port.
- Open only the ports required by the application.

---

# 🐧 Phase 2 – Linux Administration

Linux is the foundation of cloud infrastructure and DevOps.

The project uses Ubuntu Linux for installing software, managing services, running containers, and troubleshooting the server.

## Linux Commands Learned

### Basic Navigation

```bash
pwd
ls
ls -la
cd
```

| Command | Explanation |
|---|---|
| `pwd` | Displays the current working directory |
| `ls` | Lists files and directories |
| `ls -la` | Lists all files, including hidden files |
| `cd` | Changes the current directory |

### File Management

```bash
mkdir
touch
cp
mv
rm
cat
nano
vim
```

### Searching and Filtering

```bash
grep
find
```

### System Monitoring

```bash
free -h
df -h
top
ps aux
uptime
```

| Command | Explanation |
|---|---|
| `free -h` | Displays memory usage |
| `df -h` | Displays disk usage |
| `top` | Monitors running processes |
| `ps aux` | Lists running processes |
| `uptime` | Displays system uptime and load |

### Service Management

```bash
sudo systemctl status docker
sudo systemctl start docker
sudo systemctl stop docker
sudo systemctl restart docker
sudo systemctl enable docker
```

### Key Learning

Linux commands are essential for:

- Server administration
- Installing software
- Managing services
- Checking logs
- Monitoring system resources
- Troubleshooting application issues

---

# 🐳 Phase 3 – Docker Containerization

## Objective

Package the website into a Docker image and run it inside a container.

Docker allows an application to run consistently across different environments.

## Dockerfile

The project uses Nginx as the base image to serve the static website.

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

## Dockerfile Explanation

### `FROM nginx:latest`

Uses the official Nginx image as the base image.

### `COPY index.html /usr/share/nginx/html/index.html`

Copies the website HTML file into the default Nginx web directory.

### `EXPOSE 80`

Documents that the container serves HTTP traffic on port 80.

## Build Docker Image

```bash
docker build -t varun-cabs:v1 .
```

This command builds a Docker image from the Dockerfile in the current directory.

## Run Docker Container

```bash
docker run -d \
  --name varun-cabs-app \
  -p 8080:80 \
  varun-cabs:v2
```

### Port Mapping Explanation

```text
EC2 Host Port 8080
        |
        v
Container Port 80
        |
        v
Nginx inside Docker
        |
        v
Website HTML
```

The website container listens on port 80 internally, while the EC2 host exposes it on port 8080.

## Docker Commands Learned

```bash
docker images
docker ps
docker ps -a
docker pull nginx
docker build -t varun-cabs:v2 .
docker run -d --name varun-cabs-app -p 8080:80 varun-cabs:v2
docker stop varun-cabs-app
docker start varun-cabs-app
docker logs varun-cabs-app
docker exec -it varun-cabs-app bash
docker rm varun-cabs-app
docker rmi varun-cabs:v2
```

## Docker Concepts Learned

- Docker Image
- Docker Container
- Dockerfile
- Image tagging
- Port mapping
- Container lifecycle
- Docker networking
- Container logs
- Container restart policies

---

# 🧾 Phase 4 – Git and GitHub

## Objective

Manage source code using version control and store the project in GitHub.

## Initialize Git Repository

```bash
git init
```

## Add Files

```bash
git add .
```

## Commit Changes

```bash
git commit -m "Initial commit"
```

## Configure Remote Repository

```bash
git remote add origin git@github.com:santhosh2958-dot/varun-cabs.git
```

## Push Code to GitHub

```bash
git push -u origin main
```

## Git Commands Learned

```bash
git status
git add .
git commit -m "Update website"
git pull origin main --rebase
git push origin main
git log --oneline
git branch
git checkout main
```

## Git Workflow

```text
Developer
   |
   v
Modify Files
   |
   v
git add
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

## Key Learning

Git tracks changes in source code, while GitHub hosts the repository remotely and supports collaboration.

---

# 📦 Phase 5 – Docker Hub

## Objective

Store Docker images in a centralized container registry.

Docker Hub allows images to be downloaded and deployed on different servers.

## Login to Docker Hub

```bash
docker login
```

## Tag Docker Image

```bash
docker tag varun-cabs:v2 santhosh2958/varun-cabs:v2
```

## Push Docker Image

```bash
docker push santhosh2958/varun-cabs:v2
```

## Push Latest Tag

```bash
docker tag varun-cabs:v2 santhosh2958/varun-cabs:latest

docker push santhosh2958/varun-cabs:latest
```

## Pull Image

```bash
docker pull santhosh2958/varun-cabs:v2
```

## Benefits of Docker Hub

- Central image storage
- Image versioning
- Easy application deployment
- Image sharing
- Integration with CI/CD pipelines

---

# 🌎 Phase 6 – Route 53 DNS

## Objective

Connect the custom domain name to the AWS-hosted application.

## Domain

```text
varun-cabs.site
```

## DNS Configuration

Route 53 is used to manage DNS records for the domain.

An A record maps the domain name to an IPv4 address.

```text
varun-cabs.site
       |
       v
Route 53 A Record
       |
       v
EC2 Public IPv4 Address
```

## DNS Concepts Learned

- Domain name
- DNS resolution
- A record
- DNS propagation
- Public IPv4 address
- Custom domain configuration

---

# 🌐 Phase 7 – Nginx Reverse Proxy

## Objective

Configure Nginx to receive external traffic and forward requests to the Docker application.

## Problem

The Docker website was initially using host port 80.

Nginx also requires port 80 to receive HTTP traffic.

This caused a port conflict.

## Solution

The application container was moved to host port 8080.

```text
Nginx
Host Port 80 / 443
       |
       v
Reverse Proxy
       |
       v
Docker Application
Host Port 8080
       |
       v
Container Port 80
```

## Reverse Proxy Configuration

Nginx forwards incoming requests to the application running on localhost port 8080.

Example configuration:

```nginx
server {
    listen 80;
    server_name varun-cabs.site www.varun-cabs.site;

    location / {
        proxy_pass http://127.0.0.1:8080;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

The actual configuration may also include HTTPS and Certbot-managed sections.

## Nginx Commands

```bash
sudo nginx -t
sudo systemctl status nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
```

---

# 🔒 Phase 8 – SSL / HTTPS

## Objective

Secure the website using HTTPS.

## Tools Used

- Let's Encrypt
- Certbot

## Install Certbot

```bash
sudo apt update

sudo apt install certbot python3-certbot-nginx -y
```

## Obtain SSL Certificate

```bash
sudo certbot --nginx
```

Certbot configures the certificate and integrates it with Nginx.

## HTTPS Traffic Flow

```text
Browser
   |
   v
HTTPS Port 443
   |
   v
Nginx SSL
   |
   v
Docker Application
```

## SSL Concepts Learned

- HTTPS
- SSL/TLS certificates
- Certificate authority
- Certificate renewal
- Secure web traffic

## Verify Certificate Renewal

```bash
sudo certbot renew --dry-run
```

---

# ⚙️ Phase 9 – GitHub Actions

## Objective

Automate Docker image building and publishing when code is pushed to GitHub.

## Workflow

```text
Developer
   |
   v
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
Docker Hub Push
```

## GitHub Actions Responsibilities

- Detect source code changes
- Build Docker image
- Authenticate with Docker Hub
- Push image to Docker Hub
- Automate repetitive build tasks

## GitHub Secrets

Sensitive information such as Docker Hub credentials should be stored in GitHub Actions secrets.

Example secret names:

```text
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

Secrets should never be hardcoded inside workflow files.

---

# 🤖 Phase 10 – Jenkins Installation

## Objective

Install Jenkins to automate CI/CD pipelines.

Jenkins is an automation server used to build, test, and deploy applications.

## Jenkins Container

Jenkins was deployed using Docker with persistent storage.

Example:

```bash
docker run -d \
  --name jenkins \
  -p 9090:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

## Port Explanation

| Port | Purpose |
|---|---|
| 9090 | Jenkins web interface on EC2 |
| 8080 | Jenkins web interface inside container |
| 50000 | Jenkins agent communication |

## Jenkins Access

```text
http://EC2-PUBLIC-IP:9090
```

## Jenkins Concepts Learned

- Jenkins installation
- Jenkins dashboard
- Jenkins plugins
- Jenkins jobs
- Jenkins pipelines
- Jenkins workspace
- Jenkins credentials

---

# 🔗 Phase 11 – Jenkins GitHub Integration

## Objective

Connect Jenkins to the GitHub repository and retrieve application source code.

## Pipeline Flow

```text
GitHub Repository
        |
        v
      Jenkins
        |
        v
   Git Checkout
        |
        v
   Jenkins Workspace
```

## Result

- Repository cloned successfully
- Source code fetched
- Jenkins workspace created
- Pipeline executed successfully

## Concepts Learned

- Git repository integration
- Jenkins checkout
- Pipeline stages
- Workspace management

---

# 🏭 Phase 12 – Jenkins Docker Build

## Objective

Allow Jenkins to build Docker images automatically.

## Problem 1 – Docker CLI Not Found

Error:

```text
docker: not found
```

### Cause

The Jenkins container did not have the Docker CLI installed.

### Solution

A custom Jenkins image was created with the Docker CLI installed.

## Problem 2 – Docker Socket Permission Denied

Error:

```text
permission denied while trying to connect to the Docker daemon socket
```

### Cause

Jenkins could not access the Docker daemon running on the EC2 host.

### Solution

The Docker socket was mounted into the Jenkins container:

```bash
-v /var/run/docker.sock:/var/run/docker.sock
```

The custom Jenkins image and Docker socket integration allowed Jenkins to execute Docker commands.

## Jenkins Docker Build Flow

```text
GitHub
   |
   v
Jenkins
   |
   v
Checkout Source
   |
   v
Docker Build
   |
   v
Docker Image
```

## Important Security Note

Mounting the Docker socket gives Jenkins significant control over the Docker host.

This is acceptable for a controlled learning environment, but production environments should use stronger isolation and access controls.

---

# 🚀 Phase 13 – Jenkins Docker Hub Push

## Objective

Automate building and publishing Docker images through Jenkins.

## CI/CD Flow

```text
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
Docker Hub Login
   |
   v
Docker Hub Push
```

## Result

- Docker image built successfully
- Docker Hub authentication configured
- Docker image pushed successfully
- Jenkins pipeline completed

## Docker Hub Repository

```text
santhosh2958/varun-cabs
```

## CI/CD Concepts Learned

- Continuous Integration
- Continuous Delivery
- Pipeline stages
- Docker image tagging
- Registry authentication
- Jenkins credentials
- Automated image publishing

---

# ☸️ Phase 14 – Kubernetes (K3s)

## Objective

Deploy and manage the Varun Cabs application using Kubernetes.

Kubernetes is a container orchestration platform that helps manage containerized applications.

K3s is a lightweight Kubernetes distribution suitable for learning and resource-constrained environments.

## K3s Installation

```bash
curl -sfL https://get.k3s.io | sh -
```

## Verify K3s

```bash
sudo systemctl status k3s
```

## Verify Kubernetes Node

```bash
kubectl get nodes
```

## Kubernetes Architecture

```text
Kubernetes Cluster
        |
        v
      Node
        |
        v
      Pod
        |
        v
    Container
        |
        v
  Varun Cabs Website
```

---

## 🔹 Kubernetes Pod

A Pod is the smallest deployable unit in Kubernetes.

A Pod contains one or more containers that share networking and storage resources.

## Create a Pod

```bash
kubectl run varun-cabs-pod \
  --image=santhosh2958/varun-cabs:v2
```

## Check Pods

```bash
kubectl get pods
```

## Describe Pod

```bash
kubectl describe pod varun-cabs-pod
```

## Pod Concepts Learned

- Pod creation
- Container execution
- Pod status
- Pod IP address
- Pod lifecycle

---

## 🔹 Kubernetes Deployment

A Deployment manages application Pods and maintains the desired number of replicas.

## Create Deployment

```bash
kubectl create deployment varun-cabs \
  --image=santhosh2958/varun-cabs:v2 \
  --replicas=2
```

## Check Deployment

```bash
kubectl get deployments
```

## Check ReplicaSets

```bash
kubectl get replicasets
```

## Check Pods

```bash
kubectl get pods -o wide
```

## Deployment Benefits

- Replica management
- Self-healing
- Rolling updates
- Application scaling
- Rollback support

---

## 🔹 Kubernetes ReplicaSet

A ReplicaSet ensures that the desired number of Pod replicas are running.

For example:

```text
Deployment
    |
    v
ReplicaSet
    |
    +---- Pod 1
    |
    +---- Pod 2
```

## Self-Healing Test

Delete one Pod:

```bash
kubectl delete pod <pod-name>
```

Check the Pods:

```bash
kubectl get pods
```

Kubernetes automatically creates a replacement Pod to maintain the desired replica count.

---

# 🔹 Phase 15 – Kubernetes Services

## Objective

Provide stable network access to application Pods.

Pods can be replaced, and their IP addresses may change. A Kubernetes Service provides a stable endpoint for accessing a group of Pods.

## ClusterIP

ClusterIP exposes the application inside the Kubernetes cluster.

```text
Internal Application
        |
        v
    ClusterIP
        |
        v
       Pods
```

## NodePort

NodePort exposes a Service through a port on the Kubernetes node.

Example:

```bash
kubectl expose deployment varun-cabs \
  --type=NodePort \
  --port=80
```

## Check Services

```bash
kubectl get services
```

## Service Types

| Service | Purpose |
|---|---|
| ClusterIP | Internal cluster communication |
| NodePort | Exposes a Service through a node port |
| LoadBalancer | Integrates with a supported external load balancer |

---

# 🌐 Phase 16 – Kubernetes Ingress and Traefik

## Objective

Route external HTTP and HTTPS traffic to Kubernetes Services using domain names.

Traefik is the Ingress Controller used in the K3s learning environment.

## Ingress Architecture

```text
Internet
   |
   v
Domain Name
   |
   v
Traefik Ingress Controller
   |
   v
Ingress Resource
   |
   v
Kubernetes Service
   |
   v
Application Pods
```

## Ingress Responsibilities

- Host-based routing
- Path-based routing
- HTTP traffic routing
- HTTPS integration
- Connecting external traffic to Kubernetes Services

## Verify Traefik

```bash
kubectl get pods -n kube-system
```

## Check Ingress Resources

```bash
kubectl get ingress
```

## Check Services

```bash
kubectl get services
```

## Check Application Pods

```bash
kubectl get pods -o wide
```

## Current Result

The Varun Cabs website has been deployed on K3s, and the domain names have been verified as accessible:

- https://varun-cabs.site
- https://www.varun-cabs.site

The active DNS, Nginx, Ingress, and TLS configuration should be verified before making further traffic-routing changes.

---

# 🔄 Phase 17 – Docker Container Automatic Restart

## Problem

After stopping or restarting the EC2 instance, Docker containers were not automatically running.

This caused the website to become unavailable and resulted in a 502 Bad Gateway error from Nginx.

## Cause

The containers did not have an appropriate restart policy.

## Solution

Configure Docker containers to restart automatically:

```bash
docker update --restart unless-stopped varun-cabs-app

docker update --restart unless-stopped jenkins
```

Enable Docker and Nginx at system startup:

```bash
sudo systemctl enable docker

sudo systemctl enable nginx
```

Start the containers:

```bash
docker start varun-cabs-app

docker start jenkins
```

## Verify Restart Policy

```bash
docker inspect -f '{{.HostConfig.RestartPolicy.Name}}' varun-cabs-app
```

Expected:

```text
unless-stopped
```

## Key Learning

Docker restart policies help keep containers running after Docker daemon or EC2 restarts.

---

# 🛠️ Phase 18 – Troubleshooting and Problems Solved

## Problem 1 – 502 Bad Gateway

### Cause

The Nginx reverse proxy was running, but the upstream Docker application container was stopped.

### Resolution

```bash
docker ps -a
docker start varun-cabs-app
```

Check the application:

```bash
curl -I http://127.0.0.1:8080
```

Check Nginx:

```bash
sudo nginx -t
sudo systemctl status nginx
```

---

## Problem 2 – Docker Containers Not Running After EC2 Restart

### Cause

Docker containers did not have automatic restart policies.

### Resolution

```bash
docker update --restart unless-stopped varun-cabs-app

docker update --restart unless-stopped jenkins
```

Enable Docker:

```bash
sudo systemctl enable docker
```

---

## Problem 3 – Docker Command Not Found Inside Jenkins

### Cause

The Jenkins container did not include Docker CLI.

### Resolution

Create a custom Jenkins image with Docker CLI installed.

---

## Problem 4 – Docker Socket Permission Denied

### Cause

Jenkins could not access the Docker daemon socket.

### Resolution

Mount the Docker socket:

```bash
-v /var/run/docker.sock:/var/run/docker.sock
```

Use appropriate permissions and protect Jenkins because Docker socket access is highly privileged.

---

## Problem 5 – Git Push Rejected

### Error

```text
! [rejected] main -> main (fetch first)
```

### Cause

The remote GitHub repository contained commits that were not present in the local repository.

### Safe Resolution

```bash
git pull origin main --rebase

git push origin main
```

If conflicts occur, resolve them before continuing the rebase.

---

# 📊 Current Project Status

## Completed

- [x] Linux Administration
- [x] AWS EC2
- [x] Git
- [x] GitHub
- [x] Docker
- [x] Docker Hub
- [x] Route 53
- [x] Nginx Reverse Proxy
- [x] SSL / HTTPS
- [x] GitHub Actions
- [x] Jenkins
- [x] Jenkins GitHub Integration
- [x] Jenkins Docker Build
- [x] Jenkins Docker Hub Push
- [x] Kubernetes K3s
- [x] Pods
- [x] Deployments
- [x] ReplicaSets
- [x] Self-Healing
- [x] Kubernetes Services
- [x] ClusterIP
- [x] NodePort
- [x] Traefik Ingress
- [x] Website accessible through domain

---

# 🚀 Future Enhancements

The following technologies are planned for the next stages of the project.

## Phase 19 – SonarQube (Code Quality)

SonarQube will analyze source code and identify:

- Bugs
- Code smells
- Security issues
- Maintainability problems

Planned implementation:

1. Install SonarQube.
2. Create a Varun Cabs project.
3. Generate a SonarQube token.
4. Configure Jenkins credentials.
5. Add SonarQube analysis to the Jenkins pipeline.
6. Review the code quality dashboard.

## Phase 20 – Trivy (Container Security)

Trivy will scan Docker images for vulnerabilities.

Planned implementation:

1. Install Trivy.
2. Scan the Varun Cabs Docker image.
3. Review vulnerability severity.
4. Generate a scan report.
5. Integrate Trivy into Jenkins.
6. Add a security gate to the CI/CD pipeline.

Example:

```bash
trivy image santhosh2958/varun-cabs:v2
```

## Phase 21 – Kubernetes ConfigMaps and Secrets

### ConfigMap

Stores non-sensitive configuration data.

Examples:

- Application settings
- Environment variables
- Configuration files

### Secret

Stores sensitive configuration data.

Examples:

- Passwords
- API tokens
- Credentials

Planned learning:

- Create ConfigMaps
- Create Secrets
- Mount configuration into Pods
- Use environment variables
- Understand Kubernetes Secret security

## Phase 22 – Persistent Volumes

Learn how Kubernetes manages persistent storage.

Topics:

- PersistentVolume
- PersistentVolumeClaim
- StorageClass
- Volume mounting
- Persistent application data

## Phase 23 – Horizontal Pod Autoscaler

HPA automatically scales application Pods based on resource metrics.

Example:

```bash
kubectl autoscale deployment varun-cabs \
  --cpu-percent=50 \
  --min=2 \
  --max=5
```

Planned learning:

- Install metrics-server if required
- Configure resource requests and limits
- Configure HPA
- Test automatic scaling

## Phase 24 – Monitoring with Prometheus and Grafana

### Prometheus

Collects metrics from applications and infrastructure.

### Grafana

Displays metrics using dashboards and visualizations.

Planned monitoring:

- EC2 CPU usage
- Memory usage
- Disk usage
- Kubernetes node health
- Pod health
- Application availability
- Container resource usage

## Phase 25 – GitOps with ArgoCD

ArgoCD will help automate Kubernetes deployments using GitOps principles.

Planned workflow:

```text
GitHub Repository
       |
       v
Kubernetes YAML Files
       |
       v
     ArgoCD
       |
       v
Kubernetes Cluster
       |
       v
Varun Cabs Application
```

## Phase 26 – Infrastructure as Code with Terraform

Terraform will be used to automate AWS infrastructure creation.

Planned resources:

- EC2
- Security Groups
- VPC
- Subnets
- Route Tables
- IAM resources
- DNS configuration

Terraform will help manage infrastructure using reusable configuration files.

---

# 🎓 Learning Outcomes

This project provided hands-on experience with:

- Linux server administration
- AWS cloud infrastructure
- Git and GitHub
- Docker containerization
- Docker Hub image management
- Nginx reverse proxy
- SSL certificate configuration
- GitHub Actions
- Jenkins CI/CD
- Kubernetes orchestration
- K3s cluster management
- Kubernetes Services
- Ingress routing
- Application troubleshooting
- Container restart policies
- Cloud deployment and operations

---

# 📚 Useful Commands Reference

## Docker

```bash
docker ps
docker ps -a
docker images
docker logs varun-cabs-app
docker restart varun-cabs-app
docker inspect varun-cabs-app
docker system df
```

## Git

```bash
git status
git add .
git commit -m "Update project"
git pull origin main --rebase
git push origin main
```

## Linux

```bash
free -h
df -h
top
ps aux
uptime
```

## Nginx

```bash
sudo nginx -t
sudo systemctl status nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
```

## Kubernetes

```bash
kubectl get nodes
kubectl get pods
kubectl get deployments
kubectl get replicasets
kubectl get services
kubectl get ingress
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl delete pod <pod-name>
```

---

# 👨‍💻 Author

**Santhosh Kumar**

Project: Varun Cabs Bangalore  
Project Type: End-to-End DevOps and Kubernetes Learning Project

Website: https://varun-cabs.site

GitHub: https://github.com/santhosh2958-dot/varun-cabs

Docker Hub: https://hub.docker.com/r/santhosh2958/varun-cabs

---

## ⭐ Project Summary

Varun Cabs Bangalore is a practical DevOps learning project demonstrating how a static website can be hosted on AWS, containerized using Docker, automated using CI/CD pipelines, and deployed using Kubernetes.

The project continues to evolve with DevSecOps, monitoring, GitOps, and Infrastructure as Code technologies.

**Learning by building. Building by automating. Automating for reliability.** 🚀
