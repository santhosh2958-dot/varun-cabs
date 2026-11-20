# Varun Cabs - End-to-End DevOps Project

## Project Overview

This project demonstrates the deployment of a production-ready static website (**Varun Cabs Bangalore**) using modern DevOps tools and practices.

The objective was to learn and implement:

- Linux Administration
- Git & GitHub
- Docker
- Docker Hub
- AWS EC2
- Route53 DNS
- Nginx Reverse Proxy
- SSL using Let's Encrypt
- GitHub Actions
- Jenkins CI Pipeline

---

# Final Website

```text
https://varun-cabs.site
```

---

# Project Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ▼
Docker Hub
    │
    ▼
AWS EC2 Instance
    │
    ▼
Nginx Reverse Proxy
    │
    ▼
Docker Container
    │
    ▼
Varun Cabs Website
```

---

# Infrastructure Used

## AWS Services

```text
EC2
Route53
Security Groups
```

## DevOps Tools

```text
Git
GitHub
Docker
Docker Hub
GitHub Actions
Jenkins
Nginx
Certbot
```

---

# Phase 1: Launch EC2 Instance

## Objective

Create a Linux server for application deployment.

### Instance Type

```text
Ubuntu EC2
```

### Open Ports

```text
22  SSH
80  HTTP
443 HTTPS
9090 Jenkins
50000 Jenkins Agent Communication
```

### Connect to Server

```bash
ssh -i key.pem ubuntu@PUBLIC_IP
```

---

# Phase 2: Linux Setup

Update package repository

```bash
sudo apt update
```

Explanation:

```text
Downloads latest package metadata from Ubuntu repositories.
```

---

# Phase 3: Install Docker

Install Docker

```bash
sudo apt install docker.io -y
```

Start Docker

```bash
sudo systemctl start docker
```

Enable Docker

```bash
sudo systemctl enable docker
```

Verify Docker

```bash
docker --version
```

Test Docker

```bash
docker run hello-world
```

Purpose

```text
Confirms Docker Engine is functioning correctly.
```

---

# Phase 4: Create Website

Project Directory

```bash
mkdir varun-cabs

cd varun-cabs
```

Create Website File

```bash
vi index.html
```

Contains:

```text
Varun Cabs Bangalore Website HTML Code
```

---

# Phase 5: Create Dockerfile

Create Dockerfile

```bash
vi Dockerfile
```

Content

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

Explanation

```text
FROM
→ Uses official nginx image.

COPY
→ Copies website into nginx web root.

EXPOSE
→ Opens port 80.
```

---

# Phase 6: Build Docker Image

Build image

```bash
docker build -t varun-cabs:v1 .
```

Explanation

```text
docker build
    Creates image

-t
    Tag image

varun-cabs:v1
    Image Name : Version

.
    Current directory
```

Verify

```bash
docker images
```

---

# Phase 7: Run Docker Container

Run Application

```bash
docker run -d \
-p 80:80 \
--name varun-cabs-app \
varun-cabs:v1
```

Verify

```bash
docker ps
```

Test

```bash
curl localhost
```

---

# Container Architecture

```text
Docker Image
       │
       ▼
Docker Container
       │
       ▼
Nginx
       │
       ▼
Static Website
```

---

# Phase 8: GitHub Integration

Initialize Repository

```bash
git init
```

Add Files

```bash
git add .
```

Commit

```bash
git commit -m "Initial Project"
```

Connect GitHub

```bash
git remote add origin REPOSITORY_URL
```

Push

```bash
git push origin main
```

Purpose

```text
Version Control
Source Code Management
Collaboration
```

---

# Phase 9: Route53 Domain Mapping

Domain

```text
varun-cabs.site
```

Public IP

```text
13.203.192.176
```

Create A Record

```text
Name:
varun-cabs.site

Type:
A

Value:
13.203.192.176
```

Create WWW Record

```text
Name:
www

Type:
A

Value:
13.203.192.176
```

Purpose

```text
Maps domain to EC2 server.
```

---

# Phase 10: Install Nginx

Install

```bash
sudo apt install nginx -y
```

Start

```bash
sudo systemctl start nginx
```

Check Status

```bash
sudo systemctl status nginx
```

---

# Phase 11: Enable HTTPS SSL

Install Certbot

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Generate Certificate

```bash
sudo certbot --nginx
```

Domain

```text
varun-cabs.site
www.varun-cabs.site
```

Result

```text
HTTPS Enabled
Automatic Renewal Enabled
```

---

# SSL Architecture

```text
User
  │
  ▼
HTTPS
  │
  ▼
Nginx
  │
  ▼
Docker Container
  │
  ▼
Website
```

---

# Phase 12: Docker + Nginx Reverse Proxy

Problem

```text
Docker occupied port 80
Nginx required port 80
```

Solution

Container moved to:

```text
8080
```

Run Container

```bash
docker run -d \
--name varun-cabs-app \
-p 8080:80 \
varun-cabs:v2
```

Nginx Reverse Proxy

```text
Internet
     │
     ▼
