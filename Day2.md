TODO: What about Linux versus Windows on AKS?

TOC
- [Agenda of Day2](#agenda-of-day2)
- [Introduction](#introduction)
- [General resources](#general-resources)
- [Challenges](#challenges)
  - [Challenge 1 - Containerizing application locally](#challenge-1---containerizing-application-locally)
  - [Challenge 2 - Continuous Integration with your containers](#challenge-2---continuous-integration-with-your-containers)
  - [Challenge 3 - Deploy to the Cloud, Azure Kubernetes Service (AKS)](#challenge-3---deploy-to-the-cloud--azure-kubernetes-service-aks)
  - [Challenge 4 - Persisting database workload](#challenge-4---persisting-database-workload)
  - [Challenge 5 - Routing traffic to multiple applications](#challenge-5---routing-traffic-to-multiple-applications)
  - [Challenge 6 - Monitoring and Logging using existing organizational tools](#challenge-6---monitoring-and-logging-using-existing-organizational-tools)
  - [Challenge 7 - Serverless Containers](#challenge-7---serverless-containers)

# Agenda of Day2

- 8:30am - Assigned Teams + Breakfast
- 9am - Kick-off
- 12pm - Lunch will be served while you will continue your challenges
- 3:30pm - General wrap up: each team sharing what they have done and learned

# Introduction

You are the R&D team for a startup that wants to investigate the technical viability of containerize an application and its database your are currently hosting on VMs.

As a Team, take one simple solution (web/api + database on containers ideally) and go through the process by doing your own research to resolve each challenge. Each challenge will lead you through a stage of the technical investigation as briefly laid out by your fictional CTO, these investigations become more technically challenging as you progress.

We do not provide guides, or instructions to solve the challenges, just a few hints and documentation references that you may find useful. There are multiple ways to solve each challenge, and very likely some we haven't thought of, so whilst we have some ideas of the most common solutions we're interested to see your own unique solutions to the problem.

# General resources

- [Day 1 resources](./README.md)
  - + [Advanced topics](https://github.com/Azure/blackbelt-aks-hackfest/tree/master/labs/day2-labs)
- [Designing Distributed Systems Labs by Brendan Burns](https://github.com/brendandburns/designing-distributed-systems-labs)
- [eShopOnContainers - Microservices Architecture and Containers based Reference Application](https://github.com/dotnet-architecture/eShopOnContainers)
- [Troubleshoot applications with Kubernetes](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/)

# Challenges

## Challenge 1 - Containerizing application locally

In this challenge you'll be taking an existing service/application that you will containerize, run it locally and ensure it works.

Your goal is to deploy the two different custom Docker images you should prepare:
1. web/api container: NodeJS, .NET Core, etc.
2. database container: MongoDB, SQL Server, etc.
Your web/api container should display the data coming from your database container.

**Success criteria:**
- Your team must demonstrate your chosen **v1.0 containers running on their local machine to a coach**.

Tips & Resources:
- Docker
- Draft?

## Challenge 2 - Continuous Integration with your containers

In this challenge you will push your containers on a private Azure Container Registry (ACR). You will then update your web/api container to push a v2.0 in your private ACR.

**Success criteria:**
- Your team must demonstrate:
  - **how you have built your containers and pushed them in your ACR**, could be manually, but maybe you would like to automate this?
  - **your v2.0 containers published in their private Azure Container Registry**

Tips & Resources:
- ACR CLI
- ACR Build?
- Brigade?
- Jenkins?
- VSTS?

## Challenge 3 - Deploy to the Cloud, Azure Kubernetes Service (AKS)

In this challenge you will deploy your containers stored in your private Azure Container Registry to your Azure Kubernetes Service (AKS) cluster. Furthermore, the goal is to deploy them in a different Kubernetes namespace than the `default` one.

**Success criteria:**
- Your team must demonstrate **your app/api and database containers are deployed in your AKS cluster in a different namespace than the default one and are up and running**, could be manually, but maybe you would like to automate this?

Tips & Resources:
- AKS CLI
- Kubernetes Namespaces
- Helm?

## Challenge 4 - Persisting database workload

In this challenge, you will fix an issue one of your team member raised regarding the data persisted on your database container. What's happening for the data if the associated `Pod` crashed, is updated? Give it a try! Just to `kubectl delete po/<your-database-pod-name>`.

How do you want to solve that?

**Success criteria:** 
- Your team must demonstrate: TODO

Tips & Resources:
- Kubernetes Volumes and PersistentVolumes
- OSBA?

## Challenge 5 - Routing traffic to multiple applications

In this challenge, you will implement one of your needs which is to route traffic depending on the URL path. For example `/my-url-v1` is going to one web/app container (v1.0) and `/my-url-v2` is going to another web/app container (v2.0), both hosted in your AKS cluster.

**Success criteria:**
- Your team must demonstrate: hitting `/my-url-v1` is going to your web/app container (v1.0) and `/my-url-v2` is going to your web/app container (v2.0), both hosted in your AKS cluster.

Tips & Resources:
- Kubernetes ConfigMaps and Secrets
- Kubernetes Ingress Controllers
- Azure Traffic Manager?

## Challenge 6 - Monitoring and Logging using existing organizational tools

In this challenge, you will configure tools to get more insights, logs, etc. to be able to monitor your infra, your nodes, your pods, your application, etc. You could use different tools but why not the one you are currently using?

**Success criteria:**
- Your team must demonstrate: **different information at different levels you are getting for a monitoring perspective**.

Tips & Resources:
- Prometheus/Grafana
- ELK?
- OMS/LogAnalytics?
- Splunk?

## Challenge 7 - Serverless Containers

Have you heard about the concept of Serverless Containers? To be able to accelerate your delivery process you are looking for the ability to on-demand scale node agents without waiting for VMs provisioning. You have heard that Azure Container Instances (ACI) could help on that. Let's host your web/api container there! And link it to your AKS cluster?!

**Success criteria:**
- Your team must demonstrate: how you could **leverage this Serverless Containers concepts within your AKS cluster with your we/api containers**.

Tips & Resources:
- ACI CLI
- Virtual Kubelet - ACI Connector
