# Task 15 – Kubernetes Persistent Storage, Volumes & Stateful Data

## Objective

Learn how Kubernetes provides persistent storage for stateful applications using Persistent Volumes (PVs) and Persistent Volume Claims (PVCs), and understand how application data can survive Pod restarts.

## Real-World Scenario

Containers are **ephemeral**, meaning they can be stopped, deleted, or recreated at any time.
If an application stores data only inside the container's filesystem, that data is lost whenever the container is replaced.

Many production applications require persistent storage, including:
- Databases
- User-uploaded files
- Application logs
- Content management systems
- Shared application data

Kubernetes solves this problem by separating storage from the lifecycle of containers.

## Google Cloud Services Used

- Google Kubernetes Engine (GKE)
- Persistent Volumes (PV)
- Persistent Volume Claims (PVC)
- Cloud Shell
- kubectl

## Implementation Steps

### Step 1 – Create a Kubernetes Cluster

Navigate to: Kubernetes Engine | Create a new cluster using an **e2-small** machine configuration.

### Step 2 – Connect to the Cluster

Open **Cloud Shell** and connect `kubectl` to the cluster | gcloud container clusters get-credentials storage-cluster --region REGION

Replace `REGION` with your selected region.

Verify the cluster connection | kubectl get nodes

### Step 3 – Create a Persistent Volume Claim (PVC)

Create the PVC manifest | nano pvc.yaml

Paste the following configuration.
```
apiVersion: v1
kind: PersistentVolumeClaim

metadata: 
    name: nginx-pvc
spec: 
    accessModes: 
	- ReadWriteOnce
    resources: 
         requests: 
             storage: 1Gi
```

Save the file. 

Create the Persistent Volume Claim | kubectl apply -f pvc.yaml

Verify the PVC | kubectl get pvc

### Step 4 – Create the Deployment

Create the deployment manifest | nano deployment.yaml

Paste the following configuration.
```
apiVersion: apps/v1
kind: Deployment
metadata: 
    name: nginx-storage-demo
spec: 
    replicas: 1 
    selector: 
        matchLabels: 
             app: nginx-storage
template: 
    metadata: 
        labels: 
           app: nginx-storage
spec: 
    containers: 
        - name: nginx 
          image: nginx
volumeMounts: 
    - mountPath: "/usr/share/nginx/html/data" 
      name: storage-volume
volumes: 
   - name: storage-volume 
     persistentVolumeClaim: 
         claimName: nginx-pvc
```

Save the file. 

Deploy the application | kubectl apply -f deployment.yaml

Verify the Pod | kubectl get pods

### Step 5 – Test Persistent Storage

Access the running container | kubectl exec -it POD_NAME -- /bin/bash

Replace `POD_NAME` with your running Pod.

Create a file inside the mounted storage | echo "Persistent Kubernetes Storage" > /usr/share/nginx/html/data/test.txt

Verify the file | cat /usr/share/nginx/html/data/test.txt

Exit the container | exit

Delete the Pod to simulate a failure. After Kubernetes creates a replacement Pod, access it again | kubectl exec -it NEW_POD_NAME -- /bin/bash

Verify whether the file still exists | cat /usr/share/nginx/html/data/test.txt

If persistent storage is functioning correctly, the file remains available even after the original Pod has been deleted.

## Sandbox Observation

> **Persistent Volume Claims (PVCs)** using the **WaitForFirstConsumer** binding mode remain in a \*\*Pending\*\* state until a Pod that consumes the claim is scheduled. This allows Kubernetes to provision storage in the appropriate zone before binding the volume.

> During this lab, the sandbox environment restricted dynamic storage provisioning. As a result, the Persistent Volume Claim remained in the **Pending** state despite the cluster itself being healthy.

**Lab Status**

✅ Concept Understanding — Completed

✅ Cluster Validation — Completed

✅ PVC Troubleshooting — Completed

⚠️ Dynamic Storage Provisioning — Limited by sandbox environment

## Key Concepts Learned

### Stateful Applications

State refers to data that must persist beyond the lifetime of a container. Examples include:
- Database records
- Uploaded files
- Application logs
- User-generated content

Stateful applications require persistent storage to avoid data loss.

### Volumes

A Volume is storage mounted into a container. Unlike the container's internal filesystem, a Volume can persist independently of the container itself.
Volumes allow applications to retain data across container restarts.

### Persistent Volume (PV)

A Persistent Volume represents the actual storage resource within a Kubernetes cluster. Depending on the environment, it may map to:
- Google Persistent Disk
- Network File System (NFS)
- SSD storage
- Other cloud storage backends

### Persistent Volume Claim (PVC)

A Persistent Volume Claim is a request for storage made by an application. Rather than managing physical storage directly, applications request storage through PVCs, while Kubernetes handles the underlying storage provisioning.

### Dynamic Storage Provisioning

When a Persistent Volume Claim is created, Kubernetes can automatically provision the required storage if a compatible StorageClass is available. This abstraction separates storage consumption from storage implementation, allowing applications to remain portable across environments.

### Volume Mounts

The Deployment mounted the Persistent Volume Claim into the container at: /usr/share/nginx/html/data
Applications can read from and write to this directory while Kubernetes manages the underlying storage resource.

### Persistent Data

Writing data into the mounted Volume stores it outside the container's temporary filesystem. If the Pod is recreated, the replacement Pod can access the same persistent data.
This behavior is fundamental to running stateful workloads in Kubernetes.

### Stateless vs Stateful Applications

**Stateless Applications**

Examples:
- Frontend applications
- REST APIs
- Microservices

These applications can be restarted without losing important data.

**Stateful Applications**

Examples:
- Databases
- File storage systems
- Message queues

These workloads require durable, persistent storage to preserve application data across failures and restarts.

## Outcome

Successfully explored Kubernetes persistent storage concepts by creating a Persistent Volume Claim, mounting storage into a Deployment, understanding how persistent data survives Pod recreation, and troubleshooting storage provisioning behavior within a restricted sandbox environment.

## Skills Practiced

- Kubernetes
- Google Kubernetes Engine (GKE)
- Persistent Volumes (PV)
- Persistent Volume Claims (PVC)
- Volume Mounts
- Stateful Applications
- Storage Management
- kubectl

## Screenshots

*No screenshots available for this task.*

