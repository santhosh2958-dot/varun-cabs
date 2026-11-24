<<<<<<< HEAD
# Varun Cabs - End-to-End DevOps Project
=======
# Varun Cabs Bangalore – End-to-End DevOps Project
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

**Project:** Varun Cabs Bangalore  
**Website:** https://varun-cabs.site  
**GitHub Repository:** https://github.com/santhosh2958-dot/varun-cabs.git  
**Docker Hub Repository:** `santhosh2958/varun-cabs`  
**Hosting:** AWS EC2 – Ubuntu Linux

<<<<<<< HEAD
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
=======
---

# 1. Project Overview

This project demonstrates the implementation of an end-to-end DevOps workflow by deploying a static website (Varun Cabs Bangalore) using AWS cloud infrastructure and modern DevOps tools.

The main objective is to understand how a real-world website is developed, containerized, deployed, automated and maintained.

## Technologies Used

- Linux Administration – Ubuntu
- AWS EC2 – Cloud Server
- Git – Version Control
- GitHub – Source Code Management
- Docker – Containerization
- Docker Hub – Image Registry
- Nginx – Web Server and Reverse Proxy
- Route 53 – DNS Management
- Let's Encrypt – SSL Certificate
- Certbot – SSL Automation
- GitHub Actions – CI Automation
- Jenkins – CI/CD Pipeline
- Kubernetes – Future Learning

## Learning Objectives

1. Understand Linux server administration.
2. Create and configure an AWS EC2 instance.
3. Develop and deploy a static website.
4. Understand Docker images and containers.
5. Upload Docker images to Docker Hub.
6. Integrate GitHub with the EC2 server.
7. Configure domain mapping using Route 53.
8. Configure Nginx reverse proxy.
9. Enable HTTPS using Let's Encrypt.
10. Understand GitHub Actions.
11. Install and configure Jenkins.
12. Create Jenkins pipelines.
13. Configure automatic container recovery after EC2 restart.
14. Understand real-world application troubleshooting.

---

# 2. Final Website

```text
https://varun-cabs.site
```

Website features:

- Varun Cabs Bangalore branding
- Home page
- Cab services
- Sedan and SUV options
- Airport pickup and drop
- Outstation packages
- Contact information
- Call and WhatsApp integration

---

# 3. Project Architecture

## Overall Architecture

```text
                    DEVELOPER
                        |
                        |
                   Git Commands
                        |
                        v
                 GITHUB REPOSITORY
                        |
                        |
                  GitHub Actions
                        |
                        v
                   DOCKER BUILD
                        |
                        v
                    DOCKER HUB
                        |
                        |
                 AWS EC2 INSTANCE
                        |
                        |
              +---------+----------+
              |                    |
              v                    v
           NGINX                JENKINS
         Port 80/443            Port 9090
              |                    |
              |                    v
              |               Git Checkout
              |                    |
              |                    v
              |               Docker Build
              |                    |
              |                    v
              |               Docker Hub
              |
              v
        localhost:8080
              |
              v
       DOCKER CONTAINER
              |
              v
       NGINX CONTAINER
              |
              v
       VARUN CABS WEBSITE
```

**Important:** GitHub Actions and Jenkins are two separate automation approaches in this project. The complete automated deployment between them is still a learning objective. Do not assume both pipelines are already connected.

## Application Traffic Flow

```text
Customer Browser
       |
       v
varun-cabs.site
       |
       v
Route 53 DNS
       |
       v
AWS EC2 Public IP / Elastic IP
       |
       v
Nginx Reverse Proxy
       |
       v
EC2 Port 8080
       |
       v
Docker Container Port 80
       |
       v
Varun Cabs Website
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
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
=======
# 4. AWS Infrastructure

## AWS Services Used

```text
1. EC2
2. Route 53
3. Security Groups
4. Elastic IP (Recommended)
```

## EC2 Instance

Operating System:

```text
Ubuntu Linux
```

Application directory:

```text
/home/ubuntu/varun-cabs
```

## EC2 Security Group

Required inbound rules:

| Port | Protocol | Purpose |
|---|---|---|
| 22 | TCP | SSH |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 9090 | TCP | Jenkins UI, restricted access |
| 50000 | TCP | Jenkins inbound agents, only if needed |

**Security recommendation:**

- Allow SSH only from your trusted IP address.
- Allow HTTP and HTTPS from the internet.
- Restrict Jenkins port 9090 to your IP or VPN.
- Do not expose port 50000 publicly unless inbound Jenkins agents require it.
- Do not expose Docker application port 8080 publicly if Nginx is the intended entry point.

## Connect to EC2

From your local system:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
ssh -i key.pem ubuntu@PUBLIC_IP
```

Verify the operating system:

```bash
cat /etc/os-release
```

Check hostname:

```bash
hostname
```

Check private IP:

```bash
hostname -I
```

Check public IP:

```bash
curl ifconfig.me
```

---

<<<<<<< HEAD
# Phase 2: Linux Setup
=======
# 5. Linux Initial Setup
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

Update Ubuntu package metadata:

```bash
sudo apt update
```

<<<<<<< HEAD
Explanation:

