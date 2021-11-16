**Q41. (#Plan)**

You have 32 GB of data in a single file that you need to upload to a Nearline Storage bucket. The WAN connection you are using is rated at 1 Gbps, and you are the only one on the connection. You want to use as much of the rated 1 Gbps as possible to transfer the file rapidly. How should you upload the file?

- A. Use the GCP Console to transfer the file instead of gsutil.
- B. Enable parallel composite uploads using gsutil on the file transfer.
- C. Decrease the TCP window size on the machine initiating the transfer.
- D. Change the storage class of the bucket from Nearline to Multi-Regional.

***My choice is B.***

Reason: The bandwidth is good and its a single file, gsutil parallel composite uploads can be used to split the large file and upload in parallel. See this:https://cloud.google.com/storage/docs/uploads-downloads#parallel-composite-uploads.



**Q42.(#Plan #GKE)**

You've deployed a microservice called myapp1 to a Google Kubernetes Engine cluster using the YAML file specified below:

![Q42](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q42.png)

You need to refactor this configuration so that the database password is not stored in plain text. You want to follow Google-recommended practices. What should you do?

- A. Store the database password inside the Docker image of the container, not in the YAML file.
- B. Store the database password inside a Secret object. Modify the YAML file to populate the DB_PASSWORD environment variable from the Secret.
- C. Store the database password inside a ConfigMap object. Modify the YAML file to populate the DB_PASSWORD environment variable from the ConfigMap.
- D. Store the database password in a file inside a Kubernetes persistent volume, and use a persistent volume claim to mount the volume to the container.

***My choice is B.***

Reason: https://cloud.google.com/kubernetes-engine/docs/concepts/secret. 



**Q43.(#AutoScaling)**

You are running an application on multiple virtual machines within a managed instance group and have autoscaling enabled. The autoscaling policy is configured so that additional instances are added to the group if the CPU utilization of instances goes above 80%. VMs are added until the instance group reaches its maximum limit of five VMs or until CPU utilization of instances lowers to 80%. The initial delay for HTTP health checks against the instances is set to 30 seconds.
The virtual machine instances take around three minutes to become available for users. You observe that when the instance group autoscales, it adds more instances then necessary to support the levels of end-user traffic. You want to properly maintain instance group sizes when autoscaling. What should you do?

- A. Set the maximum number of instances to 1.
- B. Decrease the maximum number of instances to 3.
- C. Use a TCP health check instead of an HTTP health check.
- D. Increase the initial delay of the HTTP health check to 200 seconds.

***My choice is D.***

Reason: When you do health check, you want the VM to be working. Do the first check after initial setup time of 3 mins = 180 s < 200 s is reasonable.



**Q44.(#Plan)**

You need to select and configure compute resources for a set of batch processing jobs. These jobs take around 2 hours to complete and are run nightly. You want to minimize service costs. What should you do?

- A. Select Google Kubernetes Engine. Use a single-node cluster with a small instance type.
- B. Select Google Kubernetes Engine. Use a three-node cluster with micro instance types.
- C. Select Compute Engine. Use preemptible VM instances of the appropriate standard machine type.
- D. Select Compute Engine. Use VM instance types that support micro bursting.

***My choice is C.***

Reason: For cost-saving & not immediate fault-tolerant workloads like batch jobs use Preemptible VM instances.



**Q45.(#AppEngine #Plan)**

You recently deployed a new version of an application to App Engine and then discovered a bug in the release. You need to immediately revert to the prior version of the application. What should you do?

- A. Run gcloud app restore.
- B. On the App Engine page of the GCP Console, select the application that needs to be reverted and click Revert.
- C. On the App Engine Versions page of the GCP Console, route 100% of the traffic to the previous version.
- D. Deploy the original version as a separate application. Then go to App Engine settings and split traffic between applications so that the original version serves 100% of the requests.

***My choice is C.***

Reason: Option A is wrong as gcloud app restore was used for backup and restore and has been deprecated.Option B is wrong as there is no application revert functionality available.Option D is wrong as App Engine maintains version and need not be redeployed.



**Q46.(#AppEngine #Plan)**

You deployed an App Engine application using gcloud app deploy, but it did not deploy to the intended project. You want to find out why this happened and where the application deployed. What should you do?

- A. Check the app.yaml file for your application and check project settings.
- B. Check the web-application.xml file for your application and check project settings.
- C. Go to Deployment Manager and review settings for deployment of applications.
- D. Go to Cloud Shell and run gcloud config list to review the Google Cloud configuration used for deployment.

***My choice is D.***

Reason: In app.yaml we would just provide the runtime and not the project configurations. In configuration you can see which is the active configuration/ project set in the configuration.



**Q47.(#Plan #ComputeEngine)**

You want to configure 10 Compute Engine instances for availability when maintenance occurs. Your requirements state that these instances should attempt to automatically restart if they crash. Also, the instances should be highly available including during system maintenance. What should you do?

- A. Create an instance template for the instances. Set the ג€˜Automatic Restartג€™ to on. Set the ג€˜On-host maintenanceג€™ to Migrate VM instance. Add the instance template to an instance group.
- B. Create an instance template for the instances. Set ג€˜Automatic Restartג€™ to off. Set ג€˜On-host maintenanceג€™ to Terminate VM instances. Add the instance template to an instance group.
- C. Create an instance group for the instances. Set the ג€˜Autohealingג€™ health check to healthy (HTTP).
- D. Create an instance group for the instance. Verify that the ג€˜Advanced creation optionsג€™ setting for ג€˜do not retry machine creationג€™ is set to off.

***My choice is A.***

Reason: https://cloud.google.com/compute/docs/instances/setting-instance-scheduling-options#autorestart and this:https://cloud.google.com/compute/docs/instances/setting-instance-scheduling-options .



**Q48.(#Plan #CloudStorage)**

You host a static website on Cloud Storage. Recently, you began to include links to PDF files on this site. Currently, when users click on the links to these PDF files, their browsers prompt them to save the file onto their local system. Instead, you want the clicked PDF files to be displayed within the browser window directly, without prompting the user to save the file locally. What should you do?

- A. Enable Cloud CDN on the website frontend.
- B. Enable ג€˜Share publiclyג€™ on the PDF file objects.
- C. Set Content-Type metadata to application/pdf on the PDF file objects.
- D. Add a label to the storage bucket with a key of Content-Type and value of application/pdf.

***My choice is C.***

Reason: https://cloud.google.com/storage/docs/metadata#content-type.



**Q49.(#Plan)**

You have a virtual machine that is currently configured with 2 vCPUs and 4 GB of memory. It is running out of memory. You want to upgrade the virtual machine to have 8 GB of memory. What should you do?

- A. Rely on live migration to move the workload to a machine with more memory.
- B. Use gcloud to add metadata to the VM. Set the key to required-memory-size and the value to 8 GB.
- C. Stop the VM, change the machine type to n1-standard-8, and start the VM.
- D. Stop the VM, increase the memory to 8 GB, and start the VM.

***My choice is D.***

Reason: https://cloud.google.com/compute/docs/instances/creating-instance-with-custom-machine-type.



**Q50.(#Plan #ComputeEngine)**

You have production and test workloads that you want to deploy on Compute Engine. Production VMs need to be in a different subnet than the test VMs. All the
VMs must be able to reach each other over Internal IP without creating additional routes. You need to set up VPC and the 2 subnets. Which configuration meets these requirements?

- A. Create a single custom VPC with 2 subnets. Create each subnet in a different region and with a different CIDR range.
- B. Create a single custom VPC with 2 subnets. Create each subnet in the same region and with the same CIDR range.
- C. Create 2 custom VPCs, each with a single subnet. Create each subnet in a different region and with a different CIDR range.
- D. Create 2 custom VPCs, each with a single subnet. Create each subnet in the same region and with the same CIDR range.

***My choice is A.***

Reason: VPC is global in nature. Subnets are regional but are connected globally. So creating 1 VPC and different CIDR for different subnets should suffice the purpose.



**Q51.(#Plan #AutoScaling)**

You need to create an autoscaling managed instance group for an HTTPS web application. You want to make sure that unhealthy VMs are recreated. What should you do?

- A. Create a health check on port 443 and use that when creating the Managed Instance Group.
- B. Select Multi-Zone instead of Single-Zone when creating the Managed Instance Group.
- C. In the Instance Template, add the label ג€˜health-checkג€™.
- D. In the Instance Template, add a startup script that sends a heartbeat to the metadata server.

***My choice is A.***

Reason:  adding a label will not recreate the VM.



**Q52.(#Plan #IAM #BigQuery)**

Your company has a Google Cloud Platform project that uses BigQuery for data warehousing. Your data science team changes frequently and has few members.
You need to allow members of this team to perform queries. You want to follow Google-recommended practices. What should you do?

- A. 1. Create an IAM entry for each data scientist's user account. 2. Assign the BigQuery jobUser role to the group.
- B. 1. Create an IAM entry for each data scientist's user account. 2. Assign the BigQuery dataViewer user role to the group.
- C. 1. Create a dedicated Google group in Cloud Identity. 2. Add each data scientist's user account to the group. 3. Assign the BigQuery jobUser role to the group.
- D. 1. Create a dedicated Google group in Cloud Identity. 2. Add each data scientist's user account to the group. 3. Assign the BigQuery dataViewer user role to the group.

***My choice is C.***

Reason:  Why not IAM roles? Google recommends to use groups when it is possible. 

BigQuery Data Viewer: When applied to a table or view, this role provides permissions to: Read data and metadata from the table or view. This role cannot be applied to individual models or routines. 

When applied to a dataset, this role provides permissions to: Read the dataset's metadata and list tables in the dataset. Read data and metadata from the dataset's tables. BigQuery Job User: Provides permissions to run jobs, including queries, within the project. reference: https://cloud.google.com/bigquery/docs/access-control



**Q53.(#Plan)**

Your company has a 3-tier solution running on Compute Engine. The configuration of the current infrastructure is shown below.

![Q53](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q53.png)

Each tier has a service account that is associated with all instances within it. You need to enable communication on TCP port 8080 between tiers as follows:
\* Instances in tier #1 must communicate with tier #2.
\* Instances in tier #2 must communicate with tier #3.
What should you do?

- A. 1. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.2.0/24) ג€¢ Protocols: allow all 2. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.1.0/24) ג€¢ Protocols: allow all
- B. 1. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #2 service account ג€¢ Source filter: all instances with tier #1 service account ג€¢ Protocols: allow TCP:8080 2. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #3 service account ג€¢ Source filter: all instances with tier #2 service account ג€¢ Protocols: allow TCP: 8080
- C. 1. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #2 service account ג€¢ Source filter: all instances with tier #1 service account ג€¢ Protocols: allow all 2. Create an ingress firewall rule with the following settings: ג€¢ Targets: all instances with tier #3 service account ג€¢ Source filter: all instances with tier #2 service account ג€¢ Protocols: allow all
- D. 1. Create an egress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.2.0/24) ג€¢ Protocols: allow TCP: 8080 2. Create an egress firewall rule with the following settings: ג€¢ Targets: all instances ג€¢ Source filter: IP ranges (with the range set to 10.0.1.0/24) ג€¢ Protocols: allow TCP: 8080

***My choice is B.***

Reason: if you see closely, port 8080 and service account is required so B is the answer without reading all answers.



**Q54.(#VPC #ComputeEngine)**

You are given a project with a single Virtual Private Cloud (VPC) and a single subnetwork in the us-central1 region. There is a Compute Engine instance hosting an application in this subnetwork. You need to deploy a new instance in the same project in the europe-west1 region. This new instance needs access to the application. You want to follow Google-recommended practices. What should you do?

- A. 1. Create a subnetwork in the same VPC, in europe-west1. 2. Create the new instance in the new subnetwork and use the first instance's private address as the endpoint.
- B. 1. Create a VPC and a subnetwork in europe-west1. 2. Expose the application with an internal load balancer. 3. Create the new instance in the new subnetwork and use the load balancer's address as the endpoint.
- C. 1. Create a subnetwork in the same VPC, in europe-west1. 2. Use Cloud VPN to connect the two subnetworks. 3. Create the new instance in the new subnetwork and use the first instance's private address as the endpoint.
- D. 1. Create a VPC and a subnetwork in europe-west1. 2. Peer the 2 VPCs. 3. Create the new instance in the new subnetwork and use the first instance's private address as the endpoint.

***My choice is A.***

Reason: Subnets are global.



**Q55.(#GKE)**

Your projects incurred more costs than you expected last month. Your research reveals that a development GKE container emitted a huge number of logs, which resulted in higher costs. You want to disable the logs quickly using the minimum number of steps. What should you do?

- A. 1. Go to the Logs ingestion window in Stackdriver Logging, and disable the log source for the GKE container resource.
- B. 1. Go to the Logs ingestion window in Stackdriver Logging, and disable the log source for the GKE Cluster Operations resource.
- C. 1. Go to the GKE console, and delete existing clusters. 2. Recreate a new cluster. 3. Clear the option to enable legacy Stackdriver Logging.
- D. 1. Go to the GKE console, and delete existing clusters. 2. Recreate a new cluster. 3. Clear the option to enable legacy Stackdriver Monitoring.

***My choice is A .***

Reason: https://cloud.google.com/logging/docs/api/v2/resource-list. GKE Containers have more log than GKE Cluster Operations.



**Q56.(#AppEngine)**

You have a website hosted on App Engine standard environment. You want 1% of your users to see a new test version of the website. You want to minimize complexity. What should you do?

- A. Deploy the new version in the same application and use the --migrate option.
- B. Deploy the new version in the same application and use the --splits option to give a weight of 99 to the current version and a weight of 1 to the new version.
- C. Create a new App Engine application in the same project. Deploy the new version in that application. Use the App Engine library to proxy 1% of the requests to the new version.
- D. Create a new App Engine application in the same project. Deploy the new version in that application. Configure your network load balancer to send 1% of the traffic to that new application.

***My choice is B .***

Reason: Only one app engine can exist in one project. And in app engine we cannot create "new application", we have to create a new Project to do that, an app engine projet has 1 application (which can have multiple versions and services). Check this: https://cloud.google.com/appengine/docs/standard/python3/splitting-traffic#splitting_traffic_across_multiple_versions and this:https://cloud.google.com/appengine/docs/standard/python/splitting-traffic#gcloud









































