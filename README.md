# Port-IDP-Demo

This repository contains a demo of how to setup an IDP using Port and Terraform or Crossplane. using github actions to run the automation.



## Project Structure

port-idp-demo/
├── .github/
│   └── workflows/
│       ├── build-and-deploy.yml
│       ├── crossplane-create-cluster.yaml
│       ├── manage-eks-cluster.yml
│       └── scaffold-app.yml
│
├── app-templates/
│   ├── nodejs/
│   │   ├── cookiecutter.json
│   │   └── {{cookiecutter.directory_name}}/
│   ├── python/           
│   ├── go/              
│   ├── java/            
│   └── README.md
│
├── crossplane/
│   ├── crossplane-config/
│   │   ├── provider-helm-incluster.yaml
│   │   └── provider-kubernetes-incluster.yaml
│   └── README.md
│
├── port/
│   ├── action/
│   │   ├── create_eks_cluster.json
│   │   ├── crossplane-cluster-create-action.json
│   │   ├── delete_eks_cluster.json
│   │   ├── deploy_to_eks_action.json
│   │   └── scaffold_an_app.json
│   └── blueprint/
│       ├── crossplane-cluster-blueprint.json
│       ├── eks_cluster.json
│       └── region.json
│
├── scripts/
│   └── crossplane-create-cluster.sh
│
├── terraform/
│   ├── main.tf
│   ├── outputs.tf
│   ├── terraform.tf
│   ├── variables.tf
│   └── README.md
│
├── .gitignore
└── README.md

## Future Improvements
- Add Jenkins Ci/CD pipeline for buuilding images and pushing to ECR or DockerHub
- 
