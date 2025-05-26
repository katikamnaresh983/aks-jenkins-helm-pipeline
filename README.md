# AKS CI/CD Pipeline with Jenkins and Helm

Build and deploy a Python Flask app to Azure Kubernetes Service using Jenkins and Helm.

## Technologies Used
- Jenkins
- Docker
- Helm
- Kubernetes (AKS)
- Python (Flask)

## How It Works
1. Jenkins clones the repo
2. Builds Docker image
3. Pushes image to DockerHub
4. Deploys to AKS using Helm
