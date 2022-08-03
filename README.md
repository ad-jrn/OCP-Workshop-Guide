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

3. Afterwards, click on +Add and select `Container images`.

![Add > Container Images](https://user-images.githubusercontent.com/81570140/182545138-42847d19-72f7-4c0d-8bb2-fe98890090b8.png)

4. We will be deploying from a preloaded image from your environment's internal registry. From the dropdowns labeled Project/Image Stream:Tag, select `tools/aaa:latest`

![Deploy Settings](https://user-images.githubusercontent.com/81570140/182545551-3121b732-828e-4834-af37-b5b2c85d86fb.png)

5. Proceed with the default options and select `create`.

6. Switch back to Administrator view in the top left and select Deployments underneath Workloads. From here we can confirm that it has been successfully deployed and is running. We'll return to this later for HorizontalPodAutoScaling.

![Service Deployed](https://user-images.githubusercontent.com/81570140/182547205-bde24052-49ab-4963-99ec-b3037206d825.png)

## Self-Healing
Let's take a glance at some of our and see the tangible benefits of how OCP self heals.
1. Under `Workloads` select `Pods`. 

![Pods](https://user-images.githubusercontent.com/81570140/182551796-e0816b75-7164-4639-8bf8-267bab8c31c5.png)

2. Underneath the `Project:` dropdown menu, select `Tools`.

![Tools](https://user-images.githubusercontent.com/81570140/182552138-48aa7189-73b6-42ef-9d8b-0a72d1f9265f.png)

3. In the search bar, type in `nav`.

![Nav](https://user-images.githubusercontent.com/81570140/182552415-7cd54c46-2ac8-4c50-87b3-b6835ec3d001.png)

4. Select the Owner of one of these running Pods.

![Owner](https://user-images.githubusercontent.com/81570140/182552665-432b1e47-e506-47f5-9360-b1dce9f83a41.png)

5. Here we can view the ReplicaSet details that determine the current and desired states of our Pods.

![State](https://user-images.githubusercontent.com/81570140/182553049-6c331cc0-9922-4838-86bd-a6cc1f5a40e2.png)

6. Click on the `Pods` tab to view the running Pods.

![Pods](https://user-images.githubusercontent.com/81570140/182553267-e8bfe7d8-4bab-4a6f-a74c-1b7e1de9bace.png)

Here we will simulate what would happen if someone 'accidentally' deleted one of these pods.

7. Choose one of these pods and select `Delete Pod` from the three dot drop down menu.

![Oopsie](https://user-images.githubusercontent.com/81570140/182553829-364aa113-a24d-4a8b-93c2-98d15cb9c54c.png)

8. Select `Delete` and pay close attention to what happens.

![Oh no!](https://user-images.githubusercontent.com/81570140/182554102-38e011a8-3366-4d40-83d2-8cc0adb35102.png)

Immediately you'll see that as that pod is terminated, a new one is created to replace it. This is because OpenShift is constantly monitoring and realizes that the current state (1 Pod) does not match the desired state (2 Pods).














