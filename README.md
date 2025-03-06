# Port-IDP

This repository demonstrates how to set up an Internal Developer Portal (IDP) using Port and infrastructure as code tools (Terraform/Crossplane). The IDP automates infrastructure provisioning, application scaffolding and deployment through GitHub Actions workflows.

## Overview

The IDP provides:
- Application templating using Cookiecutter for multiple programming languages (Python, Node.js, Go, Java)
- Infrastructure provisioning using either Terraform or Crossplane
- GitOps-based deployments with ArgoCD
- Self-service developer portal powered by Port.io
- Automated workflows via GitHub Actions

## Prerequisites

Before getting started, ensure you have:

- An AWS Account with appropriate IAM permissions
- A Port account (sign up at getport.io)
- A GitHub account
- Terraform CLI (for Terraform-based provisioning)
- Crossplane CLI (for Crossplane-based provisioning)
- kubectl configured with a Kubernetes cluster (for ArgoCD deployments)

## Project Structure

```
.
├── .github/workflows/    # GitHub Actions workflow definitions
├── app-templates/       # Cookiecutter templates for different programming languages
│   ├── python/         # Python application template
│   ├── nodejs/         # Node.js application template
│   ├── go/            # Go application template
│   └── java/          # Java application template
├── argocd/            # ArgoCD application configurations
├── crossplane/        # Crossplane compositions and provider configurations
├── docs/             # Project documentation and images
├── port/             # Port IDP configurations
│   ├── action/       # Custom actions definitions
│   └── blueprint/    # Entity blueprints
├── scripts/          # Utility scripts
└── terraform/        # Terraform IaC configurations
```

## Getting Started

1. Clone this repository
2. Configure the required credentials:
   - AWS credentials
   - Port credentials
   - GitHub token
3. Follow the setup instructions in each component's README:
   - Port configuration: See ([Getting Started](https://docs.getport.io/quickstart))
   - Infrastructure setup: Choose either `terraform/README.md` or `crossplane/README.md`
   - Application templates: See `app-templates/README.md`

## Features

### Application Templates
- Multiple language support (Python, Node.js, Go, Java)
- Standardized project structure
- Built-in best practices and configurations

### Infrastructure Provisioning
- Choice between Terraform and Crossplane
- AWS infrastructure setup
- Automated provisioning through workflows

### Deployment
- GitOps-based deployment using ArgoCD
- Kubernetes manifest management
- Automated deployment pipelines

### Developer Portal
- Self-service capabilities through Port.io
- Custom actions for common developer tasks
- Infrastructure and application lifecycle management

## Future Improvements

- Add Jenkins CI/CD pipeline for building images and pushing to ECR or DockerHub
- Implement automated testing and security scanning in the CI/CD pipeline
- Add monitoring and observability setup
- Implement cost management and optimization features
- Add support for multiple cloud providers (GCP, Azure)
- Add service mesh integration
- Implement backup and disaster recovery solutions

## Contributing

Contributions are welcome! Please read our contributing guidelines before submitting pull requests.

## License

This project is licensed under the terms specified in the LICENSE file.