```text
Downloads latest package metadata from Ubuntu repositories.
=======
Upgrade installed packages:

```bash
sudo apt upgrade -y
```

Install useful utilities:

```bash
sudo apt install git curl wget unzip vim nano \
net-tools dnsutils lsof -y
```

Verify Git:

```bash
git --version
```

Verify curl:

```bash
curl --version
```

Check disk:

```bash
df -h
```

Check memory:

```bash
free -h
```

Check CPU:

```bash
nproc
```

Check running processes:

```bash
top
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
# Phase 3: Install Docker

Install Docker
=======
# 6. Install Docker

## Install Docker
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
sudo apt update
sudo apt install docker.io -y
```

<<<<<<< HEAD
Start Docker
=======
Start Docker:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
sudo systemctl start docker
```

<<<<<<< HEAD
Enable Docker
=======
Enable Docker at system startup:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
sudo systemctl enable docker
```

<<<<<<< HEAD
Verify Docker
=======
Verify:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker --version
```

<<<<<<< HEAD
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
=======
Check Docker service:

```bash
sudo systemctl status docker
```

## Test Docker

```bash
sudo docker run hello-world
```

Expected result:

```text
Hello from Docker!
```

This confirms that Docker Engine is working correctly.

## Optional: Run Docker Without sudo

```bash
sudo usermod -aG docker ubuntu
```

Log out and reconnect to apply group membership.

Verify:

```bash
groups
```

Test:

```bash
docker ps
```

**Security note:** Membership in the Docker group grants highly privileged access to the host. Treat it similarly to root-level access.

---

# 7. Create Varun Cabs Website
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

Project Directory

```bash
cd /home/ubuntu
mkdir varun-cabs
cd varun-cabs
```

<<<<<<< HEAD
Create Website File
=======
Check current location:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
pwd
```

<<<<<<< HEAD
Contains:

```text
Varun Cabs Bangalore Website HTML Code
=======
Create HTML file:

```bash
nano index.html
```

Add your Varun Cabs website HTML, CSS and JavaScript.

Save the file.

Verify:

```bash
cat index.html
```

List files:

```bash
ls -la
```

Expected structure:

```text
varun-cabs/
|
|-- index.html
|-- Dockerfile
|-- README.md
|-- .gitignore
|
|-- .github/
    |
    |-- workflows/
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
# Phase 5: Create Dockerfile

Create Dockerfile
=======
# 8. Create Dockerfile

Create:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
nano Dockerfile
```

<<<<<<< HEAD
Content
=======
Content:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

<<<<<<< HEAD
Explanation

```text
FROM
→ Uses official nginx image.

COPY
→ Copies website into nginx web root.

EXPOSE
→ Opens port 80.
=======
## Explanation

### FROM

```dockerfile
FROM nginx:latest
```

Uses the official Nginx Docker image as the base image.

### COPY

```dockerfile
COPY index.html /usr/share/nginx/html/index.html
```

Copies our website into the Nginx document root.

### EXPOSE

```dockerfile
EXPOSE 80
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

Documents the port used by the application inside the container.

Important: EXPOSE does not publish the port to the EC2 host. Port publishing is done using `-p`.

---

<<<<<<< HEAD
# Phase 6: Build Docker Image
=======
# 9. Build Docker Image

Navigate to the project directory:

```bash
cd /home/ubuntu/varun-cabs
```
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

Build image

```bash
docker build -t varun-cabs:v1 .
```

Explanation

```text
docker build
<<<<<<< HEAD
    Creates image

-t
    Tag image

varun-cabs:v1
    Image Name : Version

.
    Current directory
```

Verify
=======
    Builds the Docker image.

-t
    Assigns a name and tag.

varun-cabs
    Image name.

v1
    Image version.

.
    Current directory containing Dockerfile.
```

Check images:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker images
```

<<<<<<< HEAD
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
=======
Build second version:

```bash
docker build -t varun-cabs:v2 .
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
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
=======
# 10. Run Docker Container

Initially, the application was deployed directly on port 80.
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker run -d \
-p 80:80 \
--name varun-cabs-app \
varun-cabs:v1
```

<<<<<<< HEAD
Add Files
=======
However, Nginx was later installed directly on the EC2 host.
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

Therefore, the application container was moved to port 8080.

<<<<<<< HEAD
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
=======
## Final Application Deployment
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker run -d \
--name varun-cabs-app \
-p 8080:80 \
varun-cabs:v2
```

<<<<<<< HEAD
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
=======
Explanation:

```text
-d
    Runs container in background.

--name
    Assigns container name.

-p 8080:80
    EC2 host port 8080 maps to container port 80.

varun-cabs:v2
    Docker image used to create container.
```

## Verify Container

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

Test website:

```bash
curl http://localhost:8080
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
# Phase 13: Docker Hub

Login
=======
# 11. Docker Images and Containers

## Docker Image

A Docker image is a packaged template used to create containers.

Example:

```text
varun-cabs:v1
varun-cabs:v2
```

Commands:

```bash
docker images
docker image ls
docker inspect varun-cabs:v2
docker history varun-cabs:v2
```

## Docker Container

A container is a running or stopped instance of a Docker image.

Commands:

