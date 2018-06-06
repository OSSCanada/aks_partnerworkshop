This 2 days workshop is for helping Canadian Partners get up to speed with Docker, Kubernetes and Azure Kubernetes Service (AKS).

## PREREQUISITES
 
As part of this workshop, please plan to bring a laptop with you that has one of the following OS, or access to a VM with the OS on it:
- Windows 10 with Windows Subsystem for Linux installed
- MacOS with Homebrew installed
- Linux distribution such as Ubuntu or CentOS

In addition to the OS, please ensure the following tools need are setup/configured for the best workshop experience:
- [Docker CE](https://docs.docker.com/install/)
- [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Helm](https://github.com/kubernetes/helm)

Finally, to access the labs, you’ll need a Microsoft Azure subscription. You will host and provision all the Azure services you’ll need for the labs and challenges into it.

## Day 1

You need to have installed at least [Docker](https://docs.docker.com/install/) on your local machine (Windows, macOS or Linux) which will be named throughout the labs below as "jumpbox" or "local machine".

- *Introduction of the day*
- Presentations: **Cloud Native applications, Microservices, Containers and Docker**
- *(Optional - needs NodeJS and mongoimport installed)* Lab1 - [Run app locally to test components](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/01-setup-app-local.md)
- Lab2 - [Create Docker images for apps and push to Azure Container Registry](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/02-dockerize-apps.md)
- Wrap up
- Presentations: **Orchestrator, Kubernetes overview, Azure Kubernetes Service (AKS)**
- Lab3 - [Create an Azure Kubernetes Service (AKS) cluster](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/03-create-aks-cluster.md)
- Lab4 - [Deploy application to Azure Kubernetes Service](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/04-deploy-app-aks.md)
- Lab5 - [Kubernetes UI Overview](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/05-kubernetes-ui.md)
- Wrap up
- Presentations: **Kubernetes concepts, ACI, ACR, Operations and Management concepts, Scaling**
- Lab6 - [Operational Monitoring and Log Management](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/06-monitoring-k8s.md)
- Lab7 - [Application and Infrastructure Scaling](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/07-cluster-scaling.md)
- Wrap up
- Presentations: **Storage and State, Open Service Broker, Upgrading**
- Lab8 - [Moving your data services to Azure PaaS (CosmosDB)](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/08-migrate-mongo-to-cosmos.md)
- Lab9 - [Update and Deploy New Version of Application](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/09-update-application.md)
- Lab10 - [Upgrade an Azure Kubernetes Service (AKS) cluster](https://github.com/Azure/blackbelt-aks-hackfest/blob/master/labs/day1-labs/10-cluster-upgrading.md)
- Wrap up
- **Wrap up of the day + Q&A**
