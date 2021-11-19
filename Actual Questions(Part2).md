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

Reason: Only one app engine can exist in one project. And in app engine we cannot create "new application", we have to create a new Project to do that, an app engine projet has 1 application (which can have multiple versions and services). Check this: https://cloud.google.com/appengine/docs/standard/python3/splitting-traffic#splitting_traffic_across_multiple_versions and this:https://cloud.google.com/appengine/docs/standard/python/splitting-traffic#gcloud。



**Q57.**

You have a web application deployed as a managed instance group. You have a new version of the application to gradually deploy. Your web application is currently receiving live web traffic. You want to ensure that the available capacity does not decrease during the deployment. What should you do?

- A. Perform a rolling-action start-update with maxSurge set to 0 and maxUnavailable set to 1.
- B. Perform a rolling-action start-update with maxSurge set to 1 and maxUnavailable set to 0.
- C. Create a new managed instance group with an updated instance template. Add the group to the backend service for the load balancer. When all instances in the new managed instance group are healthy, delete the old managed instance group.
- D. Create a new instance template with the new application version. Update the existing managed instance group with the new instance template. Delete the instances in the managed instance group to allow the managed instance group to recreate the instance using the new instance template.

***My choice is B.***

Reason:  If you do not want any unavailable machines during an update, set the maxUnavailable value to 0 and the maxSurge value to greater than 0.With these settings, Compute Engine removes each old machine only after its replacement new machine is created and running. Ref: https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups and also here: https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups#max_unavailable.



