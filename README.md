# Port-IDP-Demo

Create an EKS cluster with terraform and deploy a Node.js app
This guide, we are going to use self-service actions to demonstrate a workflow that does the following:

Creates an EKS Cluster.
Scaffolds a Node.js app that's automatically ingested as an entity by Port.
Deploys the app to the cluster.

## Prerequisites

1. Install Port's GitHub app by clicking here.
2. This guide assumes the presence of a blueprint representing your repositories. If you haven't done so yet, initiate the setup of your GitHub data model by referring to this guide first.
3. A repository to contain your action resources i.e. the github workflow file.
4. In your GitHub repository, go to Settings > Secrets and add the following secrets:
	AWS Credentials. Follow this guide to create them.
		AWS_ACCESS_KEY_ID: Your AWS access key.
		AWS_SECRET_ACCESS_KEY: Your AWS secret access key.
	CREATOR_TOKEN: A GitHub personal access token (fine-grained) that has Read and Write permissions on the following scopes: Administration, Contents.
	PORT_CLIENT_ID - Port Client ID learn more
	PORT_CLIENT_SECRET - Port Client Secret learn more
5. Your AWS account has access to an Elastic Container Registry or use DockerHub

## Folder Structure

app-templates: contains the cookiecutter templates for scaffolding apps.
terraform: contains the terraform configuration for creating an EKS cluster.
port: contains the port configuration for creating an EKS cluster.
crossplane: contains the crossplane configuration for creating an EKS cluster, RDS and more.

## Tools

Github Actions: 
    Build and Deploy Image to EKS
    Manage EKS Cluster (Create/Destroy)
    Scaffold Node.js App
Cookiecutter: used to scaffold the Node.js app.
Port: used to create the self-service action.
Terraform: used to create the EKS cluster.
Crossplane: used to create the RDS instance.
Jenkins: used to build the app and push to the DockerHub.
ArgoCD: used to deploy the app to the EKS cluster.


## Usage



## Future Improvements
