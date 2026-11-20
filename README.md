# Varun Cabs - End to End DevOps Project

## Project Overview

This project demonstrates an end-to-end DevOps deployment of a static website called **Varun Cabs Bangalore** using:

- Linux (Ubuntu EC2)
- AWS EC2
- Git & GitHub
- Docker
- Docker Hub
- Route53 DNS
- Nginx Reverse Proxy
- SSL Certificate (Let's Encrypt)
- GitHub Repository

Final Website:

https://varun-cabs.site

---

# Architecture

```text
Developer
    ↓
GitHub Repository
    ↓
Docker Build
    ↓
Docker Hub
    ↓
AWS EC2
    ↓
Nginx Reverse Proxy
    ↓
SSL Certificate
    ↓
varun-cabs.site
```

---

# Phase 1 - Launch EC2 Instance

## Objective

Create a Linux server to host the application.

### AWS Configuration

- Ubuntu EC2 Instance
- Public IP Enabled

### Open Ports

```text
22 SSH
80 HTTP
443 HTTPS
```

### Connect to EC2

```bash
ssh -i key.pem ubuntu@PUBLIC_IP
```

---

# Phase 2 - Update Linux Server

Update package repository

```bash
sudo apt update
```

Purpose:

```text
Downloads latest package information.
```

---

# Phase 3 - Install Docker

Install Docker:

```bash
sudo apt install docker.io -y
```

Enable Docker:

```bash
sudo systemctl enable docker
```

Start Docker:

```bash
sudo systemctl start docker
```

Verify Docker:

```bash
docker --version
```

Check running containers:

```bash
docker ps
```

Test Docker:

```bash
docker run hello-world
```

Purpose:

```text
Verifies Docker installation.
```

---

# Phase 4 - Create Website

Create project directory:

```bash
mkdir varun-cabs

cd varun-cabs
```

Create website:

```bash
vi index.html
```

Purpose:

```text
Contains the website source code.
```

---

# Phase 5 - Create Dockerfile

Create Dockerfile:

```bash
vi Dockerfile
```

Contents:

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

Explanation:

FROM nginx:latest

```text
Uses official nginx image.
```

COPY

```text
Copies website file inside nginx web root.
```

EXPOSE 80

```text
Makes container listen on port 80.
```

---

# Phase 6 - Build Docker Image

Build image:

```bash
docker build -t varun-cabs:v1 .
```

Explanation:

```text
docker build = Create image

-t = Tag

varun-cabs:v1 = Image Name and Version

. = Current Directory
```

Verify:

```bash
docker images
```

---

# Phase 7 - Run Docker Container

Run website:

```bash
docker run -d -p 80:80 --name varun-cabs-app varun-cabs:v1
```

Explanation:

-d

```text
Detached mode
```

-p 80:80

```text
Host Port : Container Port
```

Verify:

```bash
docker ps
```

Test:

```bash
curl localhost
```

---

# Phase 8 - GitHub Integration

Initialize repository

```bash
git init
```

Add files

```bash
git add .
```

Commit files

```bash
git commit -m "Initial Varun Cabs Website"
```

Connect GitHub

```bash
git remote add origin https://github.com/santhosh2958-dot/varun-cabs.git
```

Push code

```bash
git push -u origin main
```

Purpose:

```text
Source code version control.
```

---

# Phase 9 - Domain Configuration

Domain:

```text
varun-cabs.site
```

DNS Provider:

```text
AWS Route53
```

Public IP:

```text
13.203.192.176
```

Create A Record:

```text
varun-cabs.site -> 13.203.192.176
```

Create WWW Record:

```text
www -> 13.203.192.176
```

Purpose:

```text
Maps domain to EC2 server.
```

---

# Phase 10 - Install Nginx

Install nginx:

```bash
sudo apt install nginx -y
```

Start nginx:

```bash
sudo systemctl start nginx
```

Verify:

```bash
sudo systemctl status nginx
```

Purpose:

```text
Acts as Reverse Proxy.
```

---

# Phase 11 - Configure HTTPS SSL

Install Certbot:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Generate Certificate:

```bash
sudo certbot --nginx
```

Enter:

```text
varun-cabs.site
www.varun-cabs.site
```

Result:

```text
HTTPS Enabled
Automatic Renewal Configured
```

Purpose:

```text
Secures the website using SSL.
```

---

# Phase 12 - Nginx Reverse Proxy

Run container on:

```bash
docker run -d \
--name varun-cabs-app \
-p 8080:80 \
varun-cabs:v2
```

Nginx forwards requests:

```text
Internet
   ↓
Nginx
   ↓
localhost:8080
   ↓
Docker Container
```

Benefits:

- SSL handled by nginx
- Better security
- Production architecture

---

# Phase 13 - Docker Hub

Create Docker Hub account.

Login:

```bash
docker login
```

Tag image:

```bash
docker tag varun-cabs:v2 santhosh2958/varun-cabs:v2
```

Tag latest:

```bash
docker tag varun-cabs:v2 santhosh2958/varun-cabs:latest
```

Push image:

```bash
docker push santhosh2958/varun-cabs:v2
```

Purpose:

```text
Stores images centrally.
```

Benefits:

```text
Deploy image anywhere.

EC2 crash?
→ Pull image from Docker Hub.
```

---

# Project Components Learned

## Linux

Commands:

```bash
cd
ls
pwd
cat
vi
systemctl
```

---

## Git & GitHub

Commands:

```bash
git init
git add .
git commit
git push
```

---

## Docker

Commands:

```bash
docker build
docker run
docker ps
docker images
docker stop
docker rm
docker push
```

---

## AWS

Services Used:

```text
EC2
Route53
Security Groups
```

---

## Nginx

Used As:

```text
Reverse Proxy
```

---

## SSL

Tool:

```text
Let's Encrypt
Certbot
```

---

# Current Project Status

✅ Linux

✅ AWS EC2

✅ Docker

✅ Dockerfile

✅ Docker Image

✅ Docker Container

✅ GitHub Repository

✅ Docker Hub

✅ Route53 DNS

✅ Domain Mapping

✅ Nginx

✅ SSL Certificate

✅ Production Website

---

# Next Learning Roadmap

```text
GitHub Actions
     ↓
Jenkins
     ↓
SonarQube
     ↓
Trivy
     ↓
Kubernetes
     ↓
Ingress
     ↓
Monitoring
```

# Final Outcome

Successfully deployed a Dockerized production website on AWS EC2 with Domain, SSL, Docker Hub, GitHub integration, and Nginx reverse proxy using DevOps practices.