```bash
docker ps
docker ps -a
docker container ls
docker start varun-cabs-app
docker stop varun-cabs-app
docker restart varun-cabs-app
docker logs varun-cabs-app
docker inspect varun-cabs-app
docker rm varun-cabs-app
```

## Important Difference

```text
Docker Image
     |
     v
Docker Run
     |
     v
Docker Container
     |
     v
Running Application
```

An image is not the same as a container.

Deleting a container does not automatically delete its image.

---

# 12. Docker Container Management

## Start Container

```bash
docker start varun-cabs-app
```

## Stop Container

```bash
docker stop varun-cabs-app
```

## Restart Container

```bash
docker restart varun-cabs-app
```

## Remove Container

```bash
docker stop varun-cabs-app
docker rm varun-cabs-app
```

## View Logs

```bash
docker logs varun-cabs-app
```

Last 100 lines:

```bash
docker logs --tail 100 varun-cabs-app
```

Follow live logs:

```bash
docker logs -f varun-cabs-app
```

## Enter Container

```bash
docker exec -it varun-cabs-app bash
```

For images without Bash:

```bash
docker exec -it varun-cabs-app sh
```

Exit:

```bash
exit
```

## Check Container Port

```bash
docker port varun-cabs-app
```

## Check Container Details

```bash
docker inspect varun-cabs-app
```

---

# 13. Git and GitHub Integration

## Configure Git

```bash
git config --global user.name "Santhosh"

git config --global user.email "YOUR_GITHUB_EMAIL"
```

Verify:

```bash
git config --list
```

## Initialize Repository

```bash
cd /home/ubuntu/varun-cabs

git init
```

## Add Files

```bash
git add .
```

## Commit

```bash
git commit -m "Initial Varun Cabs Website"
```

## Connect GitHub

```bash
git remote add origin git@github.com:santhosh2958-dot/varun-cabs.git
```

Check remote:

```bash
git remote -v
```

Set branch:

```bash
git branch -M main
```

Push:

```bash
git push -u origin main
```

## Common Git Commands

```bash
git status
git add .
git commit -m "Updated website"
git push origin main
git pull origin main
git log --oneline
git branch
git remote -v
```

## SSH Authentication

Generate SSH key:

```bash
ssh-keygen -t ed25519 -C "YOUR_GITHUB_EMAIL"
```

Display public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Add the public key to your GitHub SSH keys.

Test:

```bash
ssh -T git@github.com
```

Expected:

```text
Hi santhosh2958-dot!
You've successfully authenticated.
```

Never share your private key:

```text
~/.ssh/id_ed25519
```

---

# 14. Route 53 Domain Mapping

Domain:

```text
varun-cabs.site
```

Purpose:

Route 53 maps the domain name to the EC2 server's public IP address.

## Create A Record

```text
Record name:
varun-cabs.site

Record type:
A

Value:
YOUR_EC2_ELASTIC_IP
```

## Create WWW Record

```text
Record name:
www.varun-cabs.site

Record type:
A

Value:
YOUR_EC2_ELASTIC_IP
```

You can also use a suitable alias record where supported.

## Verify DNS

```bash
nslookup varun-cabs.site
```

```bash
nslookup www.varun-cabs.site
```

Check DNS propagation:

```bash
dig varun-cabs.site
```

## Important: Elastic IP

EC2 public IPv4 addresses can change when an instance is stopped and started.

For a domain-based website, allocate an Elastic IP and associate it with your EC2 instance.

Update Route 53 records to point to the Elastic IP.

This prevents your domain from pointing to an outdated public IP after an EC2 restart.

Note: Elastic IPs may incur AWS charges depending on usage and account conditions. Check current AWS pricing.

---

# 15. Install Nginx on Ubuntu

Install:

```bash
sudo apt install nginx -y
```

Start:

```bash
sudo systemctl start nginx
```

Enable automatic startup:

```bash
sudo systemctl enable nginx
```

Check:

```bash
sudo systemctl status nginx
```

Test configuration:

```bash
sudo nginx -t
```

Restart:

```bash
sudo systemctl restart nginx
```

Reload without a full restart:

```bash
sudo systemctl reload nginx
```

---

# 16. Nginx Reverse Proxy

## Why Reverse Proxy?

Initially, Docker occupied port 80.

Later, Nginx was installed directly on the EC2 host.

Both cannot listen on the same host IP and port simultaneously.

Therefore, the application was moved to port 8080.

## Final Port Mapping

```text
EC2 Host Port 8080
        |
        v
Docker Container Port 80
```

## Nginx Configuration

Edit:

```bash
sudo vi /etc/nginx/sites-available/default
```

A simplified HTTP proxy configuration:

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

Important: Preserve any existing Certbot-managed HTTPS server blocks when modifying this file.

Test:

```bash
sudo nginx -t
```

Restart:

```bash
sudo systemctl restart nginx
```

## Test Reverse Proxy

Test Docker directly:

```bash
curl http://localhost:8080
```

Test through Nginx:

```bash
curl http://localhost
```

If the first command works but the second fails, troubleshoot Nginx.

If both work locally but the domain fails, investigate DNS, Security Groups and HTTPS configuration.

---

# 17. Enable HTTPS Using Let's Encrypt

Install Certbot:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Generate SSL certificate:

