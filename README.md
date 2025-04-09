DevOps Internship Day - 2
Task -1

# 🚀 Jenkins CI/CD Pipeline App on AWS

This project demonstrates a complete CI/CD pipeline using **Jenkins**, **Docker**, and **GitHub**, running on an **AWS EC2 instance**.

---

## 📦 Tech Stack

- **Frontend / Backend**: Node.js App
- **CI/CD Tool**: Jenkins
- **Build & Deployment**: Docker
- **Cloud Host**: AWS EC2 (Ubuntu)
- **Git Repo**: [GitHub - Jenkins-cicd-pipeline-app](https://github.com/sultanashah/Jenkins-cicd-pipeline-app)

---
 Step 1: Launch Jenkins on AWS EC2
🧱 Minimum requirements:
- EC2 instance (Ubuntu 20.04 or Amazon Linux)
- Instance type: `t2.medium` or higher
- Inbound rules: open **port 8080** (Jenkins) and **port 3000** (App)
![image](https://github.com/user-attachments/assets/3c6342bc-7516-488a-8435-6066b2e959f0)


## 🔧 Pipeline Overview

The Jenkins pipeline is defined in a `Jenkinsfile` and includes the following stages:

1. **Checkout**: Pulls code from GitHub via SSH
2. **Build**: Builds a Docker image from the `Dockerfile`
3. **Test**: (Placeholder for future test scripts)
4. **Deploy**: Runs the app in a Docker container on port `3000`

---

## 📂 Jenkinsfile Structure

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Skipping test step for now'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop demo-app || true'
                sh 'docker rm demo-app || true'
                sh 'docker run -d --name demo-app -p 3000:3000 jenkins-demo-app'
            }
        }
    }
}

![image](https://github.com/user-attachments/assets/3fabeff0-e543-4941-8049-fb24bf9d35bb)

🐳## Dockerfile

FROM node:16
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
