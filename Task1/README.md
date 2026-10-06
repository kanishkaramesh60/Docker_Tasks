\# Task 1 – Node.js CI/CD with Docker



\## 📌 Overview



This task demonstrates a basic \*\*CI/CD pipeline for a Node.js application\*\* using \*\*GitHub Actions and Docker\*\*.



The application is automatically tested, containerized, and pushed to Docker Hub whenever changes are made to the Task1 folder.



\## 🛠️ Technologies Used



\- Node.js

\- npm

\- Docker

\- Docker Hub

\- GitHub

\- GitHub Actions



\## 📂 Project Structure



```text

Task1/

├── app.js

├── Dockerfile

├── package.json

├── package-lock.json

└── README.md

```



\## 🔄 CI/CD Workflow



```text

Developer pushes code

&#x20;       ↓

GitHub Repository

&#x20;       ↓

GitHub Actions

&#x20;       ↓

Install Node.js dependencies

&#x20;       ↓

Check Node.js application

&#x20;       ↓

Build Docker image

&#x20;       ↓

Login to Docker Hub

&#x20;       ↓

Push Docker image

&#x20;       ↓

Docker Hub

```



\## ⚙️ GitHub Actions



The CI/CD workflow is located at:



```text

.github/workflows/task1.yml

```



The workflow is configured to run only when files inside `Task1/` are changed.



```yaml

paths:

&#x20; - 'Task1/\*\*'

```



\### Pipeline Stages



1\. Checkout the repository

2\. Setup Node.js

3\. Install dependencies using `npm install`

4\. Validate the Node.js application using `node --check`

5\. Build the Docker image

6\. Login to Docker Hub

7\. Push the Docker image to Docker Hub



\## 🐳 Docker



The application is containerized using the `Dockerfile`.



The Docker image is pushed to:



```text

kanishka63/docker:latest

```



\## ▶️ Run Locally



Clone the repository and navigate to Task1:



```cmd

git clone https://github.com/kanishkaramesh60/Devops\_Tasks.git

cd Devops\_Tasks\\Task1

```



Install dependencies:



```cmd

npm install

```



Run the application:



```cmd

node app.js

```



\## 🐳 Build and Run with Docker



Build the Docker image:



```cmd

docker build -t kanishka63/docker:latest .

```



Run the container:



```cmd

docker run -p 3000:3000 kanishka63/docker:latest

```



\## 🔐 GitHub Secrets



The GitHub Actions workflow uses the following repository secrets:



```text

DOCKER\_USERNAME

DOCKER\_PASSWORD

```



These credentials are used to authenticate with Docker Hub before pushing the image.



\## ✅ Result



The Task1 CI/CD pipeline successfully:



\- Validates the Node.js application

\- Builds the Docker image

\- Authenticates with Docker Hub

\- Pushes the image to Docker Hub automatically



\*\*Task 1 CI/CD: Completed ✅\*\*