```bash
sudo certbot --nginx
```

Select:

```text
varun-cabs.site
www.varun-cabs.site
```

Verify:

```text
https://varun-cabs.site
```

## Check SSL Certificate

```bash
sudo certbot certificates
```

## Test Renewal

```bash
sudo certbot renew --dry-run
```

Certbot normally configures automatic renewal through a systemd timer or scheduled task.

Check timer:

```bash
sudo systemctl list-timers | grep certbot
```

---

# 18. Docker Hub Integration

Docker Hub is a central repository for storing Docker images.

Repository:

```text
santhosh2958/varun-cabs
```

## Login
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker login
```

<<<<<<< HEAD
Tag Image
=======
Use a Docker Hub access token where possible.

## Tag Image
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker tag varun-cabs:v2 santhosh2958/varun-cabs:v2

docker tag varun-cabs:v2 santhosh2958/varun-cabs:latest
```

<<<<<<< HEAD
Push
=======
## Push Image
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker push santhosh2958/varun-cabs:v2

docker push santhosh2958/varun-cabs:latest
```

<<<<<<< HEAD
Result

```text
Image stored in Docker Hub
```

Purpose

```text
Central Image Repository
Backup Images
Easy Deployment
=======
```bash
docker push santhosh2958/varun-cabs:latest
```

## Verify

```bash
docker images
```

Check your Docker Hub repository online.

## Pull Image

On another server:

```bash
docker pull santhosh2958/varun-cabs:v2
```

Run:

```bash
docker run -d \
--name varun-cabs-app \
-p 8080:80 \
santhosh2958/varun-cabs:v2
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
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
=======
# 19. GitHub Actions

## Objective

Automate Docker image building and pushing whenever code is pushed to GitHub.

## Workflow

```text
Developer
    |
    v
Git Push
    |
    v
GitHub Repository
    |
    v
GitHub Actions
    |
    v
Docker Build
    |
    v
Docker Hub Push
```

## Workflow File

Location:

```text
.github/workflows/dockerhub.yml
```

Example workflow:

```yaml
name: Build and Push Docker Image

on:
  push:
    branches:
      - main

jobs:
  docker:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Docker Hub Login
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_TOKEN }}

      - name: Build and Push
        uses: docker/build-push-action@v6
        with:
          context: .
          push: true
          tags: |
            santhosh2958/varun-cabs:v2
            santhosh2958/varun-cabs:latest
```

## Configure GitHub Secrets

Go to:

```text
GitHub Repository
    |
    v
Settings
    |
    v
Secrets and variables
    |
    v
Actions
```

Create:

```text
DOCKER_USERNAME
DOCKER_TOKEN
```

Never hardcode Docker Hub credentials in workflow files.

The example uses fixed tags for learning. For a more maintainable pipeline, use unique tags such as the Git commit SHA.

## Commit Workflow

```bash
git add .github/workflows/dockerhub.yml

git commit -m "Added Docker Hub automation"

git push origin main
```

Check:

```text
GitHub Repository
    |
    v
Actions
    |
    v
Workflow Execution
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
# Phase 15: Jenkins Installation

Create Volume
=======
# 20. Jenkins Installation Using Docker

Jenkins is an automation server used to build CI/CD pipelines.

## Create Jenkins Volume
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker volume create jenkins_home
```

<<<<<<< HEAD
Run Jenkins
=======
Verify:

```bash
docker volume ls
```

## Run Jenkins
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```bash
docker run -d \
--name jenkins \
-p 9090:8080 \
-p 50000:50000 \
-v jenkins_home:/var/jenkins_home \
jenkins/jenkins:lts
```

<<<<<<< HEAD
Access

```text
http://SERVER_IP:9090
=======
For the later Docker integration experiment, you also used:

```bash
-v /var/run/docker.sock:/var/run/docker.sock
```

This mounts the host Docker socket inside Jenkins. It provides powerful control over the EC2 host's Docker Engine and must be treated as a high-privilege security configuration.

## Access Jenkins

```text
http://EC2_PUBLIC_IP:9090
```

Prefer restricting access through your Security Group and using HTTPS or a secure access method for long-term use.

## View Jenkins Logs

```bash
docker logs jenkins
```

Follow logs:

```bash
docker logs -f jenkins
```

## Initial Admin Password

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
# Phase 16: Jenkins Plugins

Installed
=======
# 21. Jenkins Volume and Persistence

You created:

```bash
docker volume create jenkins_home
```

This is important because Jenkins stores:

- Jobs
- Plugins
- Pipeline configuration
- Credentials
- Build history
- User information

Inside the container:

```text
/var/jenkins_home
```

Docker volume:

```text
jenkins_home
```

The volume ensures that Jenkins data is not tied only to the container's writable filesystem.

## Verify Volume

```bash
docker volume ls
```

Inspect:

```bash
docker volume inspect jenkins_home
```

Important:

```bash
docker rm jenkins
```

removes the container, but does not automatically delete the named volume.

Do not run:

```bash
docker volume rm jenkins_home
```

unless you intentionally want to delete Jenkins data and have verified your backups.

---

# 22. Jenkins Plugins

