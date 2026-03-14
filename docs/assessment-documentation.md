# ShopNow Container Orchestration Assessment

## Project Overview
This assignment demonstrates deployment of the ShopNow MERN application using Kubernetes, Helm, and Jenkins.

## Kubernetes Deployment
Kubernetes deployment files were created separately for frontend and backend.

### Backend
- backend-deployment.yaml
- backend-service.yaml

### Frontend
- frontend-deployment.yaml
- frontend-service.yaml

## Helm Chart
A simple Helm chart was created inside helm/shopnow.

Files included:
- Chart.yaml
- values.yaml
- backend-deployment.yaml
- frontend-deployment.yaml

## Jenkins Pipeline
A Jenkinsfile was created to automate:
1. Repository clone
2. Docker image build
3. Kubernetes deployment

## Challenges Faced
- Understanding Kubernetes file structure
- Understanding Helm variables
- Writing basic Jenkins pipeline

## Solution
A simple structure was used to keep deployment files readable and easy to understand.