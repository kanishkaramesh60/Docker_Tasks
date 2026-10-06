# Infrastructure as Code with Terraform

## Task 3: Provision a Local Docker Container Using Terraform

### Objective

The objective of this task is to understand **Infrastructure as Code (IaC)** by using Terraform to provision and manage a local Docker container.

### Tools Used

- Terraform v1.16.5
- Docker
- Docker Desktop
- Nginx
- Windows CMD

## Project Structure

```text
terraform-docker-task/
│
├── main.tf
├── README.md
├── execution-logs.txt
└── .gitignore
```

## Implementation

Terraform was configured with the Docker provider to create an Nginx Docker container.

The Terraform configuration performs the following:

1. Configures the Docker provider.
2. Pulls the `nginx:latest` Docker image.
3. Creates a Docker container named `terraform-nginx`.
4. Maps the container's port 80 to host port 8081.
5. Manages the container using Terraform state.

## Terraform Configuration

The `main.tf` file contains the Docker provider, Docker image, and Docker container resources.

```hcl
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = true
}

resource "docker_container" "nginx" {
  name  = "terraform-nginx"
  image = docker_image.nginx.image_id

  ports {
    internal = 80
    external = 8081
  }
}
```

## Execution Steps

### 1. Initialize Terraform

```cmd
terraform init
```

This initializes the Terraform working directory and downloads the required Docker provider.

### 2. Validate the Configuration

```cmd
terraform validate
```

This checks whether the Terraform configuration is syntactically valid.

### 3. Create an Execution Plan

```cmd
terraform plan
```

This displays the infrastructure changes Terraform plans to make without actually creating the resources.

### 4. Provision the Docker Container

```cmd
terraform apply
```

After reviewing the plan, `yes` was entered to create the Docker image and container.

### 5. Verify the Docker Container

```cmd
docker ps
```

The created container was:

```text
terraform-nginx
```

The Nginx application was accessed using:

```text
http://localhost:8081
```

### 6. Check Terraform State

```cmd
terraform state list
```

This displays the resources currently managed by Terraform.

```cmd
terraform show
```

This displays detailed information about the current Terraform-managed infrastructure.

### 7. Destroy the Infrastructure

```cmd
terraform destroy
```

The infrastructure was destroyed after completing the demonstration.

## Infrastructure Flow

```text
        Terraform
            |
            v
     Docker Provider
            |
            v
     Nginx Docker Image
            |
            v
     Docker Container
      terraform-nginx
            |
            v
   localhost:8081
```

## Terraform State

Terraform maintains a state file to keep track of the infrastructure it manages.

The state file allows Terraform to:

- Track created resources
- Compare the desired configuration with the current infrastructure
- Determine what changes are required
- Manage resources during apply and destroy operations

Terraform state files were excluded from the GitHub repository using `.gitignore`.

## Commands Used

```text
terraform init
terraform validate
terraform plan
terraform apply
terraform state list
terraform show
terraform destroy
docker ps
```

## Interview Questions and Answers

### 1. What is IaC?

Infrastructure as Code (IaC) is the practice of managing and provisioning infrastructure using configuration files instead of manually configuring resources.

### 2. How does Terraform work?

Terraform uses configuration files to define the desired infrastructure. It uses providers to communicate with platforms such as Docker, AWS, and Azure. Terraform compares the desired configuration with its current state and creates, modifies, or destroys resources as required.

### 3. What is a Terraform state file?

The Terraform state file stores information about the infrastructure managed by Terraform. It helps Terraform track resources and determine what changes need to be made.

### 4. Difference between `terraform plan` and `terraform apply`

`terraform plan` previews the changes Terraform intends to make.

`terraform apply` actually performs those changes and creates, updates, or destroys resources.

### 5. What are Terraform providers?

Providers are plugins that allow Terraform to communicate with external platforms and services.

Examples include:

- Docker
- AWS
- Azure
- Google Cloud

In this project, the **Docker provider** was used.

### 6. What is resource dependency?

Resource dependency means one Terraform resource depends on another resource.

For example, the Docker container depends on the Docker image:

```text
Docker Image
     ↓
Docker Container
```

Terraform automatically determines this dependency from the configuration.

### 7. How do you handle secret variables?

Secrets should not be hardcoded directly in Terraform configuration files.

They can be handled using:

- Terraform variables
- Environment variables
- `.tfvars` files excluded through `.gitignore`
- Secret management systems such as AWS Secrets Manager or HashiCorp Vault

### 8. What are the benefits of Terraform?

Major benefits include:

- Infrastructure automation
- Consistent infrastructure
- Version-controlled configuration
- Repeatable deployments
- Infrastructure planning before changes
- Easy resource creation and destruction
- Support for multiple cloud and infrastructure platforms

## Outcome

The task successfully demonstrated **Infrastructure as Code using Terraform** by provisioning, managing, verifying, and destroying a local Nginx Docker container.

The practical workflow was:

```text
terraform init
       ↓
terraform validate
       ↓
terraform plan
       ↓
terraform apply
       ↓
Docker Container
       ↓
terraform state
       ↓
terraform destroy
```

## Conclusion

This task provided hands-on experience with Terraform and demonstrated how Infrastructure as Code can be used to automate Docker infrastructure instead of managing containers manually.