Plugins installed or explored:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```text
Git Plugin
Pipeline Plugin
Docker Plugin
Docker Workflow Plugin
SSH Agent
```

<<<<<<< HEAD
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
=======
Purpose:

| Plugin | Purpose |
|---|---|
| Git | Git repository integration |
| Pipeline | Jenkins pipeline jobs |
| Docker | Docker-related integration |
| Docker Workflow | Docker operations in pipelines |
| SSH Agent | SSH credential management |

Plugin availability and compatibility depend on the installed Jenkins version.

---

# 23. First Jenkins Pipeline

Create a Pipeline job.

Example:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```groovy
pipeline {

    agent any

    stages {

        stage('Test') {
<<<<<<< HEAD
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
=======

            steps {

                echo 'Jenkins Pipeline Works!'

            }

        }

    }

}
```

Expected output:

```text
Jenkins Pipeline Works!

Finished: SUCCESS
```

## Jenkins Pipeline Concepts

```text
Pipeline
    Complete automation workflow.

Agent
    Machine or executor where pipeline runs.

Stage
    Logical section of a pipeline.

Step
    Individual command or operation.

Workspace
    Directory where Jenkins checks out and
    processes project files.
```

---

# 24. GitHub Integration With Jenkins

Repository:

```text
https://github.com/santhosh2958-dot/varun-cabs.git
```

Example checkout:

```groovy
pipeline {

    agent any

    stages {

        stage('Checkout') {

            steps {

                git branch: 'main',
                    url: 'https://github.com/santhosh2958-dot/varun-cabs.git'

            }

        }

        stage('List Files') {

            steps {

                sh 'ls -la'

            }

        }

    }

}
```

Expected repository files:
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```text
Dockerfile
README.md
index.html
<<<<<<< HEAD
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
=======
.github/
```

Expected result:

```text
Repository cloned successfully.

Finished: SUCCESS
```

For a private repository, configure Jenkins credentials instead of relying on anonymous access.

---

# 25. Jenkins Docker Integration – Issue Encountered

## Error
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

```text
docker: not found
```

<<<<<<< HEAD
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
=======
## Reason

Docker was installed on the EC2 host.

Jenkins was running inside a separate Docker container.

These are separate environments.

```text
EC2 Host
    |
    |-- Docker Engine
    |
    |-- Jenkins Container
           |
           |-- Jenkins Pipeline
           |
           |-- Docker CLI not installed
```

## Learning

```text
Docker Engine on Host
        !=
Docker CLI inside Jenkins
```

Mounting the Docker socket alone does not automatically install the Docker CLI inside Jenkins.

To complete the integration, you need a compatible Docker CLI in the Jenkins execution environment and access to the host Docker socket.

**Security warning:** A Jenkins container with access to `/var/run/docker.sock` can potentially control the host Docker Engine and gain extensive host-level privileges. Do not expose this configuration to untrusted jobs or users.

---

# 26. MOST IMPORTANT: EC2 Shutdown and Restart Recovery

## Problem Encountered

You manually powered off your EC2 instance:

```bash
sudo shutdown -h now
```

Later, you started the EC2 instance again.

Your website displayed:

```text
502 Bad Gateway

nginx/1.24.0 (Ubuntu)
```

When you checked:

```bash
docker ps
```

Output:

```text
CONTAINER ID   IMAGE   COMMAND   CREATED   STATUS   PORTS   NAMES
```

No running containers were displayed.

However:

```bash
docker ps -a
```

showed:

```text
jenkins
varun-cabs-app
hello-world
```

The containers still existed, but they were stopped.

## Why Did This Happen?

When EC2 shuts down:

1. The Linux operating system stops.
2. Running Docker containers stop.
3. Docker Engine stops.
4. Host Nginx stops.
5. When EC2 starts, Linux boots again.
6. Docker must start.
7. Containers need a restart policy to start automatically.
8. Host Nginx must also start automatically.

The default Docker restart policy is:

```text
no
```

Therefore, containers do not automatically restart by default.

## Step 1: Enable Docker at System Startup

```bash
sudo systemctl enable docker
```

Start Docker immediately:

```bash
sudo systemctl start docker
```

Check:

```bash
sudo systemctl status docker
```

Expected:

```text
Active: active (running)
```

## Step 2: Configure Varun Cabs Automatic Restart

Your existing container:

```text
varun-cabs-app
```

Run:

```bash
docker update --restart unless-stopped varun-cabs-app
```

## Step 3: Configure Jenkins Automatic Restart

```bash
docker update --restart unless-stopped jenkins
```

These commands update existing containers. You do not need to rebuild the images.

## Step 4: Start Both Containers

```bash
docker start varun-cabs-app

docker start jenkins
```

Check:

```bash
docker ps
```

## Step 5: Verify Restart Policies

```bash
docker inspect -f '{{.Name}} {{.HostConfig.RestartPolicy.Name}}' varun-cabs-app
```

```bash
docker inspect -f '{{.Name}} {{.HostConfig.RestartPolicy.Name}}' jenkins
```

Expected:

```text
/varun-cabs-app unless-stopped
/jenkins unless-stopped
```

## Docker Restart Policies

| Policy | Behaviour |
|---|---|
| no | No automatic restart |
| always | Always restart automatically |
| unless-stopped | Restart unless manually stopped |
| on-failure | Restart when the container exits with an error |

