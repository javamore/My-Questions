### **Q179.**

Your company has a Google Cloud project that uses BigQuery for data warehousing. There are some tables that contain personally identifiable information (PII).
Only the compliance team may access the PII. The other information in the tables must be available to the data science team. You want to minimize cost and the time it takes to assign appropriate access to the tables. What should you do?

- A. 1. From the dataset where you have the source data, create views of tables that you want to share, excluding PII. 2. Assign an appropriate project-level IAM role to the members of the data science team. 3. Assign access controls to the dataset that contains the view.
- B. 1. From the dataset where you have the source data, create materialized views of tables that you want to share, excluding PII. 2. Assign an appropriate project-level IAM role to the members of the data science team. 3. Assign access controls to the dataset that contains the view.
- C. 1. Create a dataset for the data science team. 2. Create views of tables that you want to share, excluding PII. 3. Assign an appropriate project-level IAM role to the members of the data science team. 4. Assign access controls to the dataset that contains the view. 5. Authorize the view to access the source dataset.
- D. 1. Create a dataset for the data science team. 2. Create materialized views of tables that you want to share, excluding PII. 3. Assign an appropriate project-level IAM role to the members of the data science team. 4. Assign access controls to the dataset that contains the view. 5. Authorize the view to access the source dataset.

***My choice is C.***

Reason: https://cloud.google.com/bigquery/docs/share-access-views#create_a_dataset_where_you_can_store_your_view. 

------

### **Q180.**

Your operations team currently stores 10 TB of data in an object storage service from a third-party provider. They want to move this data to a Cloud Storage bucket as quickly as possible, following Google-recommended practices. They want to minimize the cost of this data migration. Which approach should they use?

- A. Use the gsutil mv command to move the data.
- B. Use the Storage Transfer Service to move the data.
- C. Download the data to a Transfer Appliance, and ship it to Google.
- D. Download the data to the on-premises data center, and upload it to the Cloud Storage bucket.

***My choice is B.***

Reason: no.

-----

### **Q181.**

You have a Compute Engine managed instance group that adds and removes Compute Engine instances from the group in response to the load on your application. The instances have a shutdown script that removes REDIS database entries associated with the instance. You see that many database entries have not been removed, and you suspect that the shutdown script is the problem. You need to ensure that the commands in the shutdown script are run reliably every time an instance is shut down. You create a Cloud Function to remove the database entries. What should you do next?

- A. Modify the shutdown script to wait for 30 seconds before triggering the Cloud Function.
- B. Do not use the Cloud Function. Modify the shutdown script to restart if it has not completed in 30 seconds.
- C. Set up a Cloud Monitoring sink that triggers the Cloud Function after an instance removal log message arrives in Cloud Logging.
- D. Modify the shutdown script to wait for 30 seconds and then publish a message to a Pub/Sub queue.

***My choice is C .*** 

Reason:  One way to do this is by setting up a Cloud Monitoring sink that triggers a Cloud Function after an instance removal log message arrives in Cloud Logging. This will allow you to use the Cloud Function to perform the necessary tasks (such as removing database entries) when an instance is shut down, and it will ensure that these tasks are performed reliably and consistently.

-----

### **Q182.**

You are managing several projects on Google Cloud and need to interact on a daily basis with BigQuery, Bigtable, and Kubernetes Engine using the gcloud CL tool. You are travelling a lot and work on different workstations during the week. You want to avoid having to manage the gcloud CLI manually. What should you do?

- A. Use Google Cloud Shell in the Google Cloud Console to interact with Google Cloud.
- B. Create a Compute Engine instance and install gcloud on the instance. Connect to this instance via SSH to always use the same gcloud installation when interacting with Google Cloud.
- C. Install gcloud on all of your workstations. Run the command gcloud components auto-update on each workstation
- D. Use a package manager to install gcloud on your workstations instead of installing it manually.

***My choice is A.***

Reason:  A is best one.

-----

