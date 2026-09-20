# 🚀 DevOps 3-Tier Application Deployment

### An end-to-end DevOps project demonstrating containerization, CI/CD automation, Kubernetes deployment, and Infrastructure as Code using Docker, Jenkins, Kubernetes, Terraform, and AWS.

### The project uses a lightweight Python Flask application and automates the application delivery workflow from source code checkout to Docker image build, application health testing, and Kubernetes deployment.

## 🛠️ Technologies Used

### ->Git & GitHub – Source code management
### ->Jenkins – CI/CD automation
### ->Docker – Application containerization
### ->Kubernetes – Container orchestration and deployment
### ->Terraform – Infrastructure as Code
### ->WS – Infrastructure provisioning practice
### ->Python / Flask – Sample application
### ->kubectl – Kubernetes management


## 📂 Project Structure

### devops-3-tier-project/ │ ├── app/ │ ├── app.py │ ├── requirements.txt │ └── Dockerfile │ ├── kubernetes/ │ ├── deployment.yaml │ └── service.yaml │ ├── terraform/ │ └── Infrastructure as Code configuration │ ├── Jenkinsfile └── README.md


## 🔄 CI/CD Pipeline

### The Jenkins pipeline performs the following stages:

## 1. Checkout
### Jenkins checks out the latest application code from the main branch of GitHub.

## 2. Build Docker Image 
### The Flask application is containerized using Docker.

## 3. Test Application
### ->Jenkins starts the newly built container and verifies the application's health endpoint.
### docker run -d --name devops-test -p 5001:5000 devops-flask-app:latest

### ->The health check is performed using:
### curl -f http://host.docker.internal:5001/health

### A successful response confirms that the application is running correctly.

## 4. Deploy to Kubernetes
### Jenkins applies the Kubernetes manifests:

### ->kubectl apply -f kubernetes/deployment.yaml
### ->kubectl apply -f kubernetes/service.yaml
### ->The deployment is then restarted and monitored:
### ->kubectl rollout restart deployment/devops-app
### ->kubectl rollout status deployment/devops-app --timeout=120s
### ->Finally, Jenkins displays the running Kubernetes pods.

## ☸️ Kubernetes

### The application is deployed using:

### ->Kubernetes Deployment
### ->Kubernetes Service
### ->2 application replicas
### ->Application health endpoint
### ->Rolling deployment verification

### The Kubernetes deployment was tested successfully on a local Docker Desktop Kubernetes cluster.
### Useful commands:

### ->kubectl get pods
### ->kubectl get deployment
### ->kubectl get services
### ->kubectl rollout history deployment/devops-app


## 🐳 Docker

### The application is packaged into a Docker image:

### ->devops-flask-app:latest
### ->The Docker image contains:
### ->Python 3.12
### ->Flask
### ->Application dependencies
### ->Flask application code

## 🏗️ Terraform

### ->Terraform configuration is included to demonstrate Infrastructure as Code and AWS infrastructure provisioning.
### ->The Terraform configuration includes AWS networking resources such as a VPC and subnets.

### ->Typical Terraform workflow:
### terraform init
### terraform plan
### terraform apply

### Note: The CI/CD application deployment demonstrated in this project uses the local Docker Desktop Kubernetes cluster. The Terraform configuration is included separately as Infrastructure as Code practice and is not required for the local Jenkins-to-Kubernetes deployment.

## 🧪 Application Health Check

### The Flask application exposes a health endpoint:

### /health
### Expected response:
### {
###  "status": "healthy"
### }

### This endpoint is used by the Jenkins pipeline to verify that the Dockerized application is responding before continuing to Kubernetes deployment.

## ✅ Pipeline Result

### The final CI/CD workflow was successfully tested:

### GitHub
  ### ↓
### Jenkins
  ### ↓
### Docker Image Build
  ### ↓
### Application Health Test
  ### ↓
### Kubernetes Deployment
  ### ↓
### Kubernetes Rollout Verification

## 🎯 Key DevOps Concepts Demonstrated

### ->CI/CD pipeline implementation
### ->GitHub source control integration
### ->Jenkins declarative pipeline
### ->Docker containerization
### ->Docker-to-Jenkins integration
### ->Kubernetes Deployments and Services
### ->Kubernetes rolling rollout
### ->Application health testing
### ->Infrastructure as Code with Terraform
### ->Basic troubleshooting of Docker and Kubernetes connectivity
### ->Automated deployment workflow

## 🔧 Troubleshooting Experience

### During implementation, the following issues were resolved:

### ->Jenkins initially could not access the Docker daemon
### ->Docker socket access was configured for Jenkins
### ->Docker CLI was installed in the Jenkins container
### ->Jenkins Docker socket permissions were configured
### ->Container-to-host connectivity was handled using host.docker.internal
### ->Jenkins Kubernetes connectivity was configured using a dedicated kubeconfig
### ->Kubernetes TLS hostname mismatch was resolved for the local Jenkins environment
### ->Kubernetes rollout was explicitly triggered for the rebuilt latest image

## 📌 Future Improvements

### Possible future enhancements include:

### ->Push Docker images to Docker Hub or Amazon ECR
### ->Deploy to Amazon EKS instead of a local Kubernetes cluster
### ->Add Kubernetes ConfigMaps and Secrets
### ->Add automated image tagging using Git commit IDs
### ->Add security scanning with Trivy
### ->Add monitoring using Prometheus and Grafana
### ->Add Jenkins webhook-based automatic builds
### ->Add separate staging and production environments

## 👩‍💻 Project Objective

### This project was built as a hands-on DevOps learning project to understand how source code moves through a CI/CD pipeline and is packaged, tested, and deployed using industry-standard DevOps tools.
