# Task 3 – Cloud Storage Static Website Hosting & Lifecycle Management

## Objective

Create a Google Cloud Storage bucket, host a static website, understand object accessibility, configure lifecycle management, and explore the fundamentals of object storage architecture.

## Real-World Scenario

An organization needs to host:
- Frontend websites
- Images
- PDF documents
- Static assets

Instead of managing Virtual Machines, operating systems, and web servers, the team chooses **Google Cloud Storage Static Website Hosting** to reduce operational overhead and infrastructure costs.
The objective of this lab is to deploy a static website using Cloud Storage and understand how Google Cloud manages object storage and access control.

## Google Cloud Services Used

- Cloud Storage
- Storage Buckets
- Object Storage
- Lifecycle Management
- IAM (Public Access)

## Implementation Steps

### Step 1 – Create a Storage Bucket

Navigate to: Cloud Storage → Buckets → Create. Configure the bucket:
- Provide a globally unique bucket name.
- Select the preferred Region.
- Choose an appropriate Storage Class.
- Set **Access Control** to **Uniform**.
- Disable **Public Access Prevention** (if permitted).
Click **Create**.

### Step 2 – Create a Static Website

Create a simple HTML file named: index.html. Add any sample HTML content to represent a basic static webpage.

### Step 3 – Upload the Website

Open the bucket. Upload the `index.html` file as an object.

### Step 4 – Configure Public Access

If permissions allow, make the uploaded object publicly accessible.
Copy the object's **Public URL** and open it in a web browser.
Expected result: The uploaded HTML page should be displayed.

### Step 5 – Configure a Lifecycle Rule

Navigate to: Bucket → Lifecycle → Add Rule. Configure the following rule:
- Condition: **Age = 30 Days**
- Action: **Set Storage Class to Nearline**
Save the lifecycle policy.

## Sandbox Observation

> **Note:** Cloud Storage objects are private by default. Public access requires the `storage.objects.get` permission (typically granted to `allUsers`). In the Pluralsight sandbox, IAM modifications may be restricted, resulting in **AccessDenied** errors even when Public Access Prevention is disabled. This is an expected limitation of the managed lab environment.

## Key Concepts Learned

### Cloud Storage Static Website Hosting

Unlike traditional web hosting, Cloud Storage can serve static website content directly without requiring a Virtual Machine or web server.
Architecture: User --> Cloud Storage Bucket --> Static Website Files
Benefits include:
- No server management
- Lower operational cost
- Highly scalable
- Fully managed by Google Cloud

### Object Storage

Cloud Storage uses an **Object Storage** architecture. Each stored object consists of:
- File data
- Metadata
- A unique identifier
Unlike traditional file systems, objects are stored independently within a bucket.

### Static vs Dynamic Websites

**Static Website**

Contains only client-side resources such as:
- HTML
- CSS
- JavaScript

Common use cases:
- Portfolio websites
- Landing pages
- Documentation sites
- React frontend builds

**Dynamic Website**

Requires server-side processing, such as:
- User authentication
- Database operations
- API requests
- Business logic
Dynamic applications are typically hosted using services such as Compute Engine, Cloud Run, Kubernetes, or App Engine.

### VM Hosting vs Cloud Storage Hosting

**Virtual Machine Hosting**
- Requires a running server
- Uses firewall rules (such as Port 80 for HTTP)
- NGINX serves website files
- Infrastructure must be managed

**Cloud Storage Hosting**
- No server required
- Objects are secured using IAM
- Google Cloud manages the underlying infrastructure
- Simpler and more cost-effective for static content


### Lifecycle Management

Lifecycle Management automatically transitions or deletes objects based on predefined conditions. Example:
After 30 days --> Move object from Standard Storage --> Nearline Storage
This helps optimize storage costs for infrequently accessed data.

## Outcome

Successfully created a Cloud Storage bucket, uploaded a static website, explored object accessibility, configured lifecycle management, and understood the architectural differences between traditional VM hosting and serverless static website hosting.

## Skills Practiced

- Cloud Storage
- Object Storage
- Static Website Hosting
- Lifecycle Management
- IAM-Based Object Access
- Storage Architecture


## Screenshots

*No screenshots available for this task.*