Nginx :80/:443
     │
     ▼
localhost:8080
     │
     ▼
Docker Container
```

Benefits

```text
SSL termination
Security
Production Architecture
Load Balancing Ready
```

---

# Phase 13: Docker Hub

Login

```bash
docker login
```

Tag Image

```bash
docker tag varun-cabs:v2 santhosh2958/varun-cabs:v2

docker tag varun-cabs:v2 santhosh2958/varun-cabs:latest
```

Push

```bash
docker push santhosh2958/varun-cabs:v2

docker push santhosh2958/varun-cabs:latest
```

Result

```text
Image stored in Docker Hub
```

Purpose

```text
Central Image Repository
Backup Images
Easy Deployment
```

---

# Phase 14: GitHub Actions

Objective

```text
Automate Docker Build Process
```

Workflow

```yaml
name: Docker Build and Push
```

Flow

```text
Git Push
   │
   ▼
GitHub Actions
   │
   ▼
Build Docker Image
   │
   ▼
Push Image
```

CI Concept Learned

```text
Continuous Integration
```

---

# Phase 15: Jenkins Installation

Create Volume

```bash
docker volume create jenkins_home
```

Run Jenkins

```bash
docker run -d \
--name jenkins \
-p 9090:8080 \
-p 50000:50000 \
-v jenkins_home:/var/jenkins_home \
jenkins/jenkins:lts
```

Access

```text
http://SERVER_IP:9090
```

---

# Phase 16: Jenkins Plugins

Installed

```text
Git Plugin
Pipeline Plugin
Docker Plugin
Docker Workflow Plugin
SSH Agent
```

Purpose

```text
Enable CI/CD Features
Git Integration
Docker Integration
Pipeline Automation
```

---

# Phase 17: Jenkins Pipeline

## First Pipeline

```groovy
pipeline {

    agent any

    stages {

        stage('Test') {
            steps {
                echo 'Jenkins Pipeline Works!'
            }
        }
    }
}
```

Output

```text
Jenkins Pipeline Works!
Finished: SUCCESS
```

---

# Phase 18: GitHub Integration with Jenkins

Pipeline

```groovy
checkout([
    $class: 'GitSCM',
    branches: [[name: '*/main']],
    userRemoteConfigs: [[
        url: 'https://github.com/santhosh2958-dot/varun-cabs.git'
    ]]
])
```

Result

```text
Repository Cloned Successfully
```

Output

```text
Dockerfile
README.md
index.html
.github
```

---

# First Real CI Pipeline

```text
GitHub Repository
        │
        ▼
Jenkins
        │
        ▼
Clone Repository
        │
        ▼
Show Files
        │
        ▼
SUCCESS
```

---

# Issue Encountered

Docker Build Failure

Error

```text
docker: not found
```

Reason

```text
Docker installed on EC2 Host

Jenkins running inside separate container

Docker CLI unavailable inside Jenkins container
```

Learning

```text
Host Docker Engine
       ≠
Jenkins Container
```

---

# Current Architecture

```text
Developer
     │
     ▼
GitHub
     │
     ▼
Jenkins
     │
     ▼
Git Checkout
     │
     ▼
Workspace
     │
     ▼
Docker Build (Pending)
```

---

# Major Concepts Learned

## Linux

```bash
ls
cd
pwd
cat
vi
systemctl
```

---

## Git

```bash
git init
git add .
git commit
git push
git pull
```

---

## Docker

```bash
docker build
docker run
docker images
docker ps
docker stop
docker rm
docker push
```

---

## Jenkins

```text
Pipeline
Stage
Step
Workspace
Node
Agent
Build History
Console Output
```

---

# Flowchart

```text
Developer
   │
   ▼
Git Push
   │
   ▼
GitHub Repository
   │
   ▼
GitHub Actions
   │
   ▼
Docker Hub
   │
   ▼
Jenkins
   │
   ▼
GitHub Checkout
   │
   ▼
Docker Build
   │
   ▼
Docker Hub Push
   │
   ▼
Kubernetes (Future)
```

---

# Project Status

```text
✅ Linux
✅ AWS EC2
✅ Git
✅ GitHub
✅ Docker
✅ Docker Image
✅ Docker Container
✅ Docker Hub
✅ Route53
✅ Domain
✅ Nginx
✅ SSL Certificate
✅ GitHub Actions
✅ Jenkins Installation
✅ Jenkins Plugins
✅ Jenkins Pipeline
✅ Jenkins GitHub Checkout

🟡 Jenkins Docker Integration (In Progress)

Future:
🔜 SonarQube
🔜 Trivy
🔜 Kubernetes
🔜 Ingress
🔜 Monitoring
```

# Conclusion

Successfully built and deployed a production website using AWS EC2, Docker, Docker Hub, Route53, Nginx, SSL, GitHub Actions, and Jenkins. Developed a functional CI pipeline where Jenkins automatically fetches source code from GitHub and prepares it for automated builds.
