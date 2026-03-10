#  Secure CI/CD Pipeline with Role-Based Access and Environment Promotion Strategy

## 📌 Project Overview

This project demonstrates the implementation of a **Secure CI/CD Pipeline** using **Jenkins, GitHub, and AWS EC2** with **Role-Based Access Control (RBAC)** and **Environment Promotion Strategy (Dev → Staging → Production).**

In many organizations, developers often have direct access to production deployments, which creates **security risks and deployment issues**.  
This project solves that problem by introducing **controlled deployments, approval workflows, and environment isolation**.

---

# 🎯 Objective

Design and implement a **secure CI/CD pipeline** with:

- Role-Based Access Control
- Multi-stage deployment pipeline
- Manual approval before production deployment
- Environment isolation
- Automated build and testing

---

# 🧰 Technologies Used

| Technology | Purpose |
|------------|--------|
| GitHub | Source Code Management |
| Jenkins | CI/CD Pipeline Automation |
| AWS EC2 | Hosting environments |
| IAM | Access control |
| Terraform | Infrastructure provisioning |
| Linux | Server environment |

---

# 🏗 Architecture Diagram

![](/image/architecturee%20digram.png)

Pipeline Flow:

Build → Unit Test → Deploy Dev → Deploy Staging → Approval → Production


---

# ⚙️ CI/CD Pipeline Stages

The Jenkins pipeline consists of the following stages:

### 1️⃣ Clone Repository

Source code is cloned from **GitHub**.

### 2️⃣ Build Stage

The application build process is executed.

### 3️⃣ Unit Test

Basic testing is performed to verify the application.

### 4️⃣ Deploy to DEV

Application is deployed to the **Development Environment**.

### 5️⃣ Deploy to STAGING

Application is promoted to the **Staging Environment**.

### 6️⃣ Manual Approval

Admin approval is required before production deployment.

### 7️⃣ Deploy to PRODUCTION

After approval, the application is deployed to the **Production Server**.

---

# 🔐 Role-Based Access Control (RBAC)

Jenkins roles are configured to control deployment permissions.

| Role | Permissions |
|-----|-------------|
| Developer | Can trigger builds and deploy to Dev/Staging |
| Admin | Can approve and deploy to Production |

### Security Improvements

- Developers **cannot deploy directly to production**
- Production deployment requires **manual approval**
- Controlled environment promotion

---

# 🌍 Environment Setup

Three separate **AWS EC2 instances** are used.

| Environment | Purpose |
|-------------|--------|
| Dev Server | Development and testing |
| Staging Server | Pre-production testing |
| Production Server | Live application |
```

### Example Server Configuration
DEV_SERVER = 3.110.121.192
STAGING_SERVER = 13.235.48.179
PROD_SERVER = 13.201.192.68

```

---

# 📸 Project Screenshots

## Jenkins Pipeline Execution

![Pipeline Build](/image/build.png)

---

## Successful Deployment

![Deployment Success](/image/build%20sucess%20op.png)

---

## AWS EC2 Instances

![EC2 Instances](/image/ec2%20server.png)

---

## Jenkinsfile Pipeline Code

![Jenkinsfile](/image/jenkinfile.png)

---

## Terraform Infrastructure Code

![Terraform Code](/image/main.tf.png)

---
## Webhook in Gihub

![](/image/webhook.png)

# 📂 Project Structure
```
Secure-CI-CD-Pipeline
│
├── Jenkinsfile
├── main.tf
├── index.html
├── README.md
│
└── images
├── build.png
├── build-success.png
├── ec2-server.png
├── jenkinsfile.png
└── main-tf.png

```

---

# 🚀 Deployment Workflow
```

Developer Push Code → GitHub

        ↓

Jenkins Pipeline Trigger

        ↓

Build Application

        ↓

Run Unit Tests

        ↓

Deploy to Dev Environment

        ↓

Promote to Staging

        ↓

Manual Approval Required

        ↓

Deploy to Production
```

---

# 🔒 Security Improvements

✔ Role-Based Access Control in Jenkins  
✔ Manual approval before production deployment  
✔ Separate environments for Dev, Staging, and Production  
✔ Controlled deployment pipeline  
✔ Infrastructure automation using Terraform

---

# 📈 Future Improvements

- Add **SonarQube for code quality scanning**
- Add **Docker containerization**
- Add **Kubernetes deployment**
- Add **Security scanning tools (Trivy)**

---

# 👨‍💻 Author

**Vaibhav Navnath Bhuse**

DevOps & Cloud Engineer

GitHub:  
https://github.com/vaibhavbhuse42