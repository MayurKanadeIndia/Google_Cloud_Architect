# Google Cloud Core Services (High Level Overview)

### Google divides the services into the following logical groups

![alt text](images/GCP_Core_services_01.PNG)

# 1. Computing and Hosting Services

- Depending on the user requirements and flexibility the cloud architect choose the services as follows.

  ![alt text](images/GCP_Core_services_02.PNG)

- GKE On-Prem is a GKE service that can be installed on your local environment and managed from your Google Console.
- Cloud Run is an FaaS offering that allows you to define containers that will listen for HTTP requests. This allows you to use languages that are not supported by Cloud Functions.
- Fully managed container platform: Cloud Run

## How to choose right resource?

- It depends upon several factors, for example
  - do we need full control over our infrastructure?
  - do we want fully managed service?

![alt text](images/Right_Resource.PNG)

### The computing options in GCP is shown as follows:

![alt text](images/Computing_Options.png)

Lets look into details of each:

### 1. GCE (Google Compute Engine) (IaaS):

- GCE is an IaaS offering. It allows the most flexibility as it provides compute infrastructure to provision VM instances.
- This means that you have control of the virtualized hardware and operating system.
- Note, this can be limited to available machine types. You can use standard GCP images or your own custom image.
- You can control where your VMs and storage are located in terms of regions and zones.
- You have granular control over the network, including firewalls and load balancing.
- With the use of an instance group, you can autoscale your control and your capacity as needed.
- Compute Engine is suitable in most cases but might not be an optimal solution.

![alt text](images/GCE_Controls.PNG)

### 2. GKE (Google Kubernetes Engine) (CaaS):

- It allows you to create Kubernetes clusters on demand, which takes away all of the heavy lifting of installing the clusters yourself.
- It leverages Compute Engine for hosting the cluster nodes, but the customer does not need to bother with the infrastructure and can concentrate on writing the code.
- The provisioned cluster can be automatically updated and scaled.
- The GCP software-defined networks are integrated with GKE and allow users to create network objects, such as load balancers, on demand when the application is deployed.
- Several services integrate with GKE, such as Artifact Registry, which allows you to store and scan your container images.

![alt text](images/GKE_Control.PNG)

### 3. App Engine (PaaS):

- It allows you to concentrate on writing your code, while Google takes care of hosting, scaling, monitoring, and updates.
- It is targeted at developers who do not need to understand the complexity of the infrastructure.
- GAE is tightly integrated with GCP services, including databases and storage. It allows versioning of your application for easy rollouts and rollbacks.

![alt text](images/GAE_Environments.PNG)

### 4. Cloud Functions (FaaS):

- It allows you to concentrate on writing your functions in one of the supported languages.
- It is ideal for executing simple tasks for data processing, mobile backends, and IoT.
- This service is completely serverless and all of the layers below it are managed by Google.
- The functions can be executed using an event trigger or HTTP endpoint.

### 5. Cloud Run (FaaS):

- Brings together the simplicity of FaaS and portability of CaaS.
- It allows you to develop and deploy self-scaling containerized applications on a fully managed serverless platform.
- It is compatible with Knative so you can move your workloads to any environment that can run Kubernetes in the cloud or on-premises.

### 6. Anthos

- Anthos is a modern application management platform that provides a consistent development and operations experience for cloud and on-premises environments.
- Anthos is not a compute option itself but allows you to run Google Kubernetes Engine and Cloud Run on Anthos in multi-cloud and hybrid environments.

### 7. Google Cloud VMWare Engine (GCVE):

- It is a fully managed native VMware Cloud Foundation software stack hosted in GCP.
- It allows you to accelerate the move to GCP by lifting and shifting your VMs hosted on vSphere into Google Cloud as is.

---

# Google Cloud Storage Services.

- Storage is an essential part of cloud computing as it saves the data and state of your applications.
- GCP offers a wide variety of storage, from object storage to managed databases.

![alt text](images/Cloud_Storage_Options.PNG)

### 1. Cloud Storage (Fully Managed, Object oriented storage):

- It has virtually infinite capacity.
- It allows the creation of buckets that store your data and allow access through APIs and tools such as gsutil.
- It has different storage classes and price differs for each tier.
- Making a conscious decision will allow you to cut costs.
- With Cloud Storage, you do not need to worry about running out of capacity.

