# Task 2 – Create a Simple Jenkins Pipeline for CI/CD

## 📌 Objective

To set up a basic Jenkins CI/CD pipeline that automates the process of building, testing, and deploying an application using Jenkins and Docker.

This task demonstrates how Jenkins can automate application delivery through different pipeline stages.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Jenkins | CI/CD automation server |
| Docker | Containerization and application deployment |
| Git | Version control |
| GitHub | Source code repository |

---

## 📋 Task Description

The objective of this task is to create a Jenkins pipeline that automatically performs the following operations:

1. Build the Docker image
2. Test the application
3. Deploy the application using Docker

The pipeline is defined using a `Jenkinsfile`.

---

## 📁 Project Structure

```text
Docker_Tasks/
│
├── Task1/
│   └── ...
│
├── Task2/
│   ├── Dockerfile
│   ├── Jenkinsfile
│   └── README.md
│
├── Task3/
│   └── ...
│
└── Task4/
    └── ...
```

---

# 🔄 Jenkins CI/CD Pipeline

The pipeline follows this workflow:

```text
                 GitHub Repository
                        │
                        ▼
                   Jenkins
                        │
                        ▼
                  Build Stage
                        │
                        ▼
                   Test Stage
                        │
                        ▼
                  Deploy Stage
                        │
                        ▼
                Docker Container
                        │
                        ▼
              Application Running
```

---

# 🧩 Jenkinsfile

The Jenkins pipeline is defined using the `Jenkinsfile`.

The pipeline contains three main stages:

- Build
- Test
- Deploy

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

# 🔨 Pipeline Stages

## 1. Build Stage

The Build stage creates a Docker image from the application's Dockerfile.

```groovy
stage('Build') {
    steps {
        bat 'docker build -t jenkins-cicd-app Task2'
    }
}
```

### Purpose

The command:

```bash
docker build -t jenkins-cicd-app Task2
```

creates a Docker image named:

```text
jenkins-cicd-app
```

The `Task2` directory is used as the Docker build context because Jenkins checks out the complete repository.

---

## 2. Test Stage

The Test stage verifies that the Nginx configuration inside the Docker image is valid.

```groovy
stage('Test') {
    steps {
        bat 'docker run --rm jenkins-cicd-app nginx -t'
    }
}
```

The command:

```bash
docker run --rm jenkins-cicd-app nginx -t
```

runs the Docker image and executes:

```bash
nginx -t
```

The `nginx -t` command checks the Nginx configuration for errors.

If the test fails, the pipeline will stop and the deployment stage will not execute.

---

## 3. Deploy Stage

The Deploy stage runs the Docker container.

```groovy
stage('Deploy') {
    steps {
        bat 'docker stop jenkins-cicd-app-container || exit 0'
        bat 'docker rm jenkins-cicd-app-container || exit 0'
        bat 'docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app'
    }
}
```

Before starting the new container, Jenkins attempts to stop and remove any previous container with the same name.

Then the new container is started using:

```bash
docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app
```

---

# 🌐 Application Access

After successful deployment, the application can be accessed through:

```text
http://localhost:8082
```

The port mapping is:

```text
Host Port 8082
      │
      ▼
Container Port 80
```

Diagram:

```text
Browser
   │
   │ http://localhost:8082
   ▼
Host Machine
   │
   │ Port 8082
   ▼
Docker Container
   │
   │ Port 80
   ▼
Nginx Web Server
```

---

# ⚙️ Jenkins Configuration

The Jenkins pipeline can be configured using a **Pipeline** job.

### Basic configuration

1. Open Jenkins.
2. Create a new Jenkins job.
3. Select **Pipeline**.
4. Configure the GitHub repository.
5. Select the pipeline definition from the repository.
6. Specify the Jenkinsfile path.
7. Save the configuration.
8. Build the pipeline.

The Jenkinsfile is stored inside:

```text
Task2/Jenkinsfile
```

---

# 🔗 GitHub Integration

The project source code is stored in GitHub.

The basic workflow is:

