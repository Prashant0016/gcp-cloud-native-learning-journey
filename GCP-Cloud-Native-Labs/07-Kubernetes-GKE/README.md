# Task 7 – Kubernetes Fundamentals, Google Kubernetes Engine (GKE) & Deploying Containers at Scale

## Objective

Deploy a containerized application on Google Kubernetes Engine (GKE), explore Kubernetes architecture, understand orchestration concepts, and learn how Kubernetes automatically manages application scaling and recovery.

## Real-World Scenario

As applications grow, organizations often manage:
- Hundreds of containers
- Multiple applications
- Increasing user traffic
- Unexpected container failures

Managing containers manually becomes impractical. Common challenges include:
- Containers crashing unexpectedly
- Sudden traffic spikes
- Virtual Machine failures
- Scaling applications to meet demand
Modern cloud-native applications solve these challenges using **Kubernetes**, which automates container orchestration and workload management.

## Google Cloud Services Used

- Google Kubernetes Engine (GKE)
- Kubernetes
- Cloud Shell
- kubectl
- Load Balancer

## Implementation Steps

### Step 1 – Create a Kubernetes Cluster

Navigate to: Kubernetes Engine
Enable the API if prompted.
Create a new **Autopilot Cluster**.
Once the cluster is ready, open **Cloud Shell**.

### Step 2 – Connect kubectl to the Cluster

Run: gcloud container clusters get-credentials my-first-gke-cluster --region asia-south1
This command configures `kubectl` to communicate with the newly created Kubernetes cluster.

### Step 3 – Verify Cluster Nodes

List the available worker nodes.
kubectl get nodes
Confirm that all nodes are in the **Ready** state.

### Step 4 – Deploy an Application

Create an NGINX deployment.
kubectl create deployment nginx-deployment --image=nginx

### Step 5 – Verify the Pods

View the running pods.
kubectl get pods
Confirm that the deployment has created a running pod.

### Step 6 – Test Self-Healing

Delete the running pod.
kubectl delete pod POD_NAME
Check the pod status again.
kubectl get pods
Observe that Kubernetes automatically creates a replacement pod to maintain the desired state.

### Step 7 – Scale the Deployment

Increase the number of replicas.
kubectl scale deployment nginx-deployment --replicas=3
Verify the deployment.
kubectl get pods
Three running pods should now be available.

### Step 8 – Expose the Deployment

Create a LoadBalancer service.
kubectl expose deployment nginx-deployment --type=LoadBalancer --port=80
View the available services.
kubectl get services
Once an External IP is assigned, open it in a web browser to access the deployed application.

## Sandbox Observation

> **Note:** Managed Kubernetes services such as Google Kubernetes Engine (GKE) automatically provision multiple underlying resources, including worker nodes, networking components, load balancing infrastructure, and orchestration services. In restricted sandbox environments, this increased infrastructure usage may trigger quota limits or anti-abuse protections. This behavior is expected and does not indicate an issue with the deployment.
> **Additional Observation:** Creating a Kubernetes cluster provisions significantly more infrastructure than creating a single Virtual Machine because Kubernetes must manage orchestration, networking, scheduling, scaling, and workload recovery across multiple nodes.

## Key Concepts Learned

### Kubernetes

Kubernetes is a container orchestration platform that automates the deployment, scaling, networking, and management of containerized applications.
While Docker packages applications into containers, Kubernetes manages those containers at scale.

### Why Kubernetes?

As applications grow, manually managing hundreds or thousands of containers becomes increasingly difficult.
Kubernetes automates tasks such as:
- Container scheduling
- Scaling
- Load balancing
- Networking
- Automatic recovery
- Rolling updates

### Google Kubernetes Engine (GKE)

Google Kubernetes Engine (GKE) is Google's managed Kubernetes service. Google manages:
- Control Plane
- Cluster upgrades
- Infrastructure management
Developers focus on deploying and managing their applications rather than maintaining Kubernetes itself.

### Kubernetes Cluster

A Kubernetes Cluster is a collection of machines working together to run containerized applications. A cluster consists of:
- Control Plane
- Worker Nodes

### Nodes

A Node is a Virtual Machine that runs Kubernetes workloads.
Worker Nodes host:
- Pods
- Containers
- Applications

### Pods

A Pod is the smallest deployable unit in Kubernetes. A Pod usually contains:
- One container
In some cases, multiple tightly coupled containers may run within the same Pod.
Kubernetes manages Pods rather than individual containers.

### kubectl

`kubectl` is the command-line interface used to interact with Kubernetes clusters. Common tasks include:
- Deploying applications
- Inspecting cluster resources
- Scaling workloads
- Managing Pods
- Troubleshooting deployments

### Declarative Infrastructure

Kubernetes follows a declarative approach. Instead of describing every individual step, you define the desired end state.
For example: Desired Replicas = 3
Kubernetes continuously works to ensure that three healthy Pods remain running.

### Deployments

A Deployment manages:
- Pods
- Replica count
- Updates
- Recovery
If a Pod fails, the Deployment automatically creates a replacement to maintain the desired state.

### Self-Healing

One of Kubernetes' core capabilities is self-healing. If a Pod crashes or is deleted, Kubernetes automatically recreates it without manual intervention.
This helps maintain application availability.

### Horizontal Scaling

Scaling a Deployment increases or decreases the number of running Pods. Example:
1 Pod --> Scale Deployment --> 3 Pods
This enables applications to handle increased workloads efficiently.

## Outcome

Successfully deployed a containerized application on Google Kubernetes Engine, explored Kubernetes architecture, verified automatic Pod recovery, scaled workloads using Deployments, and exposed the application using a LoadBalancer service.

## Skills Practiced

- Google Kubernetes Engine (GKE)
- Kubernetes
- kubectl
- Deployments
- Pods
- Load Balancing
- Scaling
- Container Orchestration

## Screenshots

*No screenshots available for this task.*