For this project:

```bash
--restart unless-stopped
```

is recommended.

## For Future Container Creation

Always include the restart policy when creating the application container:

```bash
docker run -d \
--name varun-cabs-app \
--restart unless-stopped \
-p 8080:80 \
varun-cabs:v2
```

For Jenkins:

```bash
docker run -d \
--name jenkins \
--restart unless-stopped \
-p 9090:8080 \
-p 50000:50000 \
-v jenkins_home:/var/jenkins_home \
jenkins/jenkins:lts
```

Only publish Jenkins agent port 50000 if your agent configuration requires it.

## Step 6: Enable Nginx at Boot

Nginx is installed directly on Ubuntu, not inside Docker.

Enable:

```bash
sudo systemctl enable nginx
```

Start:

```bash
sudo systemctl start nginx
```

Check:

```bash
sudo systemctl status nginx
```

## Step 7: Verify Nginx Configuration

```bash
sudo nginx -t
```

Restart if required:

```bash
sudo systemctl restart nginx
```

## Step 8: Verify Website

Test Docker application:

```bash
curl http://localhost:8080
```

Test Nginx:

```bash
curl http://localhost
```

Test domain:

```bash
curl -I https://varun-cabs.site
```

## Step 9: Test EC2 Reboot

After configuring everything:

```bash
docker ps
```

Reboot EC2:

```bash
sudo reboot
```

Wait for the instance to boot.

Reconnect using SSH.

Check:

```bash
sudo systemctl status docker

sudo systemctl status nginx

docker ps
```

Expected:

```text
varun-cabs-app    Up
jenkins           Up
```

Then test:

```bash
curl http://localhost:8080

curl http://localhost
```

Open:

```text
https://varun-cabs.site
```

**Important:** A Linux reboot test is different from an EC2 Stop/Start test. After EC2 Stop/Start, verify its IP address and Elastic IP association as well.

---

# 27. Understanding HTTP 502 Bad Gateway

## What Is 502?

A 502 Bad Gateway means the reverse proxy could not obtain a valid response from the configured backend.

In our project:

```text
Browser
   |
   v
Nginx
   |
   v
localhost:8080
   |
   v
Docker Application
```

If the application container is stopped, Nginx cannot reach the backend.

## Troubleshooting Step 1

```bash
docker ps
```

Check whether the application container is running.

## Troubleshooting Step 2

```bash
docker ps -a
```

Check stopped containers.

## Troubleshooting Step 3

```bash
docker start varun-cabs-app
```

## Troubleshooting Step 4

```bash
docker logs --tail 100 varun-cabs-app
```

## Troubleshooting Step 5

```bash
docker port varun-cabs-app
```

Expected:

```text
80/tcp -> 0.0.0.0:8080
```

## Troubleshooting Step 6

```bash
curl http://localhost:8080
```

## Troubleshooting Step 7

```bash
sudo systemctl status nginx
```

## Troubleshooting Step 8

```bash
sudo nginx -t
```

## Troubleshooting Step 9

```bash
sudo tail -50 /var/log/nginx/error.log
```

## Troubleshooting Step 10

```bash
sudo grep -R "proxy_pass" /etc/nginx/sites-enabled/
```

Check whether Nginx points to:

```text
http://127.0.0.1:8080
```

If the backend responds correctly but Nginx still returns 502, investigate the Nginx error log and proxy configuration.

---

# 28. Docker Volumes and Data Persistence

A Docker container's writable filesystem is not a reliable place to keep important persistent data.

Docker volumes help preserve application data independently of container lifecycle.

## List Volumes

```bash
docker volume ls
```

## Create Volume

```bash
docker volume create jenkins_home
```

## Inspect Volume

```bash
docker volume inspect jenkins_home
```

## Important

For Jenkins:

```text
jenkins_home
    |
    v
/var/jenkins_home
```

This preserves Jenkins data when the container is replaced.

The volume itself is still stored on the EC2 host. It is not a backup against EC2 disk loss, accidental volume deletion or instance destruction.

Maintain separate backups for important data.

---

# 29. Docker Cleanup Commands

Check Docker disk usage:

```bash
docker system df
```

Remove stopped containers:

```bash
docker container prune
```

Remove unused images:

```bash
docker image prune
```

Remove unused networks:

```bash
docker network prune
```

Remove unused build cache:

```bash
docker builder prune
```

Remove unused Docker resources:

```bash
docker system prune
```

**Warning:** Do not blindly execute cleanup commands on a production server.

Avoid `docker system prune -a --volumes` unless you fully understand which images and volumes will be removed. Your Jenkins data could be affected by volume deletion.

---

# 30. Daily DevOps Troubleshooting Commands
>>>>>>> 498e1fa (Updated complete DevOps project documentation)

## Linux

```bash
<<<<<<< HEAD
ls
cd
=======
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
pwd
ls -la
cd
cat
nano
vi
grep
find
df -h
free -h
top
ps aux
hostname
hostname -I
ip a
ss -tulpn
lsof -i :80
```

<<<<<<< HEAD
---

=======
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
## Git

