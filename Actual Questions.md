**Q1. (#Plan)**

Every employee of your company has a Google account. Your operational team needs to manage a large number of instances on Compute Engine. Each member of this team needs only administrative access to the servers. Your security team wants to ensure that the deployment of credentials is operationally efficient and must be able to determine who accessed a given instance. What should you do?

- A. Generate a new SSH key pair. Give the private key to each member of your team. Configure the public key in the metadata of each instance.
- B. Ask each member of the team to generate a new SSH key pair and to send you their public key. Use a configuration management tool to deploy those keys on each instance.
- C. Ask each member of the team to generate a new SSH key pair and to add the public key to their Google account. Grant the ג€compute.osAdminLoginג€ role to the Google group corresponding to this team.
- D. Generate a new SSH key pair. Give the private key to each member of your team. Configure the public key as a project-wide public SSH key in your Cloud Platform project and allow project-wide public SSH keys on each instance.

***My choice is C***

Reason: Some would choose D, but D is hard to "determine who accessed a given instance", and sending private keys to users is not safe, more details see this website: https://cloud.google.com/compute/docs/instances/managing-instance-access.



**Q2.(#IP)**

You need to create a custom VPC with a single subnet. The subnet's range must be as large as possible. Which range should you use?

- A. 0.0.0.0/0
- B. 10.0.0.0/8
- C. 172.16.0.0/12
- D. 192.168.0.0/16

***My choice is B.***

Reason: The private network range is defined by IETF (Ref: https://tools.ietf.org/html/rfc1918) and adhered to by all cloud providers. The supported internal IP Address ranges are 

1. 24-bit block 10.0.0.0/8 (16777216 IP Addresses)
2. 20-bit block 172.16.0.0/12 (1048576 IP Addresses)
3. 16-bit block 192.168.0.0/16 (65536 IP Addresses)
   10.0.0.0/8 gives you the most extensive range - 16777216 IP Addresses.



**Q3. (#SQL)**

You want to select and configure a cost-effective solution for relational data on Google Cloud Platform. You are working with a small set of operational data in one geographic location. You need to support point-in-time recovery. What should you do?

- A. Select Cloud SQL (MySQL). Verify that the enable binary logging option is selected.
- B. Select Cloud SQL (MySQL). Select the create failover replicas option.
- C. Select Cloud Spanner. Set up your instance with 2 nodes.
- D. Select Cloud Spanner. Set up your instance as multi-regional.

***My choice is A.***

Reason: You must enable binary logging to use point-in-time recovery. Enabling binary logging causes a slight reduction in write performance. See details here: https://cloud.google.com/sql/docs/mysql/backup-recovery/backups



**Q4.(#Plan #FewestSteps)**

You want to configure autohealing for network load balancing for a group of Compute Engine instances that run in multiple zones, using the fewest possible steps.
You need to configure re-creation of VMs if they are unresponsive after 3 attempts of 10 seconds each. What should you do?

- A. Create an HTTP load balancer with a backend configuration that references an existing instance group. Set the health check to healthy (HTTP)
- B. Create an HTTP load balancer with a backend configuration that references an existing instance group. Define a balancing mode and set the maximum RPS to 10.
- C. Create a managed instance group. Set the Autohealing health check to healthy (HTTP)
- D. Create a managed instance group. Verify that the autoscaling setting is on.

***My choice is C.***

Reason: Using a health-check with a lb (option A) would only probe if the backend instances are receiving traffic, but won't recreate unhealthy instances which is a specific ask in the question. Reference here: https://cloud.google.com/compute/docs/tutorials/high-availability-autohealing. 



**Q5.(#Plan #FewestSteps)**

You are using multiple configurations for gcloud. You want to review the configured Kubernetes Engine cluster of an inactive configuration using the fewest possible steps. What should you do?

- A. Use gcloud config configurations describe to review the output.
- B. Use gcloud config configurations activate and gcloud config list to review the output.
- C. Use kubectl config get-contexts to review the output.
- D. Use kubectl config use-context and kubectl config view to review the output.

***My choice is D.***

Reason: https://medium.com/google-cloud/kubernetes-engine-kubectl-config-b6270d2b656c. 



**Q6.(#Plan)**

Your company uses Cloud Storage to store application backup files for disaster recovery purposes. You want to follow Google's recommended practices. Which storage option should you use?

- A. Multi-Regional Storage
- B. Regional Storage
- C. Nearline Storage
- D. Coldline Storage

***My choice is D.***

Reason: Unless a withdraw frequency is mentioned, the recommended practice by google is to use "Archive Storage". However as this is not an available option, then "Coldline Storage" is the next best solution. Reference: https://cloud.google.com/storage/docs/storage-classes#nearline.



**Q7. (#Billing)**

Several employees at your company have been creating projects with Cloud Platform and paying for it with their personal credit cards, which the company reimburses. The company wants to centralize all these projects under a single, new billing account. What should you do?

- A. Contact cloud-billing@google.com with your bank account details and request a corporate billing account for your company.
- B. Create a ticket with Google Support and wait for their call to share your credit card details over the phone.
- C. In the Google Platform Console, go to the Resource Manage and move all projects to the root Organizarion.
- D. In the Google Cloud Platform Console, create a new billing account and set up a payment method.

***My choice is D(though incomplete).***

Reason:  C is incomplete. Moving projects under an organisation doesn't change their linked billing project. https://cloud.google.com/resource-manager/docs/migrating-projects-billing. Note: The link between projects and billing accounts is preserved, irrespective of the hierarchy. When you move your existing projects into the organization they will continue to work and be billed as they used to before the migration, even if the corresponding billing account has not been migrated yet.  D is incomplete as well, after setting the billing account in the organisation you need to link the projects to the new billing account.



**Q8.(#IP)**

You have an application that looks for its licensing server on the IP 10.0.3.21. You need to deploy the licensing server on Compute Engine. You do not want to change the configuration of the application and want the application to be able to reach the licensing server. What should you do?

- A. Reserve the IP 10.0.3.21 as a static internal IP address using gcloud and assign it to the licensing server.
- B. Reserve the IP 10.0.3.21 as a static public IP address using gcloud and assign it to the licensing server.
- C. Use the IP 10.0.3.21 as a custom ephemeral IP address and assign it to the licensing server.
- D. Start the licensing server with an automatic ephemeral IP address, and then promote it to a static internal IP address.

***My choice is A.***

Reason: IP 10.0.3.21 is internal by default, and to ensure that it will be static non-changing it should be selected as static internal ip address.



**Q9.(#Plan #Deploy)**

You are deploying an application to App Engine. You want the number of instances to scale based on request rate. You need at least 3 unoccupied instances at all times. Which scaling type should you use?

- A. Manual Scaling with 3 instances.
- B. Basic Scaling with min_instances set to 3.
- C. Basic Scaling with max_instances set to 3.
- D. Automatic Scaling with min_idle_instances set to 3.

***My choice is D.***

Reason: Automatic scaling creates instances based on request rate, response latencies, and other application metrics. You can specify thresholds for each of these metrics, as well as a minimum number instances to keep running at all times. See this "App Engine calculates the number of instances necessary to serve your current application traffic based on scaling settings such as target_cpu_utilization and target_throughput_utilization. Setting min_idle_instances specifies the number of instances to run in addition to this calculated number. For example, if App Engine calculates that 5 instances are necessary to serve traffic, and min_idle_instances is set to 2, App Engine will run 7 instances (5, calculated based on traffic, plus 2 additional per min_idle_instances)." from: https://cloud.google.com/appengine/docs/standard/python/how-instances-are-managed.



**Q10.(#Plan #FewestSteps)**

You have a development project with appropriate IAM roles defined. You are creating a production project and want to have the same IAM roles on the new project, using the fewest possible steps. What should you do?

- A. Use gcloud iam roles copy and specify the production project as the destination project.
- B. Use gcloud iam roles copy and specify your organization as the destination organization.
- C. In the Google Cloud Platform Console, use the ג€˜create role from roleג€™ functionality.
- D. In the Google Cloud Platform Console, use the ג€˜create roleג€™ functionality and select all applicable permissions.

***My choice is A.***

Reason: Copy roles to a "project", not "organization" as per question. The link provided, additionally has instructions on deploying roles into projects : https://cloud.google.com/sdk/gcloud/reference/iam/roles/copy gcloud iam roles copy --source="roles/spanner.databaseAdmin" --destination=CustomSpannerDbAdmin --dest-project=PROJECT_ID.



**Q11.(#Plan)**

You need a dynamic way of provisioning VMs on Compute Engine. The exact specifications will be in a dedicated configuration file. You want to follow Google's recommended practices. Which method should you use?

- A. Deployment Manager
- B. Cloud Composer
- C. Managed Instance Group
- D. Unmanaged Instance Group

***My choice is A.***

Reason: Deployment manager can create, update and delete resources inside GCP by simply using a config file.



**Q12.(#Plan)**

You have a Dockerfile that you need to deploy on Kubernetes Engine. What should you do?

- A. Use kubectl app deploy <dockerfilename>.
- B. Use gcloud app deploy <dockerfilename>.
- C. Create a docker image from the Dockerfile and upload it to Container Registry. Create a Deployment YAML file to point to that image. Use kubectl to create the deployment with that file.
- D. Create a docker image from the Dockerfile and upload it to Cloud Storage. Create a Deployment YAML file to point to that image. Use kubectl to create the deployment with that file.

***My choice is C.***

Reason: kubectl can't deploy "DockerFile", so A and B are App Engine which doesn't satisfy the use of GKE. You use Container Registry in the e2e process of deploying Docker on GKE.



**Q13.(#Plan #FewestSteps #Deploy)**

Your development team needs a new Jenkins server for their project. You need to deploy the server using the fewest steps possible. What should you do?

- A. Download and deploy the Jenkins Java WAR to App Engine Standard.
- B. Create a new Compute Engine instance and install Jenkins through the command line interface.
- C. Create a Kubernetes cluster on Compute Engine and create a deployment with the Jenkins Docker image.
- D. Use GCP Marketplace to launch the Jenkins solution

***My choice is D.***

Reason: Marketplace is a faster way to use Jenkins.



**Q14.(#Plan)**

You need to update a deployment in Deployment Manager without any resource downtime in the deployment. Which command should you use?

- A. gcloud deployment-manager deployments create --config <deployment-config-path>
- B. gcloud deployment-manager deployments update --config <deployment-config-path>
- C. gcloud deployment-manager resources create --config <deployment-config-path>
- D. gcloud deployment-manager resources update --config <deployment-config-path>

***My choice is B.***

Reason: See this site: https://cloud.google.com/sdk/gcloud/reference/deployment-manager/deployments/update.



**Q15.(#Plan #BigQuery)**

You need to run an important query in BigQuery but expect it to return a lot of records. You want to find out how much it will cost to run the query. You are using on-demand pricing. What should you do?

- A. Arrange to switch to Flat-Rate pricing for this query, then move back to on-demand.
- B. Use the command line to run a dry run query to estimate the number of bytes read. Then convert that bytes estimate to dollars using the Pricing Calculator.
- C. Use the command line to run a dry run query to estimate the number of bytes returned. Then convert that bytes estimate to dollars using the Pricing Calculator.
- D. Run a select count (*) to get an idea of how many records your query will look through. Then convert that number of rows to dollars using the Pricing Calculator.

***My choice is B.***

Reason: see this https://cloud.google.com/bigquery/docs/estimate-costs



**Q16.(#Plan #Efficient)**

You have a single binary application that you want to run on Google Cloud Platform. You decided to automatically scale the application based on underlying infrastructure CPU usage. Your organizational policies require you to use virtual machines directly. You need to ensure that the application scaling is operationally efficient and completed as quickly as possible. What should you do?

- A. Create a Google Kubernetes Engine cluster, and use horizontal pod autoscaling to scale the application.
- B. Create an instance template, and use the template in a managed instance group with autoscaling configured.
- C. Create an instance template, and use the template in a managed instance group that scales up and down based on the time of day.
- D. Use a set of third-party tools to build automation around scaling the application up and down, based on Stackdriver CPU usage monitoring.

**My choice is B **

Reason: You have to use VM instances directly .



**Q17.(#Plan #BigQuery)**

You are analyzing Google Cloud Platform service costs from three separate projects. You want to use this information to create service cost estimates by service type, daily and monthly, for the next six months using standard query syntax. What should you do?

- A. Export your bill to a Cloud Storage bucket, and then import into Cloud Bigtable for analysis.
- B. Export your bill to a Cloud Storage bucket, and then import into Google Sheets for analysis.
- C. Export your transactions to a local file, and perform analysis with a desktop tool.
- D. Export your bill to a BigQuery dataset, and then write time window-based SQL queries for analysis.

***My choice is D.***

Reason: BigQuery is for Analytical Purpose. Export your bill to a BigQuery dataset, and then write time window-based SQL queries for analysis.

A. is Not feasible, mainly because cloud BigTable is not good for Structured Data (or Relational Data on which we can run SQL queries as per the question's requirements). BigTable is better suited for Semi Structured data and NoSQL data. 

B. also is Not Feasible because there is no use of SQL in this option, which is one of the requirements. 

C. Local file, external tools... this is automatically eliminated because the operation we need is simple, and there has to be a GCP native solution for this. We shouldn't need to rely on going out of the cloud for such a simple thing. 

check this site for more info: https://cloud.google.com/billing/docs/how-to/export-data-bigquery  and this site as well: https://medium.com/google-cloud/analyzing-google-cloud-billing-data-with-big-query-30bae1c2aae4.



**Q18.(#Plan #Policy)**

You need to set up a policy so that videos stored in a specific Cloud Storage Regional bucket are moved to Coldline after 90 days, and then deleted after one year from their creation. How should you set up the policy?

- A. Use Cloud Storage Object Lifecycle Management using Age conditions with SetStorageClass and Delete actions. Set the SetStorageClass action to 90 days and the Delete action to 275 days (365 ג€" 90)
- B. Use Cloud Storage Object Lifecycle Management using Age conditions with SetStorageClass and Delete actions. Set the SetStorageClass action to 90 days and the Delete action to 365 days.
- C. Use gsutil rewrite and set the Delete action to 275 days (365-90).
- D. Use gsutil rewrite and set the Delete action to 365 days.

***My choice is B.***

Reason: From GCP : "The Age condition is satisfied when an object reaches the specified age (in days). Age is measured from the object's creation time. For example, if an object's creation time is 2019/01/10 10:00 UTC and the Age condition is 10 days, then the condition is satisfied for the object on and after 2019/01/20 10:00 UTC. This is true even if the object becomes noncurrent through Object Versioning sometime after its creation." See this site: https://cloud.google.com/storage/docs/lifecycle.



**Q19.(#Plan #ServiceAccount #CloudSQL #VM)**

You have a Linux VM that must connect to Cloud SQL. You created a service account with the appropriate access rights. You want to make sure that the VM uses this service account instead of the default Compute Engine service account. What should you do?

- A. When creating the VM via the web console, specify the service account under the ג€˜Identity and API Accessג€™ section.
- B. Download a JSON Private Key for the service account. On the Project Metadata, add that JSON as the value for the key compute-engine-service- account.
- C. Download a JSON Private Key for the service account. On the Custom Metadata of the VM, add that JSON as the value for the key compute-engine- service-account.
- D. Download a JSON Private Key for the service account. After creating the VM, ssh into the VM and save the JSON under ~/.gcloud/compute-engine-service- account.json.

***My choice is A.***

Reason: "To change an instance's service account and access scopes, the instance must be temporarily stopped ... After changing the service account or access scopes, remember to restart the instance." So we can stop the instance, change the service account, then start it up again. See this:https://cloud.google.com/compute/docs/access/create-enable-service-accounts-for-instances#changeserviceaccountandscopes. 



**Q20.(#Plan #FewestSteps)**

You created an instance of SQL Server 2017 on Compute Engine to test features in the new version. You want to connect to this instance using the fewest number of steps. What should you do?

- A. Install a RDP client on your desktop. Verify that a firewall rule for port 3389 exists.
- B. Install a RDP client in your desktop. Set a Windows username and password in the GCP Console. Use the credentials to log in to the instance.
- C. Set a Windows password in the GCP Console. Verify that a firewall rule for port 22 exists. Click the RDP button in the GCP Console and supply the credentials to log in.
- D. Set a Windows username and password in the GCP Console. Verify that a firewall rule for port 3389 exists. Click the RDP button in the GCP Console, and supply the credentials to log in.

***My choice is B.***

Reason: The default network is pre-populated with firewall rules that allow incoming connections to instances. These rules can be deleted or modified as necessary: default-allow-rdp Allows ingress connections on TCP port 3389 from any source to any instance in the network. This rule has a priority of 65534, and it enables connections to instances running the Microsoft Remote Desktop Protocol (RDP).  For testing we can assume Firewall rules are left to defaults. See this:  https://cloud.google.com/vpc/docs/firewalls. And this: https://medium.com/falafel-software/sql-server-in-the-google-cloud-a17e8a1f11ce.  



**Q21.(#Plan)**

You have one GCP account running in your default region and zone and another account running in a non-default region and zone. You want to start a new
Compute Engine instance in these two Google Cloud Platform accounts using the command line interface. What should you do?

- A. Create two configurations using gcloud config configurations create [NAME]. Run gcloud config configurations activate [NAME] to switch between accounts when running the commands to start the Compute Engine instances.
- B. Create two configurations using gcloud config configurations create [NAME]. Run gcloud configurations list to start the Compute Engine instances.
- C. Activate two configurations using gcloud configurations activate [NAME]. Run gcloud config list to start the Compute Engine instances.
- D. Activate two configurations using gcloud configurations activate [NAME]. Run gcloud configurations list to start the Compute Engine instances.

***My choice is A.***

Reason: See this:https://cloud.google.com/sdk/docs/configurations#activating_a_configuration



**Q22.(#Plan)**

You significantly changed a complex Deployment Manager template and want to confirm that the dependencies of all defined resources are properly met before committing it to the project. You want the most rapid feedback on your changes. What should you do?

- A. Use granular logging statements within a Deployment Manager template authored in Python.
- B. Monitor activity of the Deployment Manager execution on the Stackdriver Logging page of the GCP Console.
- C. Execute the Deployment Manager template against a separate project with the same configuration, and monitor for failures.
- D. Execute the Deployment Manager template using the ג€"-preview option in the same project, and observe the state of interdependent resources.

***My choice is D.***

Reason: https://cloud.google.com/deployment-manager/docs/deployments/updating-deployments. 



**Q23.(#Plan #CloudPub/Sub #CloudDataflow #CloudBigtable #BigQuery)**

![Q23](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q23.png)

***My choice is D.***

Reason: https://cloud.google.com/solutions/correlating-time-series-dataflow.



**Q24.(#Plan)**

You have a project for your App Engine application that serves a development environment. The required testing has succeeded and you want to create a new project to serve as your production environment. What should you do?

- A. Use gcloud to create the new project, and then deploy your application to the new project.
- B. Use gcloud to create the new project and to copy the deployed application to the new project.
- C. Create a Deployment Manager configuration file that copies the current App Engine deployment into a new project.
- D. Deploy your application again using gcloud and specify the project parameter with the new project name to create the new project.

***My choice is A.***

Reason: Just need to create the new project and in console make sure set the config to new project. cloud projects create <new-project-name> gcloud deployment-manager deployments create <deployment-name>.



**Q25.(#Plan #IAM #BigQuery)**

You need to configure IAM access audit logging in BigQuery for external auditors. You want to follow Google-recommended practices. What should you do?

- A. Add the auditors group to the ג€˜logging.viewerג€™ and ג€˜bigQuery.dataViewerג€™ predefined IAM roles.
- B. Add the auditors group to two new custom IAM roles.
- C. Add the auditor user accounts to the ג€˜logging.viewerג€™ and ג€˜bigQuery.dataViewerג€™ predefined IAM roles.
- D. Add the auditor user accounts to two new custom IAM roles.

***My choice is A.***

Reason: Google always recommends adding users to a group and then giving the group access. Additionally, Google recommends to use predefined roles since they have been well thought out when created, and are there to save companies the hassle of having to know what granular access every single person needs.



**Q26.(#Plan #IAM #CloudStorage)**

You need to set up permissions for a set of Compute Engine instances to enable them to write data into a particular Cloud Storage bucket. You want to follow
Google-recommended practices. What should you do?

- A. Create a service account with an access scope. Use the access scope ג€˜https://www.googleapis.com/auth/devstorage.write_onlyג€™.
- B. Create a service account with an access scope. Use the access scope ג€˜https://www.googleapis.com/auth/cloud-platformג€™.
- C. Create a service account and add it to the IAM role ג€˜storage.objectCreatorג€™ for that bucket.
- D. Create a service account and add it to the IAM role ג€˜storage.objectAdminג€™ for that bucket.

***My choice is C.***

Reason: According to Best Practices in this Google Doc (https://cloud.google.com/compute/docs/access/create-enable-service-accounts-for-instances#best_practices) you grant the instance the scope and the permissions are determined by the IAM roles of the service account. In this case, you would grant the instance the scope and the role (storage.objectCreator) to the service account.



**Q27.(#Plan #FewestSteps #CloudStorage)**

You have sensitive data stored in three Cloud Storage buckets and have enabled data access logging. You want to verify activities for a particular user for these buckets, using the fewest possible steps. You need to verify the addition of metadata labels and which files have been viewed from those buckets. What should you do?

- A. Using the GCP Console, filter the Activity log to view the information.
- B. Using the GCP Console, filter the Stackdriver log to view the information.
- C. View the bucket in the Storage section of the GCP Console.
- D. Create a trace in Stackdriver to view the information.

***My choice is A.***

Reason: From documentation---Admin Activity audit logs contain log entries for API calls or other actions that modify the configuration or metadata of resources. For example, these logs record when users create VM instances or change Identity and Access Management permissions.



**Q28.(#IAM #CloudStorage)**

You are the project owner of a GCP project and want to delegate control to colleagues to manage buckets and files in Cloud Storage. You want to follow Google- recommended practices. Which IAM roles should you grant your colleagues?

- A. Project Editor
- B. Storage Admin
- C. Storage Object Admin
- D. Storage Object Creator

***My choice is B.***

Reason: Storage Admin (roles/storage.admin) Grants full control of buckets and objects. When applied to an individual bucket, control applies only to the specified bucket and objects within the bucket. 



Q29.(#Plan #CloudStorage)





