### **Q183.**

Your company recently acquired a company that has infrastructure in Google Cloud. Each company has its own Google Cloud organization. Each company is using a Shared Virtual Private Cloud (VPC) to provide network connectivity for its applications. Some of the subnets used by both companies overlap. In order for both businesses to integrate, the applications need to have private network connectivity. These applications are not on overlapping subnets. You want to provide connectivity with minimal re-engineering. What should you do?

- A. Set up VPC peering and peer each Shared VPC together.
- B. Migrate the projects from the acquired company into your company's Google Cloud organization. Re-launch the instances in your companies Shared VPC.
- C. Set up a Cloud VPN gateway in each Shared VPC and peer Cloud VPNs.
- D. Configure SSH port forwarding on each application to provide connectivity between applications in the different Shared VPCs.

***My choice is C.***

Reason:  A is wrong because you cannot peer VPCs with overlapping subnets: https://cloud.google.com/vpc/docs/vpc-peering#interaction-subnet-subnet.

-----

### **Q184.**

You are managing several internal applications that are deployed on Compute Engine. Business users inform you that an application has become very slow over the past few days. You want to find the underlying cause in order to solve the problem. What should you do first?

- A. Inspect the logs and metrics from the instances in Cloud Logging and Cloud Monitoring.
- B. Change the Compute Engine Instances behind the application to a machine type with more CPU and memory.
- C. Restore a backup of the application database from a time before the application became slow.
- D. Deploy the applications on a managed instance group with autoscaling enabled. Add a load balancer in front of the managed instance group, and have the users connect to the IP of the load balancer.

***My choice is A.***

Reason: nope.

----

### **Q185.**

Your company has an application running as a Deployment in a Google Kubernetes Engine (GKE) cluster. When releasing new versions of the application via a rolling deployment, the team has been causing outages. The root cause of the outages is misconfigurations with parameters that are only used in production. You want to put preventive measures for this in the platform to prevent outages. What should you do?

- A. Configure liveness and readiness probes in the Pod specification.
- B. Configure health checks on the managed instance group.
- C. Create a Scheduled Task to check whether the application is available.
- D. Configure an uptime alert in Cloud Monitoring.

***My choice is A.***

Reason:  Liveness probes are used to determine whether a Pod is running, and readiness probes are used to determine whether a Pod is able to receive traffic.

By configuring liveness and readiness probes in the Pod specification, you can help to prevent outages when releasing new versions of the application via a rolling deployment. If a Pod fails a liveness or readiness probe, it will be restarted, which can help to prevent issues caused by misconfigured parameters or other problems.

----

### **Q186.**

Your company uses Google Kubernetes Engine (GKE) as a platform for all workloads. Your company has a single large GKE cluster that contains batch, stateful, and stateless workloads. The GKE cluster is configured with a single node pool with 200 nodes. Your company needs to reduce the cost of this cluster but does not want to compromise availability. What should you do?

- A. Create a second GKE cluster for the batch workloads only. Allocate the 200 original nodes across both clusters.
- B. Configure CPU and memory limits on the namespaces in the cluster. Configure all Pods to have a CPU and memory limits.
- C. Configure a HorizontalPodAutoscaler for all stateless workloads and for all compatible stateful workloads. Configure the cluster to use node auto scaling.
- D. Change the node pool to use preemptible VMs.

***My choice is C.***

Reason: nope.

---

### **Q187.**

Your company has a Google Cloud project that uses BigQuery for data warehousing on a pay-per-use basis. You want to monitor queries in real time to discover the most costly queries and which users spend the most. What should you do?

- A. 1. In the BigQuery dataset that contains all the tables to be queried, add a label for each user that can launch a query. 2. Open the Billing page of the project. 3. Select Reports. 4. Select BigQuery as the product and filter by the user you want to check.
- B. 1. Create a Cloud Logging sink to export BigQuery data access logs to BigQuery. 2. Perform a BigQuery query on the generated table to extract the information you need.
- C. 1. Create a Cloud Logging sink to export BigQuery data access logs to Cloud Storage. 2. Develop a Dataflow pipeline to compute the cost of queries split by users.
- D. 1. Activate billing export into BigQuery. 2. Perform a BigQuery query on the billing table to extract the information you need.

