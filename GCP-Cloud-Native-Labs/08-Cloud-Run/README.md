# Task 8 – Cloud Run, Serverless Containers & Modern Application Deployment

## Objective

Deploy a containerized application using Google Cloud Run, understand serverless container platforms, and explore how modern cloud services simplify application deployment without requiring infrastructure management.

## Real-World Scenario

An organization wants to deploy containerized applications but does **not** want to manage:
- Virtual Machines
- Kubernetes clusters
- Worker nodes
- Infrastructure maintenance
- Scaling policies
- Operating system updates
Instead, the organization chooses **Google Cloud Run**, allowing developers to focus solely on their applications while Google Cloud manages the underlying infrastructure.

## Google Cloud Services Used

- Cloud Run
- Serverless Containers
- Container Images
- Google Cloud Platform

## Implementation Steps

### Step 1 – Open Cloud Run

Navigate to: Cloud Run
Enable the Cloud Run API if prompted.

### Step 2 – Create a New Service

Select: Deploy one revision from an existing container image

### Step 3 – Specify the Container Image

For the container image, enter: nginx
Cloud Run automatically retrieves the public NGINX container image, similar to pulling an image from Docker Hub.

### Step 4 – Configure the Service

Provide the following details:
- Service Name
- Deployment Region
- Allow Public Access
Click **Create** to deploy the service.

### Step 5 – Verify the Deployment

Once deployment is complete, Cloud Run provides a public service URL.
Open the URL in a web browser.
Expected result: The default **NGINX Welcome Page** should be displayed.

## Sandbox Observation

> **Note:** Cloud environments enforce quotas, limits, and governance policies to prevent excessive infrastructure provisioning and resource abuse. Although Cloud Run is a serverless platform, Google Cloud still provisions compute, memory, networking, and scaling resources behind the scenes. In managed sandbox environments, these underlying resources may be restricted, which can affect deployments despite the serverless experience.

## Key Concepts Learned

### Cloud Run

Google Cloud Run is a fully managed serverless platform for deploying containerized applications. Developers provide a container image, while Google Cloud automatically manages:
- Infrastructure
- Compute resources
- Networking
- Scaling
- High availability
This enables teams to focus on application development rather than infrastructure management.

### Serverless Computing

Serverless does **not** mean that servers do not exist. Instead, it means that the cloud provider manages the servers on behalf of the user.
Developers are responsible only for deploying their application, while infrastructure operations such as provisioning, scaling, maintenance, and patching are handled automatically.

### Why Organizations Choose Serverless

Many modern organizations adopt a serverless-first approach because it offers:
- Reduced operational overhead
- Automatic scaling
- Simplified deployments
- Lower infrastructure management effort
- Cost-efficient resource utilization

### Cloud Run vs Kubernetes

Both Cloud Run and Kubernetes run containerized applications, but they differ in the level of infrastructure management required.

**Kubernetes**

Developers manage:
- Clusters
- Worker Nodes
- Scaling configuration
- Networking
- Deployment strategies

**Cloud Run**

Developers simply deploy a container image. Google Cloud automatically manages:
- Infrastructure
- Scaling
- Networking
- Availability

### Revisions

Each deployment to Cloud Run creates a new **Revision**.
A Revision represents a snapshot of the deployed application at a specific point in time. Benefits include:
- Version tracking
- Rollback capability
- Traffic splitting between application versions

### Cold Starts

Cloud Run automatically scales services based on incoming traffic. When a service scales down to zero instances, the next incoming request may take slightly longer while a new container instance starts. This delay is known as a **Cold Start**. Cold starts are a normal characteristic of serverless platforms and help optimize resource usage when applications are idle.

## Outcome

Successfully deployed a containerized application using Google Cloud Run, explored serverless deployment concepts, and gained an understanding of how fully managed platforms simplify application hosting by eliminating infrastructure management responsibilities.

## Skills Practiced

- Google Cloud Run
- Serverless Computing
- Container Deployment
- Cloud-Native Architecture
- Application Deployment
- Managed Cloud Services

## Screenshots

*No screenshots available for this task.*