```bash
git status
git add .
<<<<<<< HEAD
git commit
git push
git pull
=======
git commit -m "Updated website"
git push origin main
git pull origin main
git log --oneline
git branch
git remote -v
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

## Docker

```bash
<<<<<<< HEAD
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
=======
docker --version
docker info
docker images
docker ps
docker ps -a
docker build -t varun-cabs:v2 .
docker run -d -p 8080:80 varun-cabs:v2
docker start varun-cabs-app
docker stop varun-cabs-app
docker restart varun-cabs-app
docker logs varun-cabs-app
docker exec -it varun-cabs-app bash
docker inspect varun-cabs-app
docker port varun-cabs-app
docker volume ls
docker system df
```

## Nginx

```bash
sudo systemctl status nginx
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl enable nginx
sudo nginx -t
sudo tail -f /var/log/nginx/error.log
```

## AWS / Networking

```bash
curl ifconfig.me
nslookup varun-cabs.site
dig varun-cabs.site
curl -I https://varun-cabs.site
```

## Jenkins

```bash
docker ps
docker logs jenkins
docker logs -f jenkins
docker start jenkins
docker stop jenkins
docker restart jenkins
docker exec -it jenkins bash
docker volume ls
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
```

---

<<<<<<< HEAD
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
=======
# 31. Important System Startup Commands

These commands are especially important when operating an EC2 instance.

## Enable Docker

```bash
sudo systemctl enable docker
```

## Enable Nginx

```bash
sudo systemctl enable nginx
```

## Start Docker

```bash
sudo systemctl start docker
```

## Start Nginx

```bash
sudo systemctl start nginx
```

## Check Services

```bash
sudo systemctl status docker

sudo systemctl status nginx
```

## Check Containers

```bash
docker ps -a
```

## Check Restart Policies

```bash
docker inspect -f '{{.Name}} {{.HostConfig.RestartPolicy.Name}}' $(docker ps -aq)
```

This command checks restart policies for all existing containers.

---

# 32. EC2 Maintenance and Backup Strategy

For reliable operation, follow these practices.

## EC2

- Use an Elastic IP for stable domain mapping.
- Monitor EC2 instance status.
- Monitor disk and memory usage.
- Avoid unnecessary Stop/Start operations on production workloads.
- Take EBS snapshots before major infrastructure changes.

## Docker

- Configure restart policies.
- Keep important data in named volumes.
- Use versioned images.
- Avoid unnecessary container deletion.
- Monitor container logs.

## Jenkins

- Keep Jenkins data in `jenkins_home`.
- Back up Jenkins configuration and data.
- Restrict Jenkins access.
- Keep plugins and Jenkins updated.

## SSL

- Check certificate expiry.
- Verify automatic renewal.
- Keep ports 80 and 443 accessible as required.

## GitHub

- Push source code regularly.
- Keep Dockerfile and workflow files in version control.
- Never commit private keys or passwords.

---

# 33. Real-Time Deployment Workflow

The intended future deployment process is:

```text
Developer Updates Website
          |
          v
       Git Add
          |
          v
      Git Commit
          |
          v
      Git Push
          |
          v
  GitHub Repository
          |
          v
    GitHub Actions
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
     Pull New Image
          |
          v
    Replace Container
          |
          v
    Nginx Reverse Proxy
          |
          v
  Updated Website Live
