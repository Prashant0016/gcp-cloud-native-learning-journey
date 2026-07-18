# Task 4 – VPC Networking, Firewall Rules & Internal Communication

## Objective

Explore Google Cloud Virtual Private Cloud (VPC), understand cloud networking fundamentals, configure firewall rules, and learn how internal and external communication is controlled within a cloud environment.

## Real-World Scenario

An organization hosts multiple services within its cloud infrastructure:
- Frontend web servers
- Backend APIs
- Databases

To maintain security:
- The **Frontend** should be publicly accessible.
- The **Backend** should remain private.
- The **Database** should never be directly exposed to the Internet.

The objective of this lab is to understand how Google Cloud networking and firewall rules help secure communication between resources.

## Google Cloud Services Used
- Virtual Private Cloud (VPC)
- Subnets
- Firewall Rules
- Compute Engine
- Internal Networking

## Implementation Steps

### Step 1 – Explore the Default VPC

Navigate to: VPC Network → VPC Networks
Open the **default** VPC network and observe:
- Available subnets
- Regional distribution
- IP address ranges
- Associated firewall rules

### Step 2 – Create Two Virtual Machines

Navigate to: Compute Engine → VM Instances | Create two Ubuntu Virtual Machines within the same region. Example:
- frontend-vm
- backend-vm

Configure:
**Frontend VM**
- Allow HTTP Traffic
**Backend VM**
- Do **not** allow HTTP Traffic
This simulates a public-facing frontend and a private backend server.

### Step 3 – Explore Firewall Rules

Navigate to: VPC Network → Firewall | Review the default firewall rules created by Google Cloud and understand how they control network traffic.

### Step 4 – Test Internal Communication

Connect to the Frontend VM using SSH. Run: ping backend-vm | This verifies that internal communication between Virtual Machines within the same VPC is permitted by the default internal firewall rule.

## Sandbox Observation

> **Note:** Creating a Virtual Machine only provisions the infrastructure. A website or application will not be accessible until a service (such as NGINX) is installed and actively listening on the required network port. Similarly, allowing firewall traffic does not guarantee application availability—an application must also be running and configured to accept incoming requests.

## Key Concepts Learned

### Virtual Private Cloud (VPC)

A Virtual Private Cloud (VPC) is an isolated virtual network within Google Cloud that enables secure communication between cloud resources.
A VPC contains one or more **Subnets**, each responsible for managing a specific IP address range.

### Subnets

A subnet is a logical subdivision of a VPC network. Each subnet:
- Exists within a specific region
- Owns its own IP address range
- Hosts cloud resources such as Virtual Machines

### Default VPC

When a new Google Cloud project is created, Google automatically provides:
- A default VPC
- Default regional subnets
- Default firewall rules
The default network is useful for learning and development.
Production environments typically use custom VPCs designed around organizational security requirements.

### Firewall Rules

Firewall rules determine which network traffic is allowed to reach cloud resources. There are two primary traffic directions:

**Ingress**
Traffic entering a resource. Example: Browser --> Virtual Machine

**Egress**
Traffic leaving a resource. Example: Virtual Machine --> External API

### Default Firewall Rules

Some commonly provided firewall rules include:
| Firewall Rule | Purpose |
|---------------|---------|
| `default-allow-ssh` | Allows SSH access on Port 22 |
| `default-allow-http` | Allows HTTP traffic on Port 80 |
| `default-allow-internal` | Allows communication between resources inside the VPC |
Without properly configured firewall rules, cloud resources may either become inaccessible or unintentionally exposed to the public Internet.

### Internal vs External Communication

**Internal Communication**

Traffic exchanged between resources inside the same VPC using private IP addresses. Example:
Frontend VM --> Backend VM

**External Communication**

Traffic entering the cloud environment from the public Internet using external IP addresses. Example:
Internet User --> Frontend VM
Proper firewall configuration ensures that only the intended services are publicly accessible.

## Outcome

Successfully explored Google Cloud VPC networking, examined default firewall rules, created public and private Virtual Machines, and understood how internal and external communication is controlled using firewall policies.

## Skills Practiced

- Virtual Private Cloud (VPC)
- Subnets
- Firewall Rules
- Compute Engine Networking
- Internal \& External Communication
- Cloud Network Security

## Screenshots

*No screenshots available for this task.*

