**Q151(#VPC)**

You are working with a user to set up an application in a new VPC behind a firewall. The user is concerned about data egress. You want to configure the fewest open egress ports. What should you do?

- A. Set up a low-priority (65534) rule that blocks all egress and a high-priority rule (1000) that allows only the appropriate ports.
- B. Set up a high-priority (1000) rule that pairs both ingress and egress ports.
- C. Set up a high-priority (1000) rule that blocks all egress and a low-priority (65534) rule that allows only the appropriate ports.
- D. Set up a high-priority (1000) rule to allow the appropriate ports.

***My choice is A.***

Reason: Every VPC network has two implied firewall rules. These rules exist, but are not shown in the Cloud Console: Implied allow egress rule, Implied deny ingress rule if a higher priority firewall rule may restrict outbound access, A is the answer.

Firewall rules are executed based on the priority. 

See this:https://cloud.google.com/vpc/docs/firewalls#priority_order_for_firewall_rules. 

-----

**Q152.(#IAM)**

Your company runs its Linux workloads on Compute Engine instances. Your company will be working with a new operations partner that does not use Google
Accounts. You need to grant access to the instances to your operations partner so they can maintain the installed tooling. What should you do?

- A. Enable Cloud IAP for the Compute Engine instances, and add the operations partner as a Cloud IAP Tunnel User.
- B. Tag all the instances with the same network tag. Create a firewall rule in the VPC to grant TCP access on port 22 for traffic from the operations partner to instances with the network tag.
- C. Set up Cloud VPN between your Google Cloud VPC and the internal network of the operations partner.
- D. Ask the operations partner to generate SSH key pairs, and add the public keys to the VM instances.

***My choice is D.***

Reason: To give a user the ability to connect to a VM instance using SSH without granting them the ability to manage Compute Engine resources, [add the user's public key](https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys) to the project, or add a user's public key to a specific instance. Using this method, you can avoid adding a user as a project member, while still granting them access to specific instances.  https://cloud.google.com/compute/docs/access#granting_users_ssh_access_to_vm_instances.

-----

**Q153(#CloudStorage)**

You have created a code snippet that should be triggered whenever a new file is uploaded to a Cloud Storage bucket. You want to deploy this code snippet. What should you do?

- A. Use App Engine and configure Cloud Scheduler to trigger the application using Pub/Sub.
- B. Use Cloud Functions and configure the bucket as a trigger resource.
- C. Use Google Kubernetes Engine and configure a CronJob to trigger the application using Pub/Sub.
- D. Use Dataflow as a batch job, and configure the bucket as a data source.

***My choice is B.***

Reason: Cloud Functions can respond to change notifications emerging from Google Cloud Storage. These notifications can be configured to trigger in response to various events inside a bucket—object creation, deletion, archiving and metadata updates.

Note: Cloud Functions can only be triggered by Cloud Storage buckets in the same Google Cloud Platform project. Event types Cloud Storage events used by Cloud Functions are based on Cloud Pub/Sub Notifications for Google Cloud Storage and can be configured in a similar way.

https://cloud.google.com/functions/docs/calling/storage#event_types. 

----

**Q154.(ObjectLifecycleManagement)**

You have been asked to set up Object Lifecycle Management for objects stored in storage buckets. The objects are written once and accessed frequently for 30 days. After 30 days, the objects are not read again unless there is a special need. The objects should be kept for three years, and you need to minimize cost.
What should you do?

- A. Set up a policy that uses Nearline storage for 30 days and then moves to Archive storage for three years.
- B. Set up a policy that uses Standard storage for 30 days and then moves to Archive storage for three years.
- C. Set up a policy that uses Nearline storage for 30 days, then moves the Coldline for one year, and then moves to Archive storage for two years.
- D. Set up a policy that uses Standard storage for 30 days, then moves to Coldline for one year, and then moves to Archive storage for two years.

***My choice is B.***

Reason: Standard Storage because of  " ` frequently accesses`".  

Archive Storage is for "`the objects are not read again unless there is a special need`".

-----

**Q155.(#CloudAuditLogs)**

You are storing sensitive information in a Cloud Storage bucket. For legal reasons, you need to be able to record all requests that read any of the stored data. You want to make sure you comply with these requirements. What should you do?

- A. Enable the Identity Aware Proxy API on the project.
- B. Scan the bucket using the Data Loss Prevention API.
- C. Allow only a single Service Account access to read the data.
- D. Enable Data Access audit logs for the Cloud Storage API.

***My choice is D.***

Reason: https://cloud.google.com/storage/docs/audit-logs#types.

----

**Q156.(#Budget)**

You are the team lead of a group of 10 developers. You provided each developer with an individual Google Cloud Project that they can use as their personal sandbox to experiment with different Google Cloud solutions. You want to be notified if any of the developers are spending above $500 per month on their sandbox environment. What should you do?

- A. Create a single budget for all projects and configure budget alerts on this budget.
- B. Create a separate billing account per sandbox project and enable BigQuery billing exports. Create a Data Studio dashboard to plot the spending per billing account.
- C. Create a budget per project and configure budget alerts on all of these budgets.
- D. Create a single billing account for all sandbox projects and enable BigQuery billing exports. Create a Data Studio dashboard to plot the spending per project.

***My choice is C.***

Reason: See this: https://cloud.google.com/billing/docs/how-to/budgets.

-----

**Q157.**

You are deploying a production application on Compute Engine. You want to prevent anyone from accidentally destroying the instance by clicking the wrong button. What should you do?

- A. Disable the flag ג€Delete boot disk when instance is deleted.ג€
- B. Enable delete protection on the instance.
- C. Disable Automatic restart on the instance.
- D. Enable Preemptibility on the instance.

***My choice is B.***

Reason: See this: https://googlecloudplatform.uservoice.com/forums/302595-compute-engine/suggestions/14227521-set-delete-boot-disk-when-instance-is-deleted-to. 

---

**Q158.(#IAM)**

Your company uses a large number of Google Cloud services centralized in a single project. All teams have specific projects for testing and development. The
DevOps team needs access to all of the production services in order to perform their job. You want to prevent Google Cloud product changes from broadening their permissions in the future. You want to follow Google-recommended practices. What should you do?

- A. Grant all members of the DevOps team the role of Project Editor on the organization level.
- B. Grant all members of the DevOps team the role of Project Editor on the production project.
- C. Create a custom role that combines the required permissions. Grant the DevOps team the custom role on the production project.
- D. Create a custom role that combines the required permissions. Grant the DevOps team the custom role on the organization level.

***My choice is C.***

Reason: Key Point: Custom roles enable you to enforce the principle of least privilege, ensuring that the user and service accounts in your organization have only the permissions essential to performing their intended functions.  When you create a custom role, you must choose an organization or project to create it in. You can then grant the custom role on the organization or project, as well as any resources within that organization or project. See this:https://cloud.google.com/iam/docs/understanding-custom-roles#basic_concepts.  

-----

**Q159.(#Design)**

You are building an application that processes data files uploaded from thousands of suppliers. Your primary goals for the application are data security and the expiration of aged data. You need to design the application to:
\* Restrict access so that suppliers can access only their own data.
\* Give suppliers write access to data only for 30 minutes.
\* Delete data that is over 45 days old.
You have a very short development cycle, and you need to make sure that the application requires minimal maintenance. Which two strategies should you use?
(Choose two.)

- A. Build a lifecycle policy to delete Cloud Storage objects after 45 days.
- B. Use signed URLs to allow suppliers limited time access to store their objects.
- C. Set up an SFTP server for your application, and create a separate user for each supplier.
- D. Build a Cloud function that triggers a timer of 45 days to delete objects that have expired.
- E. Develop a script that loops through all Cloud Storage buckets and deletes any buckets that are older than 45 days.

***My choice is A&B.***

Reason: https://cloud.google.com/storage/docs/access-control/signed-urls.

-----

**Q160.(#CloudDeploymentManager)**

Your company wants to standardize the creation and management of multiple Google Cloud resources using Infrastructure as Code. You want to minimize the amount of repetitive code needed to manage the environment. What should you do?

- A. Develop templates for the environment using Cloud Deployment Manager.
- B. Use curl in a terminal to send a REST request to the relevant Google API for each individual resource.
- C. Use the Cloud Console interface to provision and manage all related resources.
- D. Create a bash script that contains all requirement steps as gcloud commands.

***My choice is A.***

Reason: https://cloud.google.com/deployment-manager/docs/fundamentals. 
(see templates)

-----

**Q161.(#IAM)**

You are performing a monthly security check of your Google Cloud environment and want to know who has access to view data stored in your Google Cloud
Project. What should you?

- A. Enable Audit Logs for all APIs that are related to data storage.
- B. Review the IAM permissions for any role that allows for data access.
- C. Review the Identity-Aware Proxy settings for each resource.
- D. Create a Data Loss Prevention job.

***My choice is B.***

Reason: See this: https://cloud.google.com/compute/docs/access.

----

**Q162.**

Your company has embraced a hybrid cloud strategy where some of the applications are deployed on Google Cloud. A Virtual Private Network (VPN) tunnel connects your Virtual Private Cloud (VPC) in Google Cloud with your company's on-premises network. Multiple applications in Google Cloud need to connect to an on-premises database server, and you want to avoid having to change the IP configuration in all of your applications when the IP of the database changes.
What should you do?

- A. Configure Cloud NAT for all subnets of your VPC to be used when egressing from the VM instances.
- B. Create a private zone on Cloud DNS, and configure the applications with the DNS name.
- C. Configure the IP of the database as custom metadata for each instance, and query the metadata server.
- D. Query the Compute Engine internal DNS from the applications to retrieve the IP of the database.

***My choice is B.***

Reason: https://gcloud.devoteam.com/blog/google-cloud-platform-dns-forwarding-big-thing-enterprises. 

-----

**Q163.**

You have developed a containerized web application that will serve internal colleagues during business hours. You want to ensure that no costs are incurred outside of the hours the application is used. You have just created a new Google Cloud project and want to deploy the application. What should you do?

- A. Deploy the container on Cloud Run for Anthos, and set the minimum number of instances to zero.
- B. Deploy the container on Cloud Run (fully managed), and set the minimum number of instances to zero.
- C. Deploy the container on App Engine flexible environment with autoscaling, and set the value min_instances to zero in the app.yaml.
- D. Deploy the container on App Engine flexible environment with manual scaling, and set the value instances to zero in the app.yaml.

***My choice is B.***

Reason: Your workloads are automatically scaled out or in to zero depending on the traffic to your app. You only pay when your app is running, billed to the nearest 100 milliseconds.

----

**Q164.(#Billing)**

You have experimented with Google Cloud using your own credit card and expensed the costs to your company. Your company wants to streamline the billing process and charge the costs of your projects to their monthly invoice. What should you do?

- A. Grant the financial team the IAM role of ג€Billing Account Userג€ on the billing account linked to your credit card.
- B. Set up BigQuery billing export and grant your financial department IAM access to query the data.
- C. Create a ticket with Google Billing Support to ask them to send the invoice to your company.
- D. Change the billing account of your projects to the billing account of your company.

***My choice is D.***

Reason: See this: https://cloud.google.com/billing/docs/how-to/modify-project#change_the_billing_account_for_a_project. 

-----

**Q165.(#BigQuery)**

You are running a data warehouse on BigQuery. A partner company is offering a recommendation engine based on the data in your data warehouse. The partner company is also running their application on Google Cloud. They manage the resources in their own project, but they need access to the BigQuery dataset in your project. You want to provide the partner company with access to the dataset. What should you do?

- A. Create a Service Account in your own project, and grant this Service Account access to BigQuery in your project.
- B. Create a Service Account in your own project, and ask the partner to grant this Service Account access to BigQuery in their project.
- C. Ask the partner to create a Service Account in their project, and have them give the Service Account access to BigQuery in their project.
- D. Ask the partner to create a Service Account in their project, and grant their Service Account access to the BigQuery dataset in your project.

***My choice is D.***

-----

**Q166.(#CloudRun)**

Your web application has been running successfully on Cloud Run for Anthos. You want to evaluate an updated version of the application with a specific percentage of your production users (canary deployment). What should you do?

- A. Create a new service with the new version of the application. Split traffic between this version and the version that is currently running.
- B. Create a new revision with the new version of the application. Split traffic between this version and the version that is currently running.
- C. Create a new service with the new version of the application. Add HTTP Load Balancer in front of both services.
- D. Create a new revision with the new version of the application. Add HTTP Load Balancer in front of both revisions.

***My choice is B.***

Reason: See this:  https://cloud.google.com/run/docs/managing/revisions. 

------

**Q167.**

Your company developed a mobile game that is deployed on Google Cloud. Gamers are connecting to the game with their personal phones over the Internet. The game sends UDP packets to update the servers about the gamers' actions while they are playing in multiplayer mode. Your game backend can scale over multiple virtual machines (VMs), and you want to expose the VMs over a single IP address. What should you do?

- A. Configure an SSL Proxy load balancer in front of the application servers.
- B. Configure an Internal UDP load balancer in front of the application servers.
- C. Configure an External HTTP(s) load balancer in front of the application servers.
- D. Configure an External Network load balancer in front of the application servers.

***My choice is D.***

Reason: https://cloud.google.com/load-balancing/docs/choosing-load-balancer.

------

**Q168.**

You are working for a hospital that stores its medical images in an on-premises data room. The hospital wants to use Cloud Storage for archival storage of these images. The hospital wants an automated process to upload any new medical images to Cloud Storage. You need to design and implement a solution. What should you do?

- A. Create a Pub/Sub topic, and enable a Cloud Storage trigger for the Pub/Sub topic. Create an application that sends all medical images to the Pub/Sub topic.
- B. Deploy a Dataflow job from the batch template, ג€Datastore to Cloud Storage.ג€ Schedule the batch job on the desired interval.
- C. Create a script that uses the gsutil command line interface to synchronize the on-premises storage with Cloud Storage. Schedule the script as a cron job.
- D. In the Cloud Console, go to Cloud Storage. Upload the relevant images to the appropriate bucket.

***My choice is C.***

------

**Q169.**

Your auditor wants to view your organization's use of data in Google Cloud. The auditor is most interested in auditing who accessed data in Cloud Storage buckets. You need to help the auditor access the data they need. What should you do?

- A. Turn on Data Access Logs for the buckets they want to audit, and then build a query in the log viewer that filters on Cloud Storage.
- B. Assign the appropriate permissions, and then create a Data Studio report on Admin Activity Audit Logs.
- C. Assign the appropriate permissions, and the use Cloud Monitoring to review metrics.
- D. Use the export logs API to provide the Admin Activity Audit Logs in the format they want.

***My choice is A.***

----------

**Q170.**

You received a JSON file that contained a private key of a Service Account in order to get access to several resources in a Google Cloud project. You downloaded and installed the Cloud SDK and want to use this private key for authentication and authorization when performing gcloud commands. What should you do?

- A. Use the command gcloud auth login and point it to the private key.
- B. Use the command gcloud auth activate-service-account and point it to the private key.
- C. Place the private key file in the installation directory of the Cloud SDK and rename it to ג€credentials.jsonג€.
- D. Place the private key file in your home directory and rename it to ג€GOOGLE_APPLICATION_CREDENTIALSג€.

***My choice is B***

Reason: See this: https://cloud.google.com/sdk/docs/authorizing#authorizing_with_a_service_account. 

------

**Q171.(#CloudSql)**

You are working with a Cloud SQL MySQL database at your company. You need to retain a month-end copy of the database for three years for audit purposes.
What should you do?

- A. Set up an export job for the first of the month. Write the export file to an Archive class Cloud Storage bucket.
- B. Save the automatic first-of-the-month backup for three years. Store the backup file in an Archive class Cloud Storage bucket.
- C. Set up an on-demand backup for the first of the month. Write the backup to an Archive class Cloud Storage bucket.
- D. Convert the automatic first-of-the-month backup to an export file. Write the export file to a Coldline class Cloud Storage bucket.

***My choice is A.***

Reason: See this: https://cloud.google.com/sql/docs/mysql/backup-recovery/backups.

----

**Q172.(#ServiceAccount)**

You are monitoring an application and receive user feedback that a specific error is spiking. You notice that the error is caused by a Service Account having insufficient permissions. You are able to solve the problem but want to be notified if the problem recurs. What should you do?

- A. In the Log Viewer, filter the logs on severity ג€˜Errorג€™ and the name of the Service Account.
- B. Create a sink to BigQuery to export all the logs. Create a Data Studio dashboard on the exported logs.
- C. Create a custom log-based metric for the specific error to be used in an Alerting Policy.
- D. Grant Project Owner access to the Service Account.

***My choice is C.***

Reason: See this: https://cloud.google.com/logging/docs/logs-based-metrics/charts-and-alerts. 

-----

**Q173.**

You are developing a financial trading application that will be used globally. Data is stored and queried using a relational structure, and clients from all over the world should get the exact identical state of the data. The application will be deployed in multiple regions to provide the lowest latency to end users. You need to select a storage option for the application data while minimizing latency. What should you do?

- A. Use Cloud Bigtable for data storage.
- B. Use Cloud SQL for data storage.
- C. Use Cloud Spanner for data storage.
- D. Use Firestore for data storage.

***My choice is C.***

Reason: See this: https://cloud.google.com/solutions/best-practices-compute-engine-region-selection. 

----

**Q174.**

You are about to deploy a new Enterprise Resource Planning (ERP) system on Google Cloud. The application holds the full database in-memory for fast data access, and you need to configure the most appropriate resources on Google Cloud for this application. What should you do?

- A. Provision preemptible Compute Engine instances.
- B. Provision Compute Engine instances with GPUs attached.
- C. Provision Compute Engine instances with local SSDs attached.
- D. Provision Compute Engine instances with M1 machine type.

***My choice is D.***

Reason: See this: https://cloud.google.com/compute/docs/machine-types.

-----

**Q175.**

You have developed an application that consists of multiple microservices, with each microservice packaged in its own Docker container image. You want to deploy the entire application on Google Kubernetes Engine so that each microservice can be scaled individually. What should you do?

- A. Create and deploy a Custom Resource Definition per microservice.
- B. Create and deploy a Docker Compose File.
- C. Create and deploy a Job per microservice.
- D. Create and deploy a Deployment per microservice.

***My choice is D.***

-----

**Q176.(CloudAPIS)**

You will have several applications running on different Compute Engine instances in the same project. You want to specify at a more granular level the service account each instance uses when calling Google Cloud APIs. What should you do?

- A. When creating the instances, specify a Service Account for each instance.
- B. When creating the instances, assign the name of each Service Account as instance metadata.
- C. After starting the instances, use gcloud compute instances update to specify a Service Account for each instance.
- D. After starting the instances, use gcloud compute instances update to assign the name of the relevant Service Account as instance metadata.

***My choice is A.***

-----

**Q177.**

You are creating an application that will run on Google Kubernetes Engine. You have identified MongoDB as the most suitable database system for your application and want to deploy a managed MongoDB environment that provides a support SLA. What should you do?

- A. Create a Cloud Bigtable cluster, and use the HBase API.
- B. Deploy MongoDB Atlas from the Google Cloud Marketplace.
- C. Download a MongoDB installation package, and run it on Compute Engine instances.
- D. Download a MongoDB installation package, and run it on a Managed Instance Group.

***My choice is B.***

-----

**Q178.**

You are managing a project for the Business Intelligence (BI) department in your company. A data pipeline ingests data into BigQuery via streaming. You want the users in the BI department to be able to run the custom SQL queries against the latest data in BigQuery. What should you do?

- A. Create a Data Studio dashboard that uses the related BigQuery tables as a source and give the BI team view access to the Data Studio dashboard.
- B. Create a Service Account for the BI team and distribute a new private key to each member of the BI team.
- C. Use Cloud Scheduler to schedule a batch Dataflow job to copy the data from BigQuery to the BI teamג€™s internal data warehouse.
- D. Assign the IAM role of BigQuery User to a Google Group that contains the members of the BI team.

***My choice is D.***

---------

**Q179.**

Your company is moving its entire workload to Compute Engine. Some servers should be accessible through the Internet, and other servers should only be accessible over the internal network. All servers need to be able to talk to each other over specific ports and protocols. The current on-premises network relies on a demilitarized zone (DMZ) for the public servers and a Local Area Network (LAN) for the private servers. You need to design the networking infrastructure on
Google Cloud to match these requirements. What should you do?

- A. 1. Create a single VPC with a subnet for the DMZ and a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public ingress traffic for the DMZ.
- B. 1. Create a single VPC with a subnet for the DMZ and a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public egress traffic for the DMZ.
- C. 1. Create a VPC with a subnet for the DMZ and another VPC with a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public ingress traffic for the DMZ.
- D. 1. Create a VPC with a subnet for the DMZ and another VPC with a subnet for the LAN. 2. Set up firewall rules to open up relevant traffic between the DMZ and the LAN subnets, and another firewall rule to allow public egress traffic for the DMZ.

***My choice is A.***

--------



***THE END***