```

A complete automated deployment still needs a configured deployment mechanism between the image registry and EC2. Building and pushing an image alone does not update the running container.

---

# 34. Current Project Status

Based on the work completed and commands executed:

| Component | Status |
|---|---|
| Linux Administration | Completed learning |
| AWS EC2 | Configured |
| Docker Installation | Completed |
| Docker Image Creation | Completed |
| Docker Container Deployment | Completed |
| Varun Cabs Website | Deployed previously |
| Git | Configured |
| GitHub Repository | Created |
| SSH Authentication | Configured |
| Docker Hub | Image push commands executed |
| Route 53 | Configured |
| Domain Mapping | Configured |
| Nginx | Installed |
| Reverse Proxy | Configured previously |
| SSL Certificate | Certbot setup performed |
| GitHub Actions | Workflow files created |
| Jenkins Installation | Completed |
| Jenkins Volume | Created |
| Jenkins Plugins | Installed/explored |
| Jenkins Pipeline | Basic pipeline completed |
| Jenkins GitHub Checkout | Completed |
| Jenkins Docker Integration | In progress |
| Docker Restart Policy | Must verify/configure |
| EC2 Startup Recovery | Must test |
| Automated Deployment | Future implementation |

---

# 35. Future Learning Roadmap

## Phase 1 – Complete Current Project

- [ ] Verify Docker restart policy.
- [ ] Verify Nginx automatic startup.
- [ ] Configure Elastic IP.
- [ ] Test EC2 Stop/Start.
- [ ] Verify SSL renewal.
- [ ] Verify Jenkins persistence.
- [ ] Complete Jenkins Docker integration securely.

## Phase 2 – Advanced CI/CD

- [ ] GitHub Actions complete pipeline.
- [ ] Jenkins automated build.
- [ ] Docker Hub automated push.
- [ ] Automated EC2 deployment.
- [ ] Rollback to previous image.
- [ ] Environment variables and secrets management.

## Phase 3 – Security

- [ ] SonarQube.
- [ ] Trivy image scanning.
- [ ] IAM roles.
- [ ] AWS Systems Manager.
- [ ] Secrets management.
- [ ] Least-privilege security.

## Phase 4 – Kubernetes

- [ ] Kubernetes fundamentals.
- [ ] Pods.
- [ ] Deployments.
- [ ] Services.
- [ ] ConfigMaps.
- [ ] Secrets.
- [ ] Ingress.
- [ ] Persistent Volumes.
- [ ] Horizontal Pod Autoscaling.

## Phase 5 – Monitoring

- [ ] Prometheus.
- [ ] Grafana.
- [ ] CloudWatch.
- [ ] Application health checks.
- [ ] Server monitoring.
- [ ] Alerting.

---

# 36. DevOps Interview Questions and Answers

### Q1. What is DevOps?

DevOps is a combination of development and operations practices that helps teams deliver applications faster and more reliably through automation and collaboration.

### Q2. What is Git?

Git is a distributed version control system used to track source code changes.

### Q3. What is GitHub?

GitHub is a platform for hosting Git repositories and collaborating on source code.

### Q4. What is Docker?

Docker is a platform used to package and run applications in containers.

### Q5. What is a Docker image?

A Docker image is a template used to create containers.

### Q6. What is a Docker container?

A Docker container is an isolated runtime instance of an image.

### Q7. What is Docker Hub?

Docker Hub is a registry used to store and distribute Docker images.

### Q8. What is a Dockerfile?

A Dockerfile contains instructions to build a Docker image.

### Q9. What is Nginx?

Nginx is a web server that can also function as a reverse proxy and load balancer.

### Q10. What is a reverse proxy?

A reverse proxy receives client requests and forwards them to backend servers or applications.

### Q11. Why did we use port 8080?

Because Nginx was installed on the EC2 host and was already using port 80. The Docker application was therefore published on host port 8080.

### Q12. What is Jenkins?

Jenkins is an automation server used for building CI/CD pipelines.

### Q13. What is a Jenkins Pipeline?

A Jenkins Pipeline defines the steps and stages used to automate software delivery.

### Q14. What is a Docker volume?

A Docker volume is used to persist data independently of a container's writable filesystem.

### Q15. Why did we get 502 Bad Gateway?

Nginx could not obtain a valid response from the configured backend. In our incident, the application container was stopped.

### Q16. Why did Docker containers stop after EC2 shutdown?

The EC2 operating system stopped, which stopped its running containers. Containers without an appropriate restart policy did not automatically restart when Docker started again.

### Q17. How can we automatically restart Docker containers?

Use:

```bash
docker update --restart unless-stopped CONTAINER_NAME
```

For a new container:

```bash
docker run -d --restart unless-stopped IMAGE_NAME
```

### Q18. What is the difference between `docker ps` and `docker ps -a`?

`docker ps` displays running containers.

`docker ps -a` displays all containers, including stopped containers.

### Q19. What is the difference between `docker stop` and `docker rm`?

`docker stop` stops a running container.

`docker rm` removes a stopped container.

### Q20. What is Continuous Integration?

Continuous Integration is the practice of regularly integrating code changes and automatically building and testing them.

### Q21. What is Continuous Deployment?

Continuous Deployment automates the release of validated changes into the production environment.

### Q22. What is Kubernetes?

Kubernetes is a container orchestration platform used to manage, deploy and scale containerized applications.

---

# 37. Complete Project Flow – Quick Revision

```text
1. Developer writes website code.

2. Git tracks changes.

3. GitHub stores source code.

4. GitHub Actions automates image building.

5. Docker builds the website image.

6. Docker Hub stores the image.

7. AWS EC2 hosts the application.

8. Docker runs the application container.

9. Nginx forwards customer traffic.

10. Route 53 resolves the domain.

11. Certbot manages HTTPS certificates.

12. Jenkins automates CI/CD workflows.

13. Docker restart policies recover containers
    after server restarts.

14. Kubernetes will be introduced in the
    next phase.
```

---

# 38. Final Conclusion

Successfully developed and deployed the Varun Cabs Bangalore website using AWS EC2, Ubuntu Linux, Docker, Git, GitHub, Docker Hub, Nginx, Route 53 and SSL.

Also explored GitHub Actions and Jenkins for CI/CD automation.

During the project, encountered and learned how to troubleshoot:

- Docker installation issues.
- Docker image build issues.
- Container lifecycle management.
- Port conflicts between Nginx and Docker.
- Nginx reverse proxy configuration.
- Jenkins Docker integration issues.
- EC2 shutdown and container recovery.
- HTTP 502 Bad Gateway errors.

The next major objective is to complete automated CI/CD deployment, improve security, configure reliable server recovery and then migrate the application to Kubernetes.

**Project Learning Goal: Linux + AWS + Git + GitHub + Docker + Jenkins + CI/CD + Kubernetes.**

---

**Repository:** https://github.com/santhosh2958-dot/varun-cabs

**Website:** https://varun-cabs.site

**Project:** Varun Cabs Bangalore – End-to-End DevOps Learning Project
>>>>>>> 498e1fa (Updated complete DevOps project documentation)