```text
Developer
    │
    ▼
Git Commit
    │
    ▼
GitHub Repository
    │
    ▼
Jenkins
    │
    ▼
Build
    │
    ▼
Test
    │
    ▼
Deploy
```

Jenkins can be configured to automatically trigger a build whenever changes are pushed to the repository.

---

# 🐳 Docker Integration

Docker is used to package the application into a container.

The Jenkins pipeline uses Docker commands to:

- Build the image
- Run tests
- Stop the previous container
- Remove the previous container
- Start a new container

Docker image:

```text
jenkins-cicd-app
```

Docker container:

```text
jenkins-cicd-app-container
```

Application port:

```text
8082
```

---

# 🔁 Complete CI/CD Workflow

```text
                    GitHub
                       │
                       ▼
                    Jenkins
                       │
                       ▼
              ┌─────────────────┐
              │  Build Stage    │
              │ Docker Build    │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │  Test Stage     │
              │   Nginx Test    │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │  Deploy Stage   │
              │ Docker Run      │
              └────────┬────────┘
                       │
                       ▼
                Running Container
                       │
                       ▼
              http://localhost:8082
```

---

# 📚 Important Jenkins Concepts

## Continuous Integration

Continuous Integration (CI) is the practice of frequently integrating code changes into a shared repository and automatically building and testing the application.

---

## Continuous Delivery

Continuous Delivery ensures that application changes are automatically prepared for deployment after passing the required tests.

---

## Continuous Deployment

Continuous Deployment automatically deploys successfully tested changes to the target environment.

In this task, Jenkins automatically deploys the Docker container after the Build and Test stages succeed.

---

# 📝 Jenkinsfile

A `Jenkinsfile` is a text file that defines the Jenkins pipeline as code.

Example:

```text
Task2/
│
├── Dockerfile
├── Jenkinsfile
└── README.md
```

Keeping the Jenkinsfile inside the repository allows the pipeline configuration to be version controlled along with the application code.

---

# 🎓 Interview Questions and Answers

## 1. What is Jenkins, and how is it used in CI/CD?

Jenkins is an open-source automation server used to automate software development processes.

It is commonly used in CI/CD pipelines to:

- Build applications
- Run automated tests
- Create Docker images
- Deploy applications
- Automate repetitive development tasks

A typical Jenkins workflow is:

```text
Code Commit
     │
     ▼
   Jenkins
     │
     ▼
   Build
     │
     ▼
    Test
     │
     ▼
   Deploy
```

---

## 2. What is a Jenkinsfile?

A Jenkinsfile is a text file that defines the Jenkins pipeline as code.

It describes:

- Pipeline configuration
- Stages
- Steps
- Build commands
- Test commands
- Deployment commands

Example:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application'
            }
        }
    }
}
```

The Jenkinsfile can be stored in the project's Git repository.

---

## 3. How do you create and configure Jenkins pipelines?

The basic process is:

1. Install and start Jenkins.
2. Open the Jenkins dashboard.
3. Create a new Pipeline job.
4. Connect the job to the Git repository.
5. Specify the Jenkinsfile.
6. Save the configuration.
7. Run the pipeline.
8. Monitor the pipeline stages.

The pipeline can also be configured to automatically trigger when new code is pushed to GitHub.

---

## 4. What are some common stages in a Jenkins pipeline?

Common Jenkins pipeline stages include:

### Build

Compiles or packages the application.

### Test

Runs automated tests to verify the application.

### Deploy

Deploys the application to the target environment.

Example:

```text
Build
  │
  ▼
Test
  │
  ▼
Deploy
```

In this task, the pipeline contains:

```text
Build → Test → Deploy
```

---

## 5. What is the difference between a declarative and scripted Jenkins pipeline?

### Declarative Pipeline

A Declarative Pipeline follows a predefined and structured syntax.

Example:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build'
            }
        }
    }
}
```

It is easier to read and commonly recommended for beginners.

### Scripted Pipeline

A Scripted Pipeline provides more programming flexibility and uses Groovy scripting.

Example:

```groovy
node {
    stage('Build') {
        echo 'Build'
    }
}
```

### Difference

