# IDP Setup with Port and Terraform

## Overview
This guide demonstrates how to create a complete Infrastructure as Code (IaC) setup using Port and Terraform. The workflow includes:
- EKS cluster creation and management
- Automated Node.js application scaffolding with Port integration
- Containerized application deployment to EKS

## Prerequisites

### Required Accounts & Tools
1. [Port's GitHub App](https://docs.getport.io/build-your-software-catalog/sync-data-to-catalog/git/github/installation) installation
2. AWS Account with appropriate permissions
3. GitHub Repository access
4. Docker Registry access (ECR or DockerHub)

### Repository Configuration
#### GitHub Secrets Setup
Navigate to `Settings > Secrets` and configure the following:

**AWS Credentials**
- `AWS_ACCESS_KEY_ID`: AWS access key
- `AWS_SECRET_ACCESS_KEY`: AWS secret access key
- `AWS_REGION`: Target AWS region

**Authentication Tokens**
- `GH_TOKEN`: GitHub personal access token (Read/Write permissions for Administration, Contents)
- `PORT_CLIENT_ID`: Port Client ID ([Documentation](https://docs.getport.io/build-your-software-catalog/sync-data-to-catalog/git/github/installation))
- `PORT_CLIENT_SECRET`: Port Client Secret
- `TF_API_TOKEN`: Terraform API token for GitHub Actions

### Data Model Requirements
- Existing repository blueprint in Port
- If needed, follow our [GitHub data model setup guide](https://docs.getport.io/build-your-software-catalog/sync-data-to-catalog/git/github/installation)



## Technology Stack

### CI/CD & Infrastructure
- **GitHub Actions**
  - Container image building and EKS deployment
  - EKS cluster lifecycle management
  - Node.js application scaffolding
- **ArgoCD**
  - Kubernetes deployment management
  - GitOps workflow implementation

### Development & Configuration
- **Cookiecutter**: Application templating and scaffolding
- **Port**: Self-service action management
- **Terraform**: Infrastructure as Code for EKS

## Implementation Guide

### EKS Cluster Setup

#### Required Blueprints
1. Region Blueprint
2. EKS Cluster Blueprint

#### Action Configuration
1. Navigate to Port's self-service page
2. Select "+ New Action"
3. Access JSON editor via "{...}" button
4. Insert configuration JSON (provided separately)
5. Save configuration


TO be completed