**Q58.(#StorageSolution)**

You are building an application that stores relational data from users. Users across the globe will use this application. Your CTO is concerned about the scaling requirements because the size of the user base is unknown. You need to implement a database solution that can scale with your user growth with minimum configuration changes. Which storage solution should you use?

- A. Cloud SQL
- B. Cloud Spanner
- C. Cloud Firestore
- D. Cloud Datastore

***My choice is B.***

Reason: For globalization and relational data...Cloud spanner is correct. Cloud SQL for small relational data, scaled manually Cloud Spanner for relational data, scaled automatically Cloud Firestore for app-based data(?) Cloud Datastore for non-relational data.



**Q59.(#Plan #Scenario)**

You are the organization and billing administrator for your company. The engineering team has the Project Creator role on the organization. You do not want the engineering team to be able to link projects to the billing account. Only the finance team should be able to link a project to a billing account, but they should not be able to make any other changes to projects. What should you do?

- A. Assign the finance team only the Billing Account User role on the billing account.
- B. Assign the engineering team only the Billing Account User role on the billing account.
- C. Assign the finance team the Billing Account User role on the billing account and the Project Billing Manager role on the organization.
- D. Assign the engineering team the Billing Account User role on the billing account and the Project Billing Manager role on the organization.

***My choice is A.***

Reason: The question says that the finance team should (ONLY) be able to link a project to a billing account, but not be able to make any other changes to projects. The purpose of the Billing Account User role is to link projects to billing accounts. Also, from its description: "This role has very restricted permissions, so you can grant it broadly, typically in combination with Project Creator. These two roles allow a user to create new projects linked to the billing account on which the role is granted." Reference: https://cloud.google.com/billing/docs/how-to/billing-access#overview-of-cloud-billing-roles-in-cloud-iam.



**Q60.(#GKE)**

You have an application running in Google Kubernetes Engine (GKE) with cluster autoscaling enabled. The application exposes a TCP endpoint. There are several replicas of this application. You have a Compute Engine instance in the same region, but in another Virtual Private Cloud (VPC), called gce-network, that has no overlapping IP ranges with the first VPC. This instance needs to connect to the application on GKE. You want to minimize effort. What should you do?

- A. 1. In GKE, create a Service of type LoadBalancer that uses the application's Pods as backend. 2. Set the service's externalTrafficPolicy to Cluster. 3. Configure the Compute Engine instance to use the address of the load balancer that has been created.
- B. 1. In GKE, create a Service of type NodePort that uses the application's Pods as backend. 2. Create a Compute Engine instance called proxy with 2 network interfaces, one in each VPC. 3. Use iptables on this instance to forward traffic from gce-network to the GKE nodes. 4. Configure the Compute Engine instance to use the address of proxy in gce-network as endpoint.
- C. 1. In GKE, create a Service of type LoadBalancer that uses the application's Pods as backend. 2. Add an annotation to this service: cloud.google.com/load-balancer-type: Internal 3. Peer the two VPCs together. 4. Configure the Compute Engine instance to use the address of the load balancer that has been created.
- D. 1. In GKE, create a Service of type LoadBalancer that uses the application's Pods as backend. 2. Add a Cloud Armor Security Policy to the load balancer that whitelists the internal IPs of the MIG's instances. 3. Configure the Compute Engine instance to use the address of the load balancer that has been created.

***My choice is C.***

Reason: C is better solution, the solution A pass trafic trought public internet, also C by internal network and the "no overlap ips" in the statament suggest that.



**Q61.(#Plan)**

Your organization is a financial company that needs to store audit log files for 3 years. Your organization has hundreds of Google Cloud projects. You need to implement a cost-effective approach for log file retention. What should you do?

- A. Create an export to the sink that saves logs from Cloud Audit to BigQuery.
- B. Create an export to the sink that saves logs from Cloud Audit to a Coldline Storage bucket.
- C. Write a custom script that uses logging API to copy the logs from Stackdriver logs to BigQuery.
- D. Export these logs to Cloud Pub/Sub and write a Cloud Dataflow pipeline to store logs to Cloud SQL.

***My choice is B.***

Reason:  In the only talked about storing at cheap-cost, so coldline has low storage cost. See this: https://cloud.google.com/bigquery/docs/best-practices-storage



**Q62.(#Plan)**

You want to run a single caching HTTP reverse proxy on GCP for a latency-sensitive website. This specific reverse proxy consumes almost no CPU. You want to have a 30-GB in-memory cache, and need an additional 2 GB of memory for the rest of the processes. You want to minimize cost. How should you run this reverse proxy?

- A. Create a Cloud Memorystore for Redis instance with 32-GB capacity.
- B. Run it on Compute Engine, and choose a custom instance type with 6 vCPUs and 32 GB of memory.
- C. Package it in a container image, and run it on Kubernetes Engine, using n1-standard-32 instances as nodes.
- D. Run it on Compute Engine, choose the instance type n1-standard-1, and add an SSD persistent disk of 32 GB.

***My choice is A.***

Reason:The key word is "for a latency-sensitive website." https://cloud.google.com/memorystore/docs/redis/redis-overview#what_its_good_for .Memorystore for Redis provides a fast, in-memory store for use cases that require fast, real-time processing of data. From simple caching use cases to real time analytics, Memorystore for Redis provides the performance you need. Caching: Cache is an integral part of modern application architectures. Memorystore for Redis provides low latency access and high throughput for heavily accessed data, compared to accessing the data from a disk based backend store. Session management, frequently accessed queries, scripts, and pages are common examples of caching.



**Q63.(#CloudStorage #Plan)**

You are hosting an application on bare-metal servers in your own data center. The application needs access to Cloud Storage. However, security policies prevent the servers hosting the application from having public IP addresses or access to the internet. You want to follow Google-recommended practices to provide the application with access to Cloud Storage. What should you do?

- A. 1. Use nslookup to get the IP address for storage.googleapis.com. 2. Negotiate with the security team to be able to give a public IP address to the servers. 3. Only allow egress traffic from those servers to the IP addresses for storage.googleapis.com.
- B. 1. Using Cloud VPN, create a VPN tunnel to a Virtual Private Cloud (VPC) in Google Cloud. 2. In this VPC, create a Compute Engine instance and install the Squid proxy server on this instance. 3. Configure your servers to use that instance as a proxy to access Cloud Storage.
- C. 1. Use Migrate for Compute Engine (formerly known as Velostrata) to migrate those servers to Compute Engine. 2. Create an internal load balancer (ILB) that uses storage.googleapis.com as backend. 3. Configure your new instances to use this ILB as proxy.
- D. 1. Using Cloud VPN or Interconnect, create a tunnel to a VPC in Google Cloud. 2. Use Cloud Router to create a custom route advertisement for 199.36.153.4/30. Announce that network to your on-premises network through the VPN tunnel. 3. In your on-premises network, configure your DNS server to resolve *.googleapis.com as a CNAME to restricted.googleapis.com.

***My choice is D.***

Reason:Ref: https://cloud.google.com/vpc/docs/configure-private-google-access-hybrid.



**Q64.(#CloudPub/Sub)**

You want to deploy an application on Cloud Run that processes messages from a Cloud Pub/Sub topic. You want to follow Google-recommended practices. What should you do?

- A. 1. Create a Cloud Function that uses a Cloud Pub/Sub trigger on that topic. 2. Call your application on Cloud Run from the Cloud Function for every message.
- B. 1. Grant the Pub/Sub Subscriber role to the service account used by Cloud Run. 2. Create a Cloud Pub/Sub subscription for that topic. 3. Make your application pull messages from that subscription.
- C. 1. Create a service account. 2. Give the Cloud Run Invoker role to that service account for your Cloud Run application. 3. Create a Cloud Pub/Sub subscription that uses that service account and uses your Cloud Run application as the push endpoint.
- D. 1. Deploy your application on Cloud Run on GKE with the connectivity set to Internal. 2. Create a Cloud Pub/Sub subscription for that topic. 3. In the same Google Kubernetes Engine cluster as your application, deploy a container that takes the messages and sends them to your application.

***My choice is C.***

Reason: See this: https://cloud.google.com/run/docs/tutorials/pubsub.



**Q65.(#Deploy #CloudRun)**

You need to deploy an application, which is packaged in a container image, in a new project. The application exposes an HTTP endpoint and receives very few requests per day. You want to minimize costs. What should you do?

- A. Deploy the container on Cloud Run.
- B. Deploy the container on Cloud Run on GKE.
- C. Deploy the container on App Engine Flexible.
- D. Deploy the container on GKE with cluster autoscaling and horizontal pod autoscaling enabled.

***My choice is A.***

Reason: Cloud Run is a fully managed compute platform that automatically scales your stateless containers. Cloud Run is serverless. Cloud Run abstracts away all infrastructure management. It automatically scales up and down from zero depending on traffic almost instantaneously. Cloud Run only charges you for the exact resources you use. Ref: https://cloud.google.com/run.



**Q66.(#Billing)**

Your company has an existing GCP organization with hundreds of projects and a billing account. Your company recently acquired another company that also has hundreds of projects and its own billing account. You would like to consolidate all GCP costs of both GCP organizations onto a single invoice. You would like to consolidate all costs as of tomorrow. What should you do?

- A. Link the acquired companyג€™s projects to your company's billing account.
- B. Configure the acquired company's billing account and your company's billing account to export the billing data into the same BigQuery dataset.
- C. Migrate the acquired companyג€™s projects into your companyג€™s GCP organization. Link the migrated projects to your company's billing account.
- D. Create a new GCP organization and a new billing account. Migrate the acquired company's projects and your company's projects into the new GCP organization and link the projects to the new billing account.

***My choice is A.***

Reason: https://cloud.google.com/billing/docs/concepts#relationships-between-resources. Please note: Payment linkage of a project linked to a Cloud Billing account is not limited by organization ownership. It is possible for a Cloud Billing account to pay for projects that belong to an organization that is different than the organization that owns the Cloud Billing account. And this: https://medium.com/google-cloud/google-cloud-platform-cross-org-billing-41c5db8fefa6. 

Please read the article how you can get invoice https://cloud.google.com/billing/docs/how-to/get-invoice If you export your data into your local BigQuery dataset it does not change anything! you only export logs! your old projects are still linked to the only billing account. And Google will create invoice based on their information. Google will NOT rely on the data that is stored in your local BigQuery table.



**Q67.(#Plan #CloudSpanner)**

You built an application on Google Cloud that uses Cloud Spanner. Your support team needs to monitor the environment but should not have access to table data.
You need a streamlined solution to grant the correct permissions to your support team, and you want to follow Google-recommended practices. What should you do?

- A. Add the support team group to the roles/monitoring.viewer role
- B. Add the support team group to the roles/spanner.databaseUser role.
- C. Add the support team group to the roles/spanner.databaseReader role.
- D. Add the support team group to the roles/stackdriver.accounts.viewer role.

***My choice is A.***

Reason: A is enough, B and C are incorrect since they allow users to read data. D is incorrect, it is not for monitoring.



**Q68.(#ComputeEngine #BigQuery)**

For analysis purposes, you need to send all the logs from all of your Compute Engine instances to a BigQuery dataset called platform-logs. You have already installed the Cloud Logging agent on all the instances. You want to minimize cost. What should you do?

- A. 1. Give the BigQuery Data Editor role on the platform-logs dataset to the service accounts used by your instances. 2. Update your instancesג€™ metadata to add the following value: logs-destination: bq://platform-logs.
- B. 1. In Cloud Logging, create a logs export with a Cloud Pub/Sub topic called logs as a sink. 2. Create a Cloud Function that is triggered by messages in the logs topic. 3. Configure that Cloud Function to drop logs that are not from Compute Engine and to insert Compute Engine logs in the platform-logs dataset.
- C. 1. In Cloud Logging, create a filter to view only Compute Engine logs. 2. Click Create Export. 3. Choose BigQuery as Sink Service, and the platform-logs dataset as Sink Destination.
- D. 1. Create a Cloud Function that has the BigQuery User role on the platform-logs dataset. 2. Configure this Cloud Function to create a BigQuery Job that executes this query: INSERT INTO dataset.platform-logs (timestamp, log) SELECT timestamp, log FROM compute.logs WHERE timestamp > DATE_SUB(CURRENT_DATE(), INTERVAL 1 DAY) 3. Use Cloud Scheduler to trigger this Cloud Function once a day.

***My choice is C.***

Reason: https://cloud.google.com/logging/docs/export/configure_export_v2



**Q69.(#DeployManager #GKE)**

You are using Deployment Manager to create a Google Kubernetes Engine cluster. Using the same Deployment Manager deployment, you also want to create a
DaemonSet in the kube-system namespace of the cluster. You want a solution that uses the fewest possible services. What should you do?

- A. Add the clusterג€™s API as a new Type Provider in Deployment Manager, and use the new type to create the DaemonSet.
- B. Use the Deployment Manager Runtime Configurator to create a new Config resource that contains the DaemonSet definition.
- C. With Deployment Manager, create a Compute Engine instance with a startup script that uses kubectl to create the DaemonSet.
- D. In the clusterג€™s definition in Deployment Manager, add a metadata that has kube-system as key and the DaemonSet manifest as value.

***My choice is A.***

Reason: Adding an API as a type provider This page describes how to add an API to Google Cloud Deployment Manager as a type provider. To learn more about types and type providers, read the Types overview documentation. A type provider exposes all of the resources of a third-party API to Deployment Manager as base types that you can use in your configurations. These types must be directly served by a RESTful API that supports Create, Read, Update, and Delete (CRUD). If you want to use an API that is not automatically provided by Google with Deployment Manager, you must add the API as a type provider. https://cloud.google.com/deployment-manager/docs/configuration/type-providers/creating-type-provider



**Q70.(#ServiceAccount)**

You are building an application that will run in your data center. The application will use Google Cloud Platform (GCP) services like AutoML. You created a service account that has appropriate access to AutoML. You need to enable authentication to the APIs from your on-premises environment. What should you do?

- A. Use service account credentials in your on-premises application.
- B. Use gcloud to create a key file for the service account that has appropriate permissions.
- C. Set up direct interconnect between your data center and Google Cloud Platform to enable authentication for your on-premises applications.
- D. Go to the IAM & admin console, grant a user account permissions similar to the service account permissions, and use this user account for authentication from your data center.

***My choice is B.***

Reason: 1st step...the key file is to be referenced in the env variable GOOGLE_APPLICATION_CREDENTIALS which would then provide access to on-prem application using ADC library. 

To use a service account outside of Google Cloud, such as on other platforms or on-premises, you must first establish the identity of the service account. Public/private key pairs provide a secure way of accomplishing this goal. https://cloud.google.com/iam/docs/creating-managing-service-account-keys.



**Q71.(#GKE)**

You are using Container Registry to centrally store your company's container images in a separate project. In another project, you want to create a Google
Kubernetes Engine (GKE) cluster. You want to ensure that Kubernetes can download images from Container Registry. What should you do?

- A. In the project where the images are stored, grant the Storage Object Viewer IAM role to the service account used by the Kubernetes nodes.
- B. When you create the GKE cluster, choose the Allow full access to all Cloud APIs option under ג€˜Access scopesג€™.
- C. Create a service account, and give it access to Cloud Storage. Create a P12 key for this service account and use it as an imagePullSecrets in Kubernetes.
- D. Configure the ACLs on each image in Cloud Storage to give read-only access to the default Compute Engine service account.

***My choice is A.***

Reason: Container Registry uses Cloud Storage buckets as the underlying storage for container images. You control access to your images by granting appropriate Cloud Storage permissions to a user, group, service account, or other identity. If the service account needs to access Container Registry in another project, you must grant the required permissions in the project with Container Registry. Reference: https://cloud.google.com/container-registry/docs/access-control#permissions.



**Q72.(#GKE)**

You deployed a new application inside your Google Kubernetes Engine cluster using the YAML file specified below.



insert image Q72(1)



You deployed a new application inside your Google Kubernetes Engine cluster using the YAML file specified below.



insert image Q72(2)



You want to find out why the pod is stuck in pending status. What should you do?

- A. Review details of the myapp-service Service object and check for error messages.
- B. Review details of the myapp-deployment Deployment object and check for error messages.
- C. Review details of myapp-deployment-58ddbbb995-lp86m Pod and check for warning messages.
- D. View logs of the container in myapp-deployment-58ddbbb995-lp86m pod and check for warning messages.

**My choice is C.**

Reason: https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/#debugging-pods.



**Q73.(#ComputeEngine)**

You are setting up a Windows VM on Compute Engine and want to make sure you can log in to the VM via RDP. What should you do?

- A. After the VM has been created, use your Google Account credentials to log in into the VM.
- B. After the VM has been created, use gcloud compute reset-windows-password to retrieve the login credentials for the VM.
- C. When creating the VM, add metadata to the instance using ג€˜windows-passwordג€™ as the key and a password as the value.
- D. After the VM has been created, download the JSON private key for the default Compute Engine service account. Use the credentials in the JSON file to log in to the VM.

***My choice is B.***

Reason: Windows Server instances use password authentication instead of SSH authentication. To prevent unauthorized access to new Windows instances, Compute Engine requires that you generate a new Windows password for that instance before you connect to it.  https://cloud.google.com/compute/docs/instances/windows/generating-credentials#gcloud. and this: https://cloud.google.com/compute/docs/instances/windows/creating-passwords-for-windows-instances.



**Q74.(#ComputeEngine)**

You want to configure an SSH connection to a single Compute Engine instance for users in the dev1 group. This instance is the only resource in this particular
Google Cloud Platform project that the dev1 users should be able to connect to. What should you do?

- A. Set metadata to enable-oslogin=true for the instance. Grant the dev1 group the compute.osLogin role. Direct them to use the Cloud Shell to ssh to that instance.
- B. Set metadata to enable-oslogin=true for the instance. Set the service account to no service account for that instance. Direct them to use the Cloud Shell to ssh to that instance.
- C. Enable block project wide keys for the instance. Generate an SSH key for each user in the dev1 group. Distribute the keys to dev1 users and direct them to use their third-party tools to connect.
- D. Enable block project wide keys for the instance. Generate an SSH key and associate the key with that instance. Distribute the key to dev1 users and direct them to use their third-party tools to connect.

**My choice is A.**

Reason: NEVER EVER DISTRIBUTE private keys or generate SSH KEYS for others. This automatically excludes two answers (C + D), it has to be A because B talks about service accounts which has nothing to do with dev group needing to SSH to the instance. https://cloud.google.com/compute/docs/instances/managing-instance-access.

--------------------------------------------------------------------------------

**Q75.(#CloudShell)**

You need to produce a list of the enabled Google Cloud Platform APIs for a GCP project using the gcloud command line in the Cloud Shell. The project name is my-project. What should you do?

- A. Run gcloud projects list to get the project ID, and then run gcloud services list --project <project ID>.
- B. Run gcloud init to set the current project to my-project, and then run gcloud services list --available.
- C. Run gcloud info to view the account value, and then run gcloud services list --account <Account>.
- D. Run gcloud projects describe <project ID> to verify the project value, and then run gcloud services list --available.

***My choice is A.***

Reason: For those, who have doubts: `gcloud services list --available` returns not only the enabled services in the project but also services that CAN be enabled. Therefore, option B is incorrect. https://cloud.google.com/sdk/gcloud/reference/services/list#--available

--------------------------------------------------------------------------------------------------------------------------------------

**Q76.(#AppEngine)**

You are building a new version of an application hosted in an App Engine environment. You want to test the new version with 1% of users before you completely switch your application over to the new version. What should you do?

- A. Deploy a new version of your application in Google Kubernetes Engine instead of App Engine and then use GCP Console to split traffic.
- B. Deploy a new version of your application in a Compute Engine instance instead of App Engine and then use GCP Console to split traffic.
- C. Deploy a new version as a separate app in App Engine. Then configure App Engine using GCP Console to split traffic between the two apps.
- D. Deploy a new version of your application in App Engine. Then go to App Engine settings in GCP Console and split traffic between the current version and newly deployed versions accordingly.

***My choice is D.***

Reason: The question is about App Engine. In the App Engine splitting the traffic will do the job.

--------------------------------------------------------------------------------------------------------------------------------------

**Q77.(#GKE #Plan)**

You need to provide a cost estimate for a Kubernetes cluster using the GCP pricing calculator for Kubernetes. Your workload requires high IOPs, and you will also be using disk snapshots. You start by entering the number of nodes, average hours, and average days. What should you do next?

- A. Fill in local SSD. Fill in persistent disk storage and snapshot storage.
- B. Fill in local SSD. Add estimated cost for cluster management.
- C. Select Add GPUs. Fill in persistent disk storage and snapshot storage.
- D. Select Add GPUs. Add estimated cost for cluster management.

***My choice is A.***

Reason: try below steps to understand why- 1) Click - https://cloud.google.com/products/calculator/. 2) Select GKE Standard 3) Check the help '?' icon for "Local SSD" field- "Local solid state disks, providing very high IOPS and very low latency block storage."

----------------------------------

**Q78.(#GKE #AutoScaling)**

You are using Google Kubernetes Engine with autoscaling enabled to host a new application. You want to expose this new application to the public, using HTTPS on a public IP address. What should you do?

- A. Create a Kubernetes Service of type NodePort for your application, and a Kubernetes Ingress to expose this Service via a Cloud Load Balancer.
- B. Create a Kubernetes Service of type ClusterIP for your application. Configure the public DNS name of your application using the IP of this Service.
- C. Create a Kubernetes Service of type NodePort to expose the application on port 443 of each node of the Kubernetes cluster. Configure the public DNS name of your application with the IP of every node of the cluster to achieve load-balancing.
- D. Create a HAProxy pod in the cluster to load-balance the traffic to all the pods of the application. Forward the public traffic to HAProxy with an iptable rule. Configure the DNS name of your application using the public IP of the node HAProxy is running on.

***My choice is A.***

Reason: For external access you need NodePort service and NodePort is a SVC so A is correct. 

HAProxy is HTTP only, doesnt support HTTPS, so you can reject option D. https://www.haproxy.org/#desc  

Cluster IP - is an internal IP, you cannot expose public externally. reject option B.

Option C, port 443 is https but public DNS is not going to give you a load balancing.

A is the right choice, kubernets ingress exposes HTTPS,  https://kubernetes.io/docs/concepts/services-networking/ingress/ . and cloud load balancer is the right choice which will help to expose the app to public.

--------------------------------------------------------------------------------------------------------------

**Q79.(#traffic #ComputeEngine)**

You need to enable traffic between multiple groups of Compute Engine instances that are currently running two different GCP projects. Each group of Compute
Engine instances is running in its own VPC. What should you do?

- A. Verify that both projects are in a GCP Organization. Create a new VPC and add all instances.
- B. Verify that both projects are in a GCP Organization. Share the VPC from one project and request that the Compute Engine instances in the other project use this shared VPC.
- C. Verify that you are the Project Administrator of both projects. Create two new VPCs and add all instances.
- D. Verify that you are the Project Administrator of both projects. Create a new VPC and add all instances.

***My choice is B.***

Reason: see this    https://cloud.google.com/vpc/docs/shared-vpc

----------------------

**Q80.(#Auditor)**

You want to add a new auditor to a Google Cloud Platform project. The auditor should be allowed to read, but not modify, all project items.
How should you configure the auditor's permissions?

- A. Create a custom role with view-only project permissions. Add the user's account to the custom role.
- B. Create a custom role with view-only service permissions. Add the user's account to the custom role.
- C. Select the built-in IAM project Viewer role. Add the user's account to this role.
- D. Select the built-in IAM service Viewer role. Add the user's account to this role.

***My choice is C.***

Reason: Basic roles include thousands of permissions across all Google Cloud services. In production environments, do not grant basic roles unless there is no alternative. Instead, grant the most limited predefined roles or custom roles that meet your needs.

-----------------------

**Q81.(#GKE)**

You are operating a Google Kubernetes Engine (GKE) cluster for your company where different teams can run non-production workloads. Your Machine Learning
(ML) team needs access to Nvidia Tesla P100 GPUs to train their models. You want to minimize effort and cost. What should you do?

- A. Ask your ML team to add the ג€accelerator: gpuג€ annotation to their pod specification.
- B. Recreate all the nodes of the GKE cluster to enable GPUs on all of them.
- C. Create your own Kubernetes cluster on top of Compute Engine with nodes that have GPUs. Dedicate this cluster to your ML team.
- D. Add a new, GPU-enabled, node pool to the GKE cluster. Ask your ML team to add the cloud.google.com/gke -accelerator: nvidia-tesla-p100 nodeSelector to their pod specification.

***My choice is D.***

Reason: Nodepools are way to logically separate your workloads and machinetypes based on your organization team/project structure and requirements.

------------------------

**Q82.(#VM)**

Your VMs are running in a subnet that has a subnet mask of 255.255.255.240. The current subnet has no more free IP addresses and you require an additional
10 IP addresses for new VMs. The existing and new VMs should all be able to reach each other without additional routes. What should you do?

- A. Use gcloud to expand the IP range of the current subnet.
- B. Delete the subnet, and recreate it using a wider range of IP addresses.
- C. Create a new project. Use Shared VPC to share the current network with the new project.
- D. Create a new subnet with the same starting IP but a wider range to overwrite the current subnet.

***My choice is A.***

Reason: https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/expand-ip-range.

---

**Q83.(#Plan)**

Your organization uses G Suite for communication and collaboration. All users in your organization have a G Suite account. You want to grant some G Suite users access to your Cloud Platform project. What should you do?

- A. Enable Cloud Identity in the GCP Console for your domain.
- B. Grant them the required IAM roles using their G Suite email address.
- C. Create a CSV sheet with all usersג€™ email addresses. Use the gcloud command line tool to convert them into Google Cloud Platform accounts.
- D. In the G Suite console, add the users to a special group called cloud-console-users@yourdomain.com. Rely on the default behavior of the Cloud Platform to grant users access if they are members of this group.

**My choice is B.**

Reason: To actively adopt the Organization resource, the G Suite or Cloud Identity super admins need to assign the Organization Administrator Cloud IAM role to a user or group.

------

**Q84.(#Plan)**

You have a Google Cloud Platform account with access to both production and development projects. You need to create an automated process to list all compute instances in development and production projects on a daily basis. What should you do?

- A. Create two configurations using gcloud config. Write a script that sets configurations as active, individually. For each configuration, use gcloud compute instances list to get a list of compute resources.
- B. Create two configurations using gsutil config. Write a script that sets configurations as active, individually. For each configuration, use gsutil compute instances list to get a list of compute resources.
- C. Go to Cloud Shell and export this information to Cloud Storage on a daily basis.
- D. Go to GCP Console and export this information to Cloud SQL on a daily basis.

***My choice is A.***

Reason: https://cloud.google.com/sdk/gcloud/reference/compute/instances/list.

-----

**Q85.(#CloudStorage)**

You have a large 5-TB AVRO file stored in a Cloud Storage bucket. Your analysts are proficient only in SQL and need access to the data stored in this file. You want to find a cost-effective way to complete their request as soon as possible. What should you do?

- A. Load data in Cloud Datastore and run a SQL query against it.
- B. Create a BigQuery table and load data in BigQuery. Run a SQL query on this table and drop this table after you complete your request.
- C. Create external tables in BigQuery that point to Cloud Storage buckets and run a SQL query on these external tables to complete your request.
- D. Create a Hadoop cluster and copy the AVRO file to NDFS by compressing it. Load the file in a hive table and provide access to your analysts so that they can run SQL queries.

***My choice is C.***

Reason: 

A. ....Load data in Cloud Datastore... (Not Correct because Cloud Datastore is not a good option to run SQL Queries) 

B. ...Load data in BigQuery.... (Not Cost Effective because loading the data which is already present in the bucket into BigQuery again is expensive) 

C. Create external tables in BigQuery that point to Cloud Storage buckets and run a SQL query on these external tables to complete your request. (This is the right answer as it meets all the requirements from the question) 

D. Create a Hadoop cluster and copy the AVRO file to NDFS by compressing it. Load the file in a hive table and provide access to your analysts so that they can run SQL queries. (Too roundabout and indirect. Not the right option)

and this:https://cloud.google.com/bigquery/external-data-sources.

-----

**Q86.(#Verify)**

You need to verify that a Google Cloud Platform service account was created at a particular time. What should you do?

- A. Filter the Activity log to view the Configuration category. Filter the Resource type to Service Account.
- B. Filter the Activity log to view the Configuration category. Filter the Resource type to Google Project.
- C. Filter the Activity log to view the Data Access category. Filter the Resource type to Service Account.
- D. Filter the Activity log to view the Data Access category. Filter the Resource type to Google Project.

***My choice is A.***

Reason: Data access category will only have the details of the service accounts which and when access the data, so option should be A.

------

**Q87.(#ComputeEngine)**

You deployed an LDAP server on Compute Engine that is reachable via TLS through port 636 using UDP. You want to make sure it is reachable by clients over that port. What should you do?

- A. Add the network tag allow-udp-636 to the VM instance running the LDAP server.
- B. Create a route called allow-udp-636 and set the next hop to be the VM instance running the LDAP server.
- C. Add a network tag of your choice to the instance. Create a firewall rule to allow ingress on UDP port 636 for that network tag.
- D. Add a network tag of your choice to the instance running the LDAP server. Create a firewall rule to allow egress on UDP port 636 for that network tag.

***My choice is C.***

Reason: A tag is simply a character string added to a tags field in a resource, such as Compute Engine virtual machine (VM) instances or instance templates. A tag is not a separate resource, so you cannot create it separately. All resources with that string are considered to have that tag. Tags enable you to make firewall rules and routes applicable to specific VM instances.

-----

**Q88.(#Billing)**

You need to set a budget alert for use of Compute Engineer services on one of the three Google Cloud Platform projects that you manage. All three projects are linked to a single billing account. What should you do?

- A. Verify that you are the project billing administrator. Select the associated billing account and create a budget and alert for the appropriate project.
- B. Verify that you are the project billing administrator. Select the associated billing account and create a budget and a custom alert.
- C. Verify that you are the project administrator. Select the associated billing account and create a budget for the appropriate project.
- D. Verify that you are project administrator. Select the associated billing account and create a budget and a custom alert.

***My choice is A.***

Reason: If you just go into the Google Cloud console, you can easily see that there's no custom alert. For Alerts, you first set the project, then the service, you have the option to select All Services if you want.

-------

**Q89.(#Plan)**

You are migrating a production-critical on-premises application that requires 96 vCPUs to perform its task. You want to make sure the application runs in a similar environment on GCP. What should you do?

- A. When creating the VM, use machine type n1-standard-96.
- B. When creating the VM, use Intel Skylake as the CPU platform.
- C. Create the VM using Compute Engine default settings. Use gcloud to modify the running instance to have 96 vCPUs.
- D. Start the VM using Compute Engine default settings, and adjust as you go based on Rightsizing Recommendations.

***My choice is A.***

Reason: https://cloud.google.com/compute/docs/machine-types.

-------

**Q90.(#CloudStorage)**

You want to configure a solution for archiving data in a Cloud Storage bucket. The solution must be cost-effective. Data with multiple versions should be archived after 30 days. Previous versions are accessed once a month for reporting. This archive data is also occasionally updated at month-end. What should you do?

- A. Add a bucket lifecycle rule that archives data with newer versions after 30 days to Coldline Storage.
- B. Add a bucket lifecycle rule that archives data with newer versions after 30 days to Nearline Storage.
- C. Add a bucket lifecycle rule that archives data from regional storage after 30 days to Coldline Storage.
- D. Add a bucket lifecycle rule that archives data from regional storage after 30 days to Nearline Storage.

***My choice is B.***

Reason: https://cloud.google.com/storage/docs/storage-classes.

































