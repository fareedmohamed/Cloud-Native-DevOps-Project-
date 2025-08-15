# Cloud-Native-DevOps-Project-
![Cloud-Native-DevOps-Project](https://github.com/fareedmohamed/Cloud-Native-DevOps-Project-/blob/792a4d9f29c073b1c0db7abb67407bea3f246224/68747470733a2f2f696d6775722e636f6d2f63703663776c582e706e67.jpeg)

# 🚀 Full-Stack DevOps Project

This repository contains a full-stack application deployment using modern DevOps practices and cloud-native technologies.  
The project demonstrates the implementation of **Infrastructure as Code (IaC)**, containerization, orchestration, and continuous integration/deployment (**CI/CD**) pipelines.

---

## 📋 Project Overview

This project implements a complete DevOps lifecycle for a cloud-native application with:

- 🛠️ Infrastructure automation using **Terraform**  
- ☸️ Container orchestration with **Kubernetes (EKS)**  
- 🔄 CI/CD implementation using **Jenkins**  
- 📦 Artifact management with **Nexus**  
- 🧪 Code quality with **SonarQube**  
- 🛡️ Security scanning with **CodeQL** and **Veracode**  
- 📊 Monitoring and observability  

---

## 🏗️ Infrastructure as Code - Terraform

The infrastructure is completely automated using **Terraform** with **state management** and **locking** enabled through **AWS S3**.

### **📡 VPC Architecture**
- 🌐 **Public Subnet**: Hosts Bastion Host, VPN, and ALB (Ingress Controller)  
- 🔒 **Private Subnet**: Houses EKS Cluster  
- 🗄️ **DB Subnet**: Contains RDS (MySQL)  
- 📏 CIDR blocks segmented per subnet  
- 🌉 NAT Gateway for private subnet internet access  
- 🌍 Internet Gateway for public subnet  

### **🛠️ Additional AWS Services**
- 📛 **Route53** for DNS management  
- 🌎 **CloudFront CDN** for static content delivery  
- 💾 **EFS** for persistent storage  
- 🐳 **Amazon ECR** for container registry  
- 📦 **S3 Buckets** for artifacts & Terraform state  
- 🔐 **KMS** for encryption key management  

**Terraform Structure**
terraform/
├── 00-vpc/ # VPC and networking
├── 10-sg/ # Security Groups
├── 20-bastion/ # Bastion Host
├── 30-db/ # RDS Database
├── 40-eks/ # EKS Cluster
├── 50-acm/ # SSL Certificates
├── 60-ingress-alb/ # ALB Ingress
└── 70-ecr/ # Container Registry


---

## ☸️ Kubernetes Architecture - EKS

Our application runs on **Amazon EKS** with:

### **⚙️ Cluster Configuration**
- Version: **1.24+**  
- Node Groups: mix of on-demand & spot instances  
- Auto-scaling: **2-10 nodes**  
- Multi-AZ for high availability  

### **📡 Traffic Flow**
- AWS ALB as entry point  
- Ingress Controller with:
  - URL path-based routing  
  - SSL termination  
  - Rate limiting  

### **🛠️ Application Management**
- Deployments with rolling updates  
- ConfigMaps for environment configs  
- Secrets for credentials  
- Helm Charts for packaging & versioning  
- EFS for persistent volumes  

**Helm Chart Structure**
helm/
├── Chart.yaml
├── values.yaml
└── templates/
├── deployment.yaml
├── service.yaml
├── ingress.yaml
├── configmap.yaml
├── secret.yaml
└── hpa.yaml

---

## 🔄 CI/CD Pipeline - Jenkins

The CI/CD pipeline is implemented using **Jenkins**, triggered by **GitHub Webhooks**.

### **Pipeline Features**
- Multi-branch pipeline  
- Shared libraries for common functions  
- Parallel execution  
- Timeout & retry mechanisms  
- Slack/Email notifications  

### **Pipeline Stages**
1. **Build Initialization**: dependencies, checkout, environment validation  
2. **Code Quality**: SonarQube, unit & integration tests  
3. **Infrastructure**: Terraform plan/apply, security group checks  
4. **Containerization**: Docker multi-stage builds, ECR push, scanning  
5. **Deployment**: Helm validation, rolling deploy, smoke tests, rollback  

---

## 📊 Monitoring & Security

### **📈 Monitoring Stack**
- Prometheus + Grafana dashboards  
- ELK Stack for logging  
- Alerts via PagerDuty, Slack, Email  

### **🛡️ Security**
- SonarQube Quality Gates  
- CodeQL & Veracode scans  
- Container & dependency scanning  
- HTTPS, WAF rules, rate limiting  
- Secrets management & IAM policies  

---

## 📝 Contributing
1. Fork the repository  
2. Create feature branch  
3. Commit changes  
4. Push branch  
5. Open Pull Request  

