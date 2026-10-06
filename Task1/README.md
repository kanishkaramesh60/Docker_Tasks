# Task 1 – Node.js CI/CD with Docker

## 📌 Overview

This task demonstrates a basic **CI/CD pipeline for a Node.js application** using **GitHub Actions and Docker**.

The application is automatically tested, containerized, and pushed to Docker Hub whenever changes are made to the `Task1` folder.

## 🛠️ Technologies Used

- Node.js
- npm
- Docker
- Docker Hub
- GitHub
- GitHub Actions

## 📂 Project Structure

```text
Task1/
├── app.js
├── Dockerfile
├── package.json
├── package-lock.json
└── README.md
```

## 🔄 CI/CD Workflow

```text
Developer pushes code
        ↓
GitHub Repository
        ↓
GitHub Actions
        ↓
Install Node.js dependencies
        ↓
Check Node.js application
        ↓
Build Docker image
        ↓
Login to Docker Hub
        ↓
Push Docker image
        ↓
Docker Hub
```

## ⚙️ GitHub Actions

The CI/CD workflow is located at:

```text
.github/workflows/task1.yml
```

The workflow is configured to run only when files inside the `Task1/` folder are changed.

```yaml
paths:
  - 'Task1/**'
```

### Pipeline Stages

1. **Checkout Repository**
2. **Setup Node.js**
3. **Install Dependencies**
4. **Validate Node.js Application**
5. **Build Docker Image**
6. **Login to Docker Hub**
7. **Push Docker Image**

The Node.js application is validated using:

```cmd
node --check app.js
```

## 🐳 Docker

The application is containerized using the `Dockerfile`.

The Docker image is pushed to:

```text
kanishka63/docker:latest
```

## ▶️ Run Locally

Clone the repository:

```cmd
git clone https://github.com/kanishkaramesh60/Devops_Tasks.git
```

Navigate to Task1:

```cmd
cd Devops_Tasks\Task1
```

Install dependencies:

```cmd
npm install
```

Run the application:

```cmd
node app.js
```

## 🐳 Build and Run with Docker

Build the Docker image:

```cmd
docker build -t kanishka63/docker:latest .
```

Run the Docker container:

```cmd
docker run -p 3000:3000 kanishka63/docker:latest
```

## 🔐 GitHub Secrets

The GitHub Actions workflow uses the following repository secrets:

```text
DOCKER_USERNAME
DOCKER_PASSWORD
```

These credentials are used to authenticate with Docker Hub before pushing the Docker image.

> **Note:** The Docker Hub password should be stored as a GitHub Secret or Docker Hub Personal Access Token. Never hard-code credentials in the workflow.

## ✅ Result

The Task1 CI/CD pipeline successfully:

- ✅ Validates the Node.js application
- ✅ Builds the Docker image
- ✅ Authenticates with Docker Hub
- ✅ Pushes the Docker image to Docker Hub automatically

### 🎯 Task 1 Status

**Task 1 CI/CD: Completed ✅**