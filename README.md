# Reverse Proxy App (CI/CD Version)

A simple Multi-Container Application with Backend, Frontend, and Nginx Reverse Proxy, deployed manually or via GitHub Actions CI/CD workflow.

---

## Table of Contents

1. [Project Structure](#project-structure)  
2. [Prerequisites](#prerequisites)  
3. [Setup Instructions](#setup-instructions)  
4. [Manual Deployment](#manual-deployment)  
5. [CI/CD Deployment](#ci-cd-deployment)  
6. [Usage](#usage)

---

## Project Structure

```text
reverse-proxy-app/
├── backend/
│   ├── app.py
│   ├── Dockerfile
│   └── requirements.txt
├── frontend/
│   ├── index.html
│   └── Dockerfile
├── nginx/
│   ├── nginx.conf
│   └── Dockerfile
└── docker-compose.yml

Prerequisites
	Docker
	Docker Compose
	Git
	Access to AWS EC2 instance for deployment
	GitHub account for CI/CD workflow

Setup Instructions
	Clone the repository:
		git clone git@github.com:hmurafique/reverse-proxy-app-ci-cd.git
		cd reverse-proxy-app-ci-cd

	Create .env files if needed for environment variables.

Manual Deployment
	Build and run containers:
		docker-compose up -d --build

	Stop containers:
		Stop containers:

Access Frontend at http://<EC2_PUBLIC_IP>:80

CI/CD Deployment
	Add secrets in GitHub repository:
	EC2_SSH_KEY → Private key of EC2
	EC2_HOST → EC2 public IP
	EC2_USER → EC2 username (usually ubuntu)
	Workflow .github/workflows/deploy.yml triggers automatically on main branch push:
		ssh -i ~/.ssh/id_rsa ${{ secrets.EC2_USER }}@${{ secrets.EC2_HOST }} "bash /home/ubuntu/deploy.sh"

Push changes to main branch:
	git add .
	git commit -m "Trigger CI/CD workflow"
	git push origin main

GitHub Actions workflow will deploy the latest code to EC2.

Usage
	Frontend: http://<EC2_PUBLIC_IP>:80
	Backend (API): http://<EC2_PUBLIC_IP>:5000/api
	Nginx Reverse Proxy handles routing between Frontend and Backend.
		