***My choice is C.***

Reason: nope.

---

### **Q188.**

Your company and one of its partners each have a Google Cloud project in separate organizations. Your company's project (prj-a) runs in Virtual Private Cloud(vpc-a). The partner's project (prj-b) runs in vpc-b. There are two instances running on vpc-a and one instance running on vpc-b. Subnets defined in both VPCs are not overlapping. You need to ensure that all instances communicate with each other via internal IPs, minimizing latency and maximizing throughput. What should you do?

- A. Set up a network peering between vpc-a and vpc-b.
- B. Set up a VPN between vpc-a and vpc-b using Cloud VPN.
- C. Configure IAP TCP forwarding on the instance in vpc-b, and then launch the following gcloud command from one of the instances in vpc-a gcloud: gcloud compute start-iap-tunnel INSTANCE_NAME_IN_VPC_8 22 \ --local-host-port=localhost:22
- D. 1. Create an additional instance in vpc-a. 2. Create an additional instance in vpc-b. 3. Install OpenVPN in newly created instances. 4. Configure a VPN tunnel between vpc-a and vpc-b with the help of OpenVPN.

***My choice is A.***

Reason: A is OK.

-------

### **Q189.**

You want to store critical business information in Cloud Storage buckets. The information is regularly changed, but previous versions need to be referenced on a regular basis. You want to ensure that there is a record of all changes to any information in these buckets. You want to ensure that accidental edits or deletions can be easily rolled back. Which feature should you enable?

- A. Bucket Lock
- B. Object Versioning
- C. Object change notification
- D. Object Lifecycle Management

***My choice is B.***

Reason: NO REASON.

----

### **Q190.**

You have a Compute Engine application that you want to autoscale when total memory usage exceeds 80%. You have installed the Cloud Monitoring agent and configured the autoscaling policy as follows:
✑ Metric identifier: agent.googleapis.com/memory/percent_used
✑ Filter: metric.label.state = 'used'
✑ Target utilization level: 80
✑ Target type: GAUGE
You observe that the application does not scale under high load. You want to resolve this. What should you do?

- A. Change the Target type to DELTA_PER_MINUTE.
- B. Change the Metric identifier to agent.googleapis.com/memory/bytes_used.
- C. Change the filter to metric.label.state = 'used' AND metric.label.state = 'buffered' AND metric.label.state = 'cached' AND metric.label.state = 'slab'.
- D. Change the filter to metric.label.state = 'free' and the Target utilization to 20.

***My choice is C.***

Reason: nope.

----

### **Q191.**

You are deploying an application to Google Cloud. The application is part of a system. The application in Google Cloud must communicate over a private network with applications in a non-Google Cloud environment. The expected average throughput is 200 kbps. The business requires:
✑ as close to 100% system availability as possible
✑ cost optimization
You need to design the connectivity between the locations to meet the business requirements. What should you provision?

- A. An HA Cloud VPN gateway connected with two tunnels to an on-premises VPN gateway
- B. Two Classic Cloud VPN gateways connected to two on-premises VPN gateways Configure each Classic Cloud VPN gateway to have two tunnels, each connected to different on-premises VPN gateways
- C. Two HA Cloud VPN gateways connected to two on-premises VPN gateways Configure each HA Cloud VPN gateway to have two tunnels, each connected to different on-premises VPN gateways
- D. A single Cloud VPN gateway connected to an on-premises VPN gateway

***My choice is C.***

Reason: 

A - Not Correct as it was working before with same ISP. 

B - New code update caused an issue- why to open support ticket. 

C - I agree with C. 

D - This requires downtime and live prod affected too.

----





















































