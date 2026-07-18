# Task 10 – CI/CD Pipeline with Cloud Build & Automated Container Builds

## Objective

Understand Continuous Integration and Continuous Deployment (CI/CD) by creating a Cloud Build pipeline, triggering automated workflows, and exploring how cloud-native applications are built and deployed without manual intervention.

## Real-World Scenario

In modern software development, engineers do not manually:
- SSH into servers
- Build Docker images
- Deploy applications

Instead, organizations use **CI/CD pipelines** where code changes automatically trigger build and deployment workflows.

Typical workflow:
Developer Pushes Code -> Automatic Build -> Automated Testing -> Application Deployment. This approach reduces manual effort, improves consistency, and enables faster software delivery.

## Google Cloud Services Used

- Cloud Build
- Cloud Build Triggers
- Artifact Registry (Concept)
- YAML Build Configuration

## Implementation Steps

### Step 1 – Open Cloud Build

Navigate to: Cloud Build | Enable the API if prompted.

Open **Triggers** and select **Create Trigger**. Provide an appropriate trigger name and configuration.

### Step 2 – Choose the Trigger Type

Two approaches can be used.

#### Option A – GitHub Repository

If a GitHub repository is available:
1. Select **Push to Branch**.
2. Connect the GitHub repository.
3. Choose **Dockerfile** as the build configuration.
4. Keep the default Dockerfile location.
5. Select the Artifact Registry destination.
6. Create the trigger.

When code is pushed to the selected branch, Cloud Build automatically starts the pipeline.

#### Option B – Manual Invocation

If no GitHub repository is available:
1. Select **Manual Invocation**.
2. Choose **Inline** as the configuration type.
3. Paste the following YAML into the editor.

steps:
```
- name: 'gcr.io/cloud-builders/docker'
- args: ['version']
```  
If the build reports a logging-related error, update the configuration:
```
  options: 
     - logging: CLOUD_LOGGING_ONLY
```
     
This configures Cloud Build to write logs directly to Cloud Logging instead of using a custom storage bucket. Select an available service account, then create and run the trigger.

### Step 3 – Upgrade the Pipeline

Replace the previous YAML with the following example: steps:
```
- name: 'ubuntu'
- entrypoint: 'bash'
- args: 
     - '-c'
       - echo "Starting automated pipeline"
       - mkdir automation-demo
       - cd automation-demo
       - echo "Build completed successfully" > result.txt
       - cat result.txt
- options:
      - logging: CLOUD_LOGGING_ONLY
```

Run the trigger again. This workflow demonstrates a simple automated pipeline that creates a directory, writes a file, and prints its contents during the build process.

### Step 4 – View Build History

Navigate to: Cloud Build → History | If permissions allow, the build logs should display output similar to: Starting automated pipeline Build completed successfully

## Sandbox Observation

> **Note:** In the managed sandbox environment, Cloud Build execution completed, but viewing build logs was restricted because the service account lacked the required `logging.logEntries.create` permission. This IAM limitation is expected in restricted lab environments and does not necessarily indicate an issue with the pipeline configuration.

## Key Concepts Learned

### Continuous Integration (CI)

Continuous Integration (CI) is the practice of frequently merging code changes into a shared repository. Each code change automatically triggers validation processes such as:
- Building the application
- Running automated checks
- Detecting integration issues early

### Continuous Delivery / Continuous Deployment (CD)

Continuous Delivery and Continuous Deployment automate the release process. Instead of manually deploying software, applications are delivered through standardized and repeatable deployment pipelines.

### CI/CD Pipeline

A CI/CD pipeline is an automated sequence of tasks that builds, validates, and prepares software for deployment. Typical pipeline flow:
Source Code -> Build -> Test -> Deploy

Automation improves reliability, consistency, and deployment speed.

### Cloud Build

Cloud Build is Google Cloud's managed CI/CD service. It can be used to:
- Build container images
- Execute scripts
- Automate workflows
- Integrate with source repositories
- Deploy applications

### Build Triggers

A Trigger defines the event that starts a Cloud Build pipeline. Common trigger events include:
- Git Push
- Pull Request
- Tag Creation
- Manual Invocation
- API Requests

Triggers eliminate the need to start builds manually.

### Pipeline Workflow

When a build is triggered, Cloud Build performs a sequence of automated steps. For a Docker-based pipeline:
Provision Temporary Build Worker -> Download Source Code -> Read Dockerfile -> Build Container Image -> Push Image to Artifact Registry -> (Optional) Deploy Application

For the manual YAML demonstration: Provision Temporary Build Worker -> Execute Bash Script -> Create Directory -> Generate File -> Write Build Output -> Display Results in Logs -> Destroy Temporary Environment

### Temporary Build Workers

Cloud Build creates a temporary build environment for every pipeline execution. After the workflow completes:
- Build resources are automatically cleaned up.
- No build infrastructure needs to be managed manually.

### Immutable Deployment

Modern deployment strategies replace running application versions with newly built versions rather than modifying existing servers. This approach provides:
- Consistent deployments
- Easier rollbacks
- Predictable releases

### Build Artifacts

A Build Artifact is the output produced by a pipeline. Examples include:
- Docker Images
- Executable Files
- Deployment Packages

Artifacts are typically stored in repositories such as Artifact Registry.

### YAML

YAML is a human-readable configuration language widely used in cloud-native technologies. It is commonly used for:
- CI/CD Pipelines
- Kubernetes Manifests
- Infrastructure as Code
- DevOps Automation

## Outcome

Successfully created and executed Cloud Build pipelines, explored manual and trigger-based automation, understood the CI/CD workflow, and learned how automated build systems simplify application delivery in modern cloud environments.

## Skills Practiced

- Cloud Build
- CI/CD
- YAML
- Build Automation
- Cloud-Native Development
- DevOps Fundamentals
- Pipeline Design

## Screenshots

*No screenshots available for this task.*

