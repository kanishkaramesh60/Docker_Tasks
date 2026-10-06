\# Task 2 – CI/CD with Jenkins and Docker



\## 📌 Overview



This task demonstrates a \*\*CI/CD pipeline using Jenkins and Docker\*\*.



The Jenkins pipeline automatically builds a Docker image, tests the application, and deploys the container.



\---



\## 🛠️ Technologies Used



\- Jenkins

\- Docker

\- Dockerfile

\- Nginx

\- Git

\- GitHub



\---



\## 📂 Project Structure



```text

Task2/

├── app/

├── Dockerfile

├── Jenkinsfile

└── README.md

```



\---



\## 🔄 CI/CD Workflow



```text

Developer

&#x20;   │

&#x20;   │ Push Code

&#x20;   ▼

GitHub Repository

&#x20;   │

&#x20;   ▼

Jenkins

&#x20;   │

&#x20;   ├── Build

&#x20;   │     └── Build Docker Image

&#x20;   │

&#x20;   ├── Test

&#x20;   │     └── Test Nginx Configuration

&#x20;   │

&#x20;   └── Deploy

&#x20;         └── Run Docker Container

&#x20;                │

&#x20;                ▼

&#x20;         Application Running

```



\---



\## ⚙️ Jenkins Pipeline



The Jenkins pipeline is defined in:



```text

Jenkinsfile

```



The pipeline contains three stages:



\### 1. Build



Builds the Docker image using the Task2 Dockerfile.



```cmd

docker build -t jenkins-cicd-app Task2

```



\### 2. Test



Tests the Nginx configuration inside the Docker container.



```cmd

docker run --rm jenkins-cicd-app nginx -t

```



\### 3. Deploy



Stops the existing container, removes it, and starts a new container.



```cmd

docker stop jenkins-cicd-app-container || exit 0

docker rm jenkins-cicd-app-container || exit 0

docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app

```



\---



\## 🐳 Docker Configuration



\### Docker Image



```text

jenkins-cicd-app

```



\### Docker Container



```text

jenkins-cicd-app-container

```



\### Port Mapping



```text

8082:80

```



The application is available at:



```text

http://localhost:8082

```



\---



\## ▶️ Run Manually



\### Step 1 – Build the Docker Image



```cmd

docker build -t jenkins-cicd-app Task2

```



\### Step 2 – Test the Docker Image



```cmd

docker run --rm jenkins-cicd-app nginx -t

```



\### Step 3 – Run the Container



```cmd

docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app

```



\### Step 4 – Access the Application



Open:



```text

http://localhost:8082

```



\---



\## 🔧 Jenkins Configuration



Jenkins uses the `Jenkinsfile` located inside the `Task2` folder.



The pipeline follows:



```text

Build → Test → Deploy

```



\### Build



```text

Dockerfile → Docker Image

```



\### Test



```text

Docker Image → Nginx Configuration Test

```



\### Deploy



```text

Docker Image → Docker Container → Application

```



\---



\## 📋 Jenkinsfile



```groovy

pipeline {

&#x20;   agent any



&#x20;   stages {



&#x20;       stage('Build') {

&#x20;           steps {

&#x20;               bat 'docker build -t jenkins-cicd-app Task2'

&#x20;           }

&#x20;       }



&#x20;       stage('Test') {

&#x20;           steps {

&#x20;               bat 'docker run --rm jenkins-cicd-app nginx -t'

&#x20;           }

&#x20;       }



&#x20;       stage('Deploy') {

&#x20;           steps {

&#x20;               bat 'docker stop jenkins-cicd-app-container || exit 0'

&#x20;               bat 'docker rm jenkins-cicd-app-container || exit 0'

&#x20;               bat 'docker run -d --name jenkins-cicd-app-container -p 8082:80 jenkins-cicd-app'

&#x20;           }

&#x20;       }

&#x20;   }

}

```



\---



\## 🎯 Task 2 Objectives



\- Learn Jenkins pipeline configuration

\- Automate Docker image building

\- Test Dockerized applications

\- Automate container deployment

\- Understand CI/CD using Jenkins and Docker

\- Integrate Jenkins with a GitHub repository



\---



\## ✅ Result



The Task2 CI/CD pipeline successfully:



\- ✅ Builds the Docker image

\- ✅ Tests the Nginx configuration

\- ✅ Stops the previous container

\- ✅ Removes the previous container

\- ✅ Deploys a new Docker container

\- ✅ Makes the application available on port `8082`



\---



\## 🎯 Task Status



\*\*Task 2 CI/CD: Completed ✅\*\*

