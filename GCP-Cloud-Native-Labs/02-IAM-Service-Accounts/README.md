# Task 2 – Enterprise IAM & Access Management

## Objective

Explore Google Cloud Identity and Access Management (IAM), understand role-based access control, create a Service Account, and learn how cloud resources are secured using the Principle of Least Privilege.

## Real-World Scenario

As part of a Cloud Engineering team, different users require different levels of access to cloud resources. For example:

- Developers deploy and manage applications.
- DevOps Engineers manage infrastructure.
- Security teams audit permissions.
- Interns require read-only access.
- Applications securely access Google Cloud services using Service Accounts.

The goal of this lab is to understand how IAM manages identities and permissions across an organization.

## Google Cloud Services Used

- IAM & Admin
- IAM Roles
- Service Accounts
- Compute Engine (Service Account Attachment)

## Implementation Steps

### Step 1 – Explore IAM

Navigate to: IAM & Admin → IAM | 
Review the members and roles currently assigned within the project.

### Step 2 – Explore Predefined Roles

Navigate to: IAM & Admin → Roles | 
Search for: Compute Admin | 
Review the permissions included within this predefined role to understand how Google groups related permissions into reusable roles.

### Step 3 – Create a Service Account

Navigate to: IAM & Admin → Service Accounts. Create a new Service Account by providing:
- Name
- Description

Proceed through the wizard and assign an appropriate role if permissions allow.

### Step 4 – Attach the Service Account (If Applicable)

When creating or editing a Compute Engine Virtual Machine, a Service Account can be attached to allow the VM to securely access Google Cloud services without storing user credentials.

## Sandbox Observation

> **Note:** In the Pluralsight Hands-on Playground, certain IAM operations (such as assigning additional roles to Service Accounts) are restricted due to limited permissions in the managed lab environment. These restrictions are expected and do not indicate a configuration error.

## Key Concepts Learned

### Identity and Access Management (IAM)

IAM controls **who** can access Google Cloud resources and **what actions** they are permitted to perform.
IAM answers three fundamental questions:
- Who are you?
- What resources can you access?
- What actions are you allowed to perform?

### Authentication vs Authorization

**Authentication** verifies your identity.
Examples:
- Password
- One-Time Password (OTP)
- Fingerprint
- Security Key

**Authorization** determines what actions you are allowed to perform after your identity has been verified.
Examples:
- View resources
- Create Virtual Machines
- Delete Storage Buckets

### Roles

A role is a collection of permissions. Instead of assigning hundreds of individual permissions such as:
- compute.instances.create 
- compute.instances.delete  
- compute.instances.start  

Google combines them into predefined roles such as: Compute Admin

Types of IAM Roles include:
- Basic Roles (Owner, Editor, Viewer)
- Predefined Roles (Compute Admin, Storage Admin, Kubernetes Engine Admin, etc.)
- Custom Roles

### IAM Binding

An IAM Binding connects a Principal to a Role. | Structure: Principal + Role = Access

Example: john@company.com + Compute Viewer = Can view Compute Engine Virtual Machines


### Principal

A Principal is any identity that can be granted access to Google Cloud resources.
Common Principal types include:

| Principal Type | Example |
|----------------|---------|
| User | max@example.com |
| Group | dev-team@example.com |
| Service Account | backend-app@project.iam.gserviceaccount.com |

### Service Accounts

A Service Account represents an application or service instead of a human user.
Rather than using passwords, applications authenticate using Service Accounts to securely access Google Cloud resources.

Common use cases include:
- Virtual Machines accessing Cloud Storage
- Applications writing logs
- Kubernetes workloads connecting to databases
- Cloud services communicating securely with one another

## Outcome

Successfully explored Google Cloud IAM, examined predefined roles, created a Service Account, and gained an understanding of identity management, authorization, role-based access control, and secure application authentication.

## Skills Practiced

- Identity and Access Management (IAM)
- Role-Based Access Control (RBAC)
- Service Accounts
- Principle of Least Privilege
- Authentication \& Authorization
- Google Cloud Security

## Screenshots

*No screenshots available for this task.*

