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
- 9:30am - Work as teams to complete Kubernetes Challenges
- 12pm - Lunch will be served while you will continue your challenges
- 3:30pm - General wrap up: each team sharing what they have done and learned

# Introduction

You are part of the R&D team for your organization.  Your team has been tasked with investigating the technical viability of containerizing an existing application and its corresponding database that is currently running in a traditional VM environment.

As a Team, you will attempt to go through designing/architechting out a solution/process, by researching how to resolve each of the below challenges. Each challenge will lead you through a set of the technical investigations has been briefly laid out by your (fictional) CTO.  Each of these investigations are meant to solve an increasingly more technical challenging as you progress.

We do not provide guides, or instructions on how to solve the challenges, just a few hints/pointers to documentation and references that you *may* find useful. There are potentiall multiple solutions to each challenge and very likely some which haven't been thought of.  While there are common solutions to each challenge, we're primarily interested in seeing your own unique thought process and outcome to solve for each challenge.

# General resources

- [Day 1 resources](./README.md)
  - + [Advanced topics](https://github.com/Azure/blackbelt-aks-hackfest/tree/master/labs/day2-labs)
- [Designing Distributed Systems Labs by Brendan Burns](https://github.com/brendandburns/designing-distributed-systems-labs)
- [eShopOnContainers - Microservices Architecture and Containers based Reference Application](https://github.com/dotnet-architecture/eShopOnContainers)
- [Troubleshoot applications with Kubernetes](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/)

# Challenges

*General note: currently AKS only support Linux workload (Windows in Private preview as we speak). But if you would like to follow the Windows containers path, you could look at "ACS-Engine" or "Azure Container Instances (ACI) with VirtualKubelet". Up to you!*

## Challenge 1 - Containerizing application locally

In this challenge you'll be taking an existing service/application that you will containerize, run it in Docker locally and ensure it works first.

Your goal is to deploy the two different custom Docker images. You should prepare:
1. web/api container: NodeJS, .NET Core, etc. (whatever is in your heart)
2. database container: MongoDB, SQL Server, etc.
Your web/api container should use your database container as its underlying datastore i.e. they should be working together as part of an n-tier application and not simply deployed in isolation.

**Success criteria:**
Your team must demonstrate:
1. your chosen **v1.0 containers running on their local machine to a coach** 
2. prove the data is persisting between refreshes/sessions (i.e. data is being stored from your web/api container to your database container)

Tips & Resources:
- Docker

## Challenge 2 - Continuous Integration with your containers

In this challenge you will push (i.e. save) your custom Docker container(s) built locally, to a private Azure Container Registry (ACR) to share/deploy to your organization's container environment(s). You can/will then update your web/api code, rebuild the container and push it into ACR as as a v2.0/vNext .

**Success criteria:**
Your team must demonstrate:
1. **how you have built your containers and pushed them in your ACR**, could be a manual process, but wouldn't it be better to automate this???
2. **prove v2.0 containers are published into your Azure Container Registry**

Tips & Resources:
- Azure CLI (ACR sub-command)
- ACR Build?
- Brigade?
- Jenkins?
- VSTS?
- Git pre/post Hooks?

## Challenge 3 - Deploy to the Cloud, Azure Kubernetes Service (AKS)

In this challenge you will deploy your containers that are stored/saved in Azure Container Registry to your organization's Azure Kubernetes Service (AKS) cluster. Furthermore, the goal is to deploy them in a different Kubernetes namespace other than the `default` one.

**Success criteria:**
Your team must demonstrate:
1. **your app/api and database containers are deployed in your AKS cluster in a different namespace other than the "default" namespace***
2. **the app is up and running** i.e. can save/persist/display data just like before

Tips & Resources:
- Azure-CLI (AKS sub-command)
- Kubernetes Namespaces

## Challenge 4 - Persisting database workload

In this challenge, you will fix an issue that one of your team members have raised regarding the data persisted to your database. What's happening to the data if the associated `Pod` crashes (dies) or is updated? 

Live dangerously!!!! Give it a try!!! [devil emoji]

```:bash
  kubectl delete po/<your-database-pod-name>
```

How can you solve for this?

**Success criteria:** 
Your team must demonstrate:
1. **Deleting a database pod manually** and the pod being resurrected back to life...magically
2. **The data the original pod(s) saved** is still there...even though they were tragically murdered in cold digital bloooood

Tips & Resources:
- Kubernetes Volumes, Persistent Volumes, Persisten Volume Claims
- Replica Sets vs. Daemon Sets vs. ???
- OSBA - what is it and why could this be a better solution for persisting data?

## Challenge 5 - Routing traffic to multiple applications

In this challenge, you will implement a need/want from your CTO, which is to route traffic depending on the URL endpoint path. For example `/my-url-v1` is going to route to one web/app container version/instance/build (e.g. v1.0) and `/my-url-v2` is going to another web/app container version/instance/build (e.g. v2.0), which are both hosted in the same AKS cluster.

**Success criteria:**
Your team must demonstrate:
1. hitting `/my-url-v1` in a browser is going to your "first" web/app container (i.e. v1.0/vCurrent)
2. hitting `/my-url-v2` in a browser is going to your "second" web/app container (i.e. v2.0/vNext)
3. both are hosted in the same AKS cluster simultaneously

Tips & Resources:
- Kubernetes ConfigMaps and Secrets
- Kubernetes Ingress Controllers vs. Services
- Blue/Green, Red/Black deployments vs. A/B Testing vs. Rolling Updates
- Azure Traffic Manager?

## Challenge 6 - Monitoring and Logging using existing organizational tools

In this challenge, you will configure tools to get more insights, logs, etc. to be able to monitor your infrastructure, nodes, pods, application/services, etc. You could use new and different tooling for each but why can't you just keep using the tools that you already know and (likely) love?

**Success criteria:**
Your team must demonstrate: 
1. **different information/telemetry for different levels of monitoring granularity/perspectives**.

Tips & Resources:
- Prometheus/Grafana
- ELK?
- OMS/LogAnalytics?
- Splunk?
- DataDog?
- SysDig?

## Challenge 7 - Serverless Containers

Your CTO just heard from some cool kids, about this new concept of "Serverless Containers". To be able to handle random spikes in demand, your CTO wants you to look into the ability to (almost) instantly scale your services on-demand in seconds without waiting for VMs (agent nodes) to provision/join your cluster, which can take multiple minutes...which is now a virtual lifetime to wait for. 

You have heard from the same cool kids that Azure Container Instances (ACI) could help solve all your problems in life. Let's try to host your web/api containers there! But how can you link it to your AKS cluster?!

**Success criteria:**
Your team must demonstrate: 
1. how you could **leverage this Serverless Containers concepts within your AKS cluster with your we/api containers** and scale your app almost instantaneously
2. What are the downsides to this whole instant bursty container thingy?

Tips & Resources:
- Azure-CLI (ACI sub-command)
- Virtual Kubelet vs. ACI Connector??
