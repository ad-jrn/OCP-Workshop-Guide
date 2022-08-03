# OCP Workshop Guide

## Overview
Red Hat OpenShift Container Platform (OCP) is a cloud-based Kubernetes platform for developing and running containerized applications. It is designed for ease-of-use and flexibility for both developers and end-users. OCP enables organizations to build, deploy, and scale applications quickly both on-premises and in the cloud. All while protecting your infrastructure with enterprise-grade security. This produces a more simple access point to underlying infrastructure that can help manage application life cycle and development workflows.

Welcome to day three of our workshop. Today we will be highlighting five features of OCP:
- How to deploy a service
- Self-Healing
- Horizontal Pod Auto Scaling
- How to access the dashboard and CLI
- How to access log files

We will be using your environment that was prepared on [Day 2.](https://github.com/jmhossain/gitops-workshop-guide/blob/main/mq/README.md)

## Service Deployment from an Image

1. Navigate to your assigned IBM Cloud Environment. This will be listed in your TechZone invitation under Cluster URL. Afterwards, open the OpenShift Web Console in the upper righthand side of your Cluster.

![Cluster URL](https://user-images.githubusercontent.com/81570140/182544235-0e885a85-4090-4445-8525-9946e11bd705.png)

2. From the OCP Web Console, switch from Administrator to Developer view in the left dropdown menu.

![Swap to Developer mode](https://user-images.githubusercontent.com/81570140/182544822-dd8c431f-230b-40e0-94f6-08918c8be719.png)

3. Afterwards, click on +Add and select Container images.

![Add > Container Images](https://user-images.githubusercontent.com/81570140/182545138-42847d19-72f7-4c0d-8bb2-fe98890090b8.png)

4. We will be deploying from a preloaded image from your environment's internal registry. From the dropdowns labeled Project/Image Stream:Tag, select tools/aaa:latest

![Deploy Settings](https://user-images.githubusercontent.com/81570140/182545551-3121b732-828e-4834-af37-b5b2c85d86fb.png)

5. Proceed with the default options and select create.

6. Switch back to Administrator view in the top left and select Deployments underneath Workloads. From here we will be able to view our newly deployed service.

![Service Deployed](https://user-images.githubusercontent.com/81570140/182547205-bde24052-49ab-4963-99ec-b3037206d825.png)