| Declarative Pipeline | Scripted Pipeline |
|---|---|
| Structured syntax | Flexible Groovy scripting |
| Easier to read | More programming control |
| Easier for beginners | Useful for complex logic |
| Uses `pipeline {}` | Uses `node {}` |

The pipeline used in this task is a **Declarative Pipeline**.

---

# 💡 Additional Interview Questions

## 6. What is a Jenkins agent?

A Jenkins agent is a machine or environment where Jenkins executes pipeline tasks.

The agent performs operations such as:

- Building applications
- Running tests
- Executing Docker commands
- Deploying applications

---

## 7. What is a Jenkins stage?

A stage is a logical section of a Jenkins pipeline.

Examples:

```text
Build
Test
Deploy
```

Stages make the pipeline easier to understand and monitor.

---

## 8. What is a Jenkins step?

A step is an individual operation performed inside a stage.

For example:

```groovy
steps {
    echo 'Building application'
}
```

Here, `echo` is a pipeline step.

---

## 9. What happens if the Test stage fails?

If a stage fails, Jenkins normally marks the pipeline as failed and stops subsequent stages.

For example:

```text
Build
  │
  ▼
Test ❌
  │
  X
Deploy
```

Therefore, the application will not be deployed if the required test stage fails.

---

## 10. Why is Docker used with Jenkins?

Docker provides a consistent environment for building, testing, and deploying applications.

Using Docker with Jenkins helps:

- Package applications
- Create reproducible environments
- Reduce environment-related issues
- Simplify deployment
- Automate container management

---

# 📦 Task Deliverables

The following deliverables were completed:

- Jenkins pipeline
- `Jenkinsfile`
- Docker integration
- Build stage
- Test stage
- Deploy stage
- GitHub repository integration
- Docker container deployment
- README documentation

---

# 🧪 Testing the Pipeline

The Jenkins pipeline was tested by running the job from the Jenkins dashboard.

The expected pipeline execution is:

```text
Build       ✅
   │
   ▼
Test        ✅
   │
   ▼
Deploy      ✅
```

After successful deployment, the Docker container runs the application on:

```text
http://localhost:8082
```

---

# 🎯 Expected Outcome

After completing this task, the following concepts are understood:

- Jenkins
- CI/CD
- Jenkins pipelines
- Jenkinsfile
- Declarative pipelines
- Pipeline stages
- Pipeline steps
- Docker integration
- Automated testing
- Automated deployment
- GitHub integration

---

# 🚀 Real-World CI/CD Flow

A real-world Jenkins CI/CD pipeline can be represented as:

```text
Developer
    │
    ▼
GitHub
    │
    ▼
Jenkins
    │
    ├───────────────┐
    ▼               │
Build               │
    │               │
    ▼               │
Test                │
    │               │
    ▼               │
Docker Build        │
    │               │
    ▼               │
Docker Registry     │
    │               │
    ▼               │
Deployment ◄────────┘
    │
    ▼
Production
```

---

# 📌 Key Commands Used

### Build Docker Image

```bash
docker build -t jenkins-cicd-app Task2
```

### Test Docker Image

```bash
docker run --rm jenkins-cicd-app nginx -t
```

### Stop Existing Container

```bash
docker stop jenkins-cicd-app-container
```

### Remove Existing Container

```bash
docker rm jenkins-cicd-app-container
```

### Run Docker Container

```bash
docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app
```

---

# 📖 Task Information

**Task:** Task 2 – Create a Simple Jenkins Pipeline for CI/CD

**Objective:**  
Set up a basic Jenkins pipeline to automate the process of building and deploying an application.

**Tools:**

- Jenkins
- Docker
- Git
- GitHub

**Pipeline Stages:**

```text
Build → Test → Deploy
```

---

# 🎉 Conclusion

This task demonstrated how Jenkins can be used to automate a basic CI/CD pipeline.

A Jenkinsfile was created with separate Build, Test, and Deploy stages. Docker was integrated into the pipeline to build the application image, test it, and deploy it as a running container.

This provides practical experience with Jenkins pipeline automation and demonstrates the basic principles of CI/CD.

---

## ✅ Task 2 Completed

**Simple Jenkins Pipeline for CI/CD**