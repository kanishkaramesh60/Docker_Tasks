# Task 2 – Jenkins CI/CD with Docker

## 📌 Overview

This task demonstrates the implementation of a **CI/CD pipeline using Jenkins and Docker**.

The pipeline automates the process of:

**Build → Test → Deploy**

Jenkins builds the Docker image, validates the Nginx configuration, and deploys the application as a Docker container.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Jenkins** | CI/CD automation |
| **Docker** | Application containerization |
| **Nginx** | Web server |
| **Git** | Version control |
| **GitHub** | Source code repository |

---

## 📂 Project Structure

```text
Task2/
│
├── app/
│
├── Dockerfile
│
├── Jenkinsfile
│
└── README.md
```

---

## 🔄 CI/CD Workflow

```text
                    ┌──────────────────┐
                    │    Developer     │
                    └────────┬─────────┘
                             │
                             │ Push Code
                             ▼
                    ┌──────────────────┐
                    │      GitHub      │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     Jenkins      │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌──────────┐   ┌──────────┐   ┌──────────┐
        │  Build   │ → │   Test   │ → │  Deploy  │
        └──────────┘   └──────────┘   └─────┬────┘
                                            │
                                            ▼
                                    ┌──────────────┐
                                    │    Docker    │
                                    │   Container  │
                                    └──────┬───────┘
                                           │
                                           ▼
                                  localhost:8082
```

---

## ⚙️ Jenkins Pipeline

The Jenkins pipeline is defined in the:

```text
Jenkinsfile
```

The pipeline consists of three stages.

### 1️⃣ Build

The Docker image is built using the Task2 Dockerfile.

```cmd
docker build -t jenkins-cicd-app Task2
```

**Output:**

```text
jenkins-cicd-app
```

---

### 2️⃣ Test

The Nginx configuration is tested inside the Docker container.

```cmd
docker run --rm jenkins-cicd-app nginx -t
```

This verifies that the Nginx configuration is valid before deployment.

---

### 3️⃣ Deploy

The existing container is stopped and removed before deploying a new container.

```cmd
docker stop jenkins-cicd-app-container || exit 0
docker rm jenkins-cicd-app-container || exit 0
docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app
```

The application is then available on:

```text
http://localhost:8082
```

---

## 🐳 Docker Configuration

### Docker Image

```text
jenkins-cicd-app
```

### Docker Container

```text
jenkins-cicd-app-container
```

### Port Mapping

```text
8082:80
```

| Host Port | Container Port | Purpose |
|---:|---:|---|
| 8082 | 80 | Nginx Web Server |

---

## ▶️ Run the Project Manually

### Build the Docker Image

Run from the repository root:

```cmd
docker build -t jenkins-cicd-app Task2
```

### Test the Image

```cmd
docker run --rm jenkins-cicd-app nginx -t
```

### Start the Container

```cmd
docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app
```

### Access the Application

Open your browser and visit:

```text
http://localhost:8082
```

---

## 📋 Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'docker build -t jenkins-cicd-app Task2'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run --rm jenkins-cicd-app nginx -t'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop jenkins-cicd-app-container || exit 0'
                bat 'docker rm jenkins-cicd-app-container || exit 0'
                bat 'docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app'
            }
        }
    }
}
```

---

## 🎯 Objectives

- Automate application deployment using Jenkins
- Build Docker images through a Jenkins pipeline
- Test the Dockerized Nginx application
- Automate Docker container deployment
- Understand Jenkins CI/CD pipeline stages
- Integrate Jenkins with GitHub
- Learn Docker-based application deployment

---

## ✅ Result

The Jenkins CI/CD pipeline successfully performs:

```text
Build
  ↓
Test
  ↓
Deploy
```

The application is successfully containerized using Docker and deployed through Jenkins.

### 🎉 Task 2 Completed

**Jenkins + Docker CI/CD Pipeline: ✅ Completed**