![alt text](images/Cloud_Storage_Buckets.PNG)

### 2. Cloud Filestore (Managed file storage service)

- It allows users to provision a Network Attached Storage (NAS) service that can be integrated with GCE and GKE.
- Google Cloud Filestore offers several performance tiers, including Basic, High Scale, Zonal, and Enterprise/Regional.
- Each designed for different workloads and requirements, from economical file sharing to high-performance computing and mission-critical applications.
- These tiers vary in capacity, performance (like IOPS and throughput), and availability, with options for both HDD and SSD storage to balance cost and speed.

![alt text](images/Cloud_Filestore.PNG)

### 3. Cloud SQL (Fully-managed RDBMS)

- Cloud SQL is a fully-managed relational database service for either a MySQL, PostgreSQL, or SQL Server database.
- It offers data replication, backups, data exports, and monitoring.
- It is ideal when you need to move your current instances from on-premises and want to delegate the maintenance of the database to Google.

![alt text](images/Cloud_SQL_Offerings.PNG)

### 4. Cloud Datastore (Fully managed, NoSQL database)

- It is ideal for applications that rely on highly available structured data at scale.
- The scaling and high availability are achieved with a distributed architecture and are abstracted from the user.
- There is only one database available per project.
- Cloud Datastore offers SQL-like language to query your data. It has been superseded by Cloud Firestore.

### 5. Cloud Firestore (Next Gen Cloud Datastore):

- It can run in Native or Datastore mode.
- Google has already started moving all Datastore clients to Cloud Firestore without any downtime or any user intervention.
- All new projects should be created in Cloud Firestore instead of Datastore.

### 6. Cloud Spanner (Fully managed, globally distributed database service)

- It offers the strong consistency of a relational database with non-relational database scaling capabilities.
- Users can define a schema and leverage industry-standard American National Standards Institute (ANSI) 2011 SQL.
- It delivers high-performance transactions, with a 99.999% availability Service-Level Agreement (SLA), meaning there is almost no downtime.
- Cloud Spanner is aimed at use cases such as financial trading, insurance, global call centers, telecoms, gaming, and e-commerce.
- Global consistency makes it ideal for globally accessible applications.

![alt text](images/Cloud_Spanner_Offerings.PNG)

### 7. Bigtable (Fully managed, massive scale, NoSQL database service):

- It is NoSQL, consistent sub-10ms latency for large analytical and operational workloads.
- It is used by Google to deliver services such as Gmail and Google Maps.
- It is ideal for fintech, IoT, and ML storage use cases.
- It integrates easily with big data product families such as Dataproc and Dataflow.
- It is based on open source Apache HBase, enabling the use of its API.
- The cost of Bigtable is much higher than Datastore, so the database should be chosen with great care.

![alt text](images/Bigtable_Offerings.PNG)

### 8. Custom Databases (Using Compute Engine)

- Choose Compute Engine to install custom databases.
- eg. MongoDB, CouchDB etc.

### 9. Persistent Disk

- There are durable network storage devices hat can be accessed by our instances as if they were physical disks.
- They are located independently from our VM instances and can be detached and moved to keep data safe even after a VM is deleted.

![alt text](images/Persistent_Disk_Offerings.PNG)

---

# GCP Networking Services.

- GCP networking is based on Software-Defined Networks (SDNs). which allow users to deliver all networking services programmatically.
- All of the services are fully managed, leaving users with the task of configuring them according to their requirements.

![alt text](images/Google_Cloud_Network.PNG)

### 1. VPC (Virtual Private Cloud):

- You can think of it as a cloud version of a physical network.
- Each VPC network can contain one or more regional subnets.
- A VPC creates a global logical boundary that allows communication between resources within the same VPC network, subject to applicable network firewall rules.
- To allow communication between VPCs, traffic needs to traverse the internet or use VPC peering.

![alt text](images/VPC_Offerings.PNG)

### 2. Load Balancer (Traffic Distributor)

- A load balancer allows the distribution of traffic between your workloads.
- They are available for GCE, GAE, and GKE.
- For GCE, you can choose from load balancers with global or regional scopes.

![alt text](images/GCP_LoadBalancer_Types.PNG)
