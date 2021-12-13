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



**Q29.(#Plan #CloudStorage)**

You have an object in a Cloud Storage bucket that you want to share with an external company. The object contains sensitive data. You want access to the content to be removed after four hours. The external company does not have a Google account to which you can grant specific user-based access privileges. You want to use the most secure method that requires the fewest steps. What should you do?

- A. Create a signed URL with a four-hour expiration and share the URL with the company.
- B. Set object access to ג€˜publicג€™ and use object lifecycle management to remove the object after four hours.
- C. Configure the storage bucket as a static website and furnish the objectג€™s URL to the company. Delete the object from the storage bucket after four hours.
- D. Create a new Cloud Storage bucket specifically for the external company to access. Copy the object to that bucket. Delete the bucket after four hours have passed.

***My Choice is A.***

Reason: Signed URLs are used to give time-limited resource access to anyone in possession of the URL, regardless of whether they have a Google account. See this: https://cloud.google.com/storage/docs/access-control/signed-urls



**Q30.(#GKE #Plan)**

You are creating a Google Kubernetes Engine (GKE) cluster with a cluster autoscaler feature enabled. You need to make sure that each node of the cluster will run a monitoring pod that sends container metrics to a third-party monitoring solution. What should you do?

- A. Deploy the monitoring pod in a StatefulSet object.
- B. Deploy the monitoring pod in a DaemonSet object.
- C. Reference the monitoring pod in a Deployment object.
- D. Reference the monitoring pod in a cluster initializer at the GKE cluster creation time.

***My choice is B.***

Reason: B is right https://cloud.google.com/kubernetes-engine/docs/concepts/daemonset, and this:https://cloud.google.com/kubernetes-engine/docs/concepts/daemonset#usage_patterns. 



**Q31.(#CloudPub/Sub #Plan)**

You want to send and consume Cloud Pub/Sub messages from your App Engine application. The Cloud Pub/Sub API is currently disabled. You will use a service account to authenticate your application to the API. You want to make sure your application can use Cloud Pub/Sub. What should you do?

- A. Enable the Cloud Pub/Sub API in the API Library on the GCP Console.
- B. Rely on the automatic enablement of the Cloud Pub/Sub API when the Service Account accesses it.
- C. Use Deployment Manager to deploy your application. Rely on the automatic enablement of all APIs used by the application being deployed.
- D. Grant the App Engine Default service account the role of Cloud Pub/Sub Admin. Have your application enable the API on the first connection to Cloud Pub/ Sub.

***My choice is A.***

Reason: https://cloud.google.com/pubsub/docs/quickstart-console.



**Q32.(#Plan #Stackdriver)**

You need to monitor resources that are distributed over different projects in Google Cloud Platform. You want to consolidate reporting under the same Stackdriver
Monitoring dashboard. What should you do?

- A. Use Shared VPC to connect all projects, and link Stackdriver to one of the projects.
- B. For each project, create a Stackdriver account. In each project, create a service account for that project and grant it the role of Stackdriver Account Editor in all other projects.
- C. Configure a single Stackdriver account, and link all projects to the same account.
- D. Configure a single Stackdriver account for one of the projects. In Stackdriver, create a Group and add the other project names as criteria for that Group.

***My choice is C.***

Reason: It doesn't make sense to create one account for one project when you need to monitor all of them, just create one account and link them all.



**Q33.(#Plan #VM #ComputeEngine)**

You are deploying an application to a Compute Engine VM in a managed instance group. The application must be running at all times, but only a single instance of the VM should run per GCP project. How should you configure the instance group?

- A. Set autoscaling to On, set the minimum number of instances to 1, and then set the maximum number of instances to 1.
- B. Set autoscaling to Off, set the minimum number of instances to 1, and then set the maximum number of instances to 1.
- C. Set autoscaling to On, set the minimum number of instances to 1, and then set the maximum number of instances to 2.
- D. Set autoscaling to Off, set the minimum number of instances to 1, and then set the maximum number of instances to 2.

***My choice is A or B.***

Reason: This question is considering "Managed Instance Groups" and to quote the documentation "If a VM in the group stops, crashes, or is deleted by an action other than an instance group management command (for example, an intentional scale in), the MIG automatically recreates that VM in accordance with the original instance's specification (same VM name, same template) so that the VM can resume its work." This is independent of autoscaling! source: https://cloud.google.com/compute/docs/instance-groups Autoscaling is about reacting to load or traffic and being able to horizontally scale. We only have 1 VM so there is no horizontal scaling. source: https://cloud.google.com/compute/docs/autoscaler



**Q34.(#IAM #Plan)**

You want to verify the IAM users and roles assigned within a GCP project named my-project. What should you do?

- A. Run gcloud iam roles list. Review the output section.
- B. Run gcloud iam service-accounts list. Review the output section.
- C. Navigate to the project and then to the IAM section in the GCP Console. Review the members and roles.
- D. Navigate to the project and then to the Roles section in the GCP Console. Review the roles and status.

***My choice is C.***

Reason: Question talks about members and roles both. IAM section provides the list of both Members and Roles.Option A is wrong as it would provide information about the roles only.Option B is wrong as it would provide only the service accounts.Option D is wrong as it would provide information about the roles only.



**Q35.(#Plan)**

You need to create a new billing account and then link it with an existing Google Cloud Platform project. What should you do?

- A. Verify that you are Project Billing Manager for the GCP project. Update the existing project to link it to the existing billing account.
- B. Verify that you are Project Billing Manager for the GCP project. Create a new billing account and link the new billing account to the existing project.
- C. Verify that you are Billing Administrator for the billing account. Create a new project and link the new project to the existing billing account.
- D. Verify that you are Billing Administrator for the billing account. Update the existing project to link it to the existing billing account.

***My choice is B.***

Reason: For option A, The billing account has to be new (you need to CREATE it), you can't link the project to an EXISTING billing account C. The project already exists, you don't want to CREATE a new project D. Even if you are a Billing Administrator for the billing account you can't update a project billing account without having access to it + the billing account has to be new so you don't want to link the project to an existing billing account B. Project Billing Manager is required to manage the GCP project billing settings. We assume you can create a new billing account because you are an organization billing admin or because you are not part of an organization.



**Q36.(#Plan #ServiceAccount)**

You have one project called proj-sa where you manage all your service accounts. You want to be able to use a service account from this project to take snapshots of VMs running in another project called proj-vm. What should you do?

- A. Download the private key from the service account, and add it to each VMs custom metadata.
- B. Download the private key from the service account, and add the private key to each VMג€™s SSH keys.
- C. Grant the service account the IAM Role of Compute Storage Admin in the project called proj-vm.
- D. When creating the VMs, set the service accountג€™s API scope for Compute Engine to read/write.

***My choice is C.***

Reason: https://cloud.google.com/compute/docs/access/iam#compute.storageAdmin



**Q37.(#Plan #AppEngine)**

You created a Google Cloud Platform project with an App Engine application inside the project. You initially configured the application to be served from the us- central region. Now you want the application to be served from the asia-northeast1 region. What should you do?

- A. Change the default region property setting in the existing GCP project to asia-northeast1.
- B. Change the region property setting in the existing App Engine application from us-central to asia-northeast1.
- C. Create a second App Engine application in the existing GCP project and specify asia-northeast1 as the region to serve your application.
- D. Create a new GCP project and create an App Engine application inside this new project. Specify asia-northeast1 as the region to serve your application.

***My choice is D.***

Reason: Each Cloud project can contain only a single App Engine application, and once created you cannot change the location of your App Engine application. https://cloud.google.com/appengine/docs/flexible/nodejs/managing-projects-apps-billing#create.



**Q38.(#Plan #IAM)**

You need to grant access for three users so that they can view and edit table data on a Cloud Spanner instance. What should you do?

- A. Run gcloud iam roles describe roles/spanner.databaseUser. Add the users to the role.
- B. Run gcloud iam roles describe roles/spanner.databaseUser. Add the users to a new group. Add the group to the role.
- C. Run gcloud iam roles describe roles/spanner.viewer - -project my-project. Add the users to the role.
- D. Run gcloud iam roles describe roles/spanner.viewer - -project my-project. Add the users to a new group. Add the group to the role.

***My choice is B.***

Reason: We need to apply common roles for each user, so creating a group and assigning role to that group is the best practice.



**Q39.(#Plan #GKE)**

You create a new Google Kubernetes Engine (GKE) cluster and want to make sure that it always runs a supported and stable version of Kubernetes. What should you do?

- A. Enable the Node Auto-Repair feature for your GKE cluster.
- B. Enable the Node Auto-Upgrades feature for your GKE cluster.
- C. Select the latest available cluster version for your GKE cluster.
- D. Select ג€Container-Optimized OS (cos)ג€ as a node image for your GKE cluster.

***My choice is B.***

Reason: https://cloud.google.com/kubernetes-engine/versioning-and-upgrades.



**Q40.(#Plan)**

You have an instance group that you want to load balance. You want the load balancer to terminate the client SSL session. The instance group is used to serve a public web application over HTTPS. You want to follow Google-recommended practices. What should you do?

- A. Configure an HTTP(S) load balancer.
- B. Configure an internal TCP load balancer.
- C. Configure an external SSL proxy load balancer.
- D. Configure an external TCP proxy load balancer.

***My choice is A.***

Reason:  https://cloud.google.com/load-balancing/docs/choosing-load-balancer

----

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



![Q72(1)](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q72(1).png)



You deployed a new application inside your Google Kubernetes Engine cluster using the YAML file specified below.



![Q72(2)](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q72(2).png)



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

---

**Q91. (#Plan #VPC)**

- Your company's infrastructure is on-premises, but all machines are running at maximum capacity. You want to burst to Google Cloud. The workloads on Google
  Cloud must be able to directly communicate to the workloads on-premises using a private IP range. What should you do?
  - A. In Google Cloud, configure the VPC as a host for Shared VPC.
  - B. In Google Cloud, configure the VPC for VPC Network Peering.
  - C. Create bastion hosts both in your on-premises environment and on Google Cloud. Configure both as proxy servers using their public IP addresses.
  - D. Set up Cloud VPN between the infrastructure on-premises and Google Cloud.

***My choice is D.***

Reason: VPC peering only works on GCP cloud network.

------------------------

**Q92.(#CloudStorage)**

You want to select and configure a solution for storing and archiving data on Google Cloud Platform. You need to support compliance objectives for data from one geographic location. This data is archived after 30 days and needs to be accessed annually. What should you do?

- A. Select Multi-Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Coldline Storage.
- B. Select Multi-Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Nearline Storage.
- C. Select Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Nearline Storage.
- D. Select Regional Storage. Add a bucket lifecycle rule that archives data after 30 days to Coldline Storage.

***My choice is D.***

Reason: Coldline Storage is ideal for data you plan to read or modify at most once a quarter..

---------

**Q93.(#BigQuery)**

Your company uses BigQuery for data warehousing. Over time, many different business units in your company have created 1000+ datasets across hundreds of projects. Your CIO wants you to examine all datasets to find tables that contain an employee_ssn column. You want to minimize effort in performing this task.
What should you do?

- A. Go to Data Catalog and search for employee_ssn in the search box.
- B. Write a shell script that uses the bq command line tool to loop through all the projects in your organization.
- C. Write a script that loops through all the projects in your organization and runs a query on INFORMATION_SCHEMA.COLUMNS view to find the employee_ssn column.
- D. Write a Cloud Dataflow job that loops through all the projects in your organization and runs a query on INFORMATION_SCHEMA.COLUMNS view to find employee_ssn column.

***My choice is A.***

Reason:  https://cloud.google.com/data-catalog/docs/how-to/search#how_to_search_for_data_assets. 

------

**Q94.(#GKE #Deployment)**

You create a Deployment with 2 replicas in a Google Kubernetes Engine cluster that has a single preemptible node pool. After a few minutes, you use kubectl to examine the status of your Pod and observe that one of them is still in Pending status:

![Q94](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q94.png)

What is the most likely cause?

- A. The pending Pod's resource requests are too large to fit on a single node of the cluster.
- B. Too many Pods are already running in the cluster, and there are not enough resources left to schedule the pending Pod.
- C. The node pool is configured with a service account that does not have permission to pull the container image used by the pending Pod.
- D. The pending Pod was originally scheduled on a node that has been preempted between the creation of the Deployment and your verification of the Podsג€™ status. It is currently being rescheduled on a new node.

My choice is B.

Reason: https://cloud.google.com/kubernetes-engine/docs/troubleshooting#node_allocatable.

------

**Q95.(#IAM #CloudSpanner)**

You want to find out when users were added to Cloud Spanner Identity Access Management (IAM) roles on your Google Cloud Platform (GCP) project. What should you do in the GCP Console?

- A. Open the Cloud Spanner console to review configurations.
- B. Open the IAM & admin console to review IAM policies for Cloud Spanner roles.
- C. Go to the Stackdriver Monitoring console and review information for Cloud Spanner.
- D. Go to the Stackdriver Logging console, review admin activity logs, and filter them for Cloud Spanner IAM roles.

***My Choice is D.***

Reason: Go to the Stackdriver Logging console, review admin activity logs, and filter them for Cloud Spanner IAM roles.

------

**Q96.(#BigQuery #ControlCost)**

Your company implemented BigQuery as an enterprise data warehouse. Users from multiple business units run queries on this data warehouse. However, you notice that query costs for BigQuery are very high, and you need to control costs. Which two methods should you use? (Choose two.)

- A. Split the users from business units to multiple projects.
- B. Apply a user- or project-level custom query quota for BigQuery data warehouse.
- C. Create separate copies of your BigQuery data warehouse for each business unit.
- D. Split your BigQuery data warehouse into multiple data warehouses for each business unit.
- E. Change your BigQuery query model from on-demand to flat rate. Apply the appropriate number of slots to each Project.

***My choice is B and E.***

Reason: https://cloud.google.com/bigquery/docs/custom-quotas and this: https://cloud.google.com/bigquery/pricing#flat_rate_pricing. 

-----------------

**Q97.(#GKE #Pod)**

You are building a product on top of Google Kubernetes Engine (GKE). You have a single GKE cluster. For each of your customers, a Pod is running in that cluster, and your customers can run arbitrary code inside their Pod. You want to maximize the isolation between your customers' Pods. What should you do?

- A. Use Binary Authorization and whitelist only the container images used by your customersג€™ Pods.
- B. Use the Container Analysis API to detect vulnerabilities in the containers used by your customersג€™ Pods.
- C. Create a GKE node pool with a sandbox type configured to gvisor. Add the parameter runtimeClassName: gvisor to the specification of your customersג€™ Pods.
- D. Use the cos_containerd image for your GKE nodes. Add a nodeSelector with the value cloud.google.com/gke-os-distribution: cos_containerd to the specification of your customersג€™ Pods.

***My choice is C.***

Reason: see this:  https://cloud.google.com/kubernetes-engine/sandbox.

------------------

**Q98(#CloudSpanner)**

Your customer has implemented a solution that uses Cloud Spanner and notices some read latency-related performance issues on one table. This table is accessed only by their users using a primary key. The table schema is shown below.

![Q98](https://github.com/javamore/ACE-the-ACE/blob/main/images/Q98.png)

You want to resolve the issue. What should you do?

- A. Remove the profile_picture field from the table.

- B. Add a secondary index on the person_id column.

- C. Change the primary key to not have monotonically increasing values.

- D. Create a secondary index using the following Data Definition Language (DDL):

  CREATE INDEX person_id_ix

  ON Persons(

  ​			person_id,

  ​			firstname,

  ​			lastname

  ) STORING(

  ​			profile_picture

  )

***My choice is C.***

Reason: Reference URL: https://cloud.google.com/spanner/docs/schema-design and this: https://medium.com/google-cloud/cloud-spanner-choosing-the-right-primary-keys-cd2a47c7b52d.

-----

**Q99.(#Billing)**

Your finance team wants to view the billing report for your projects. You want to make sure that the finance team does not get additional permissions to the project. What should you do?

- A. Add the group for the finance team to roles/billing user role.
- B. Add the group for the finance team to roles/billing admin role.
- C. Add the group for the finance team to roles/billing viewer role.
- D. Add the group for the finance team to roles/billing project/Manager role.

***My choice is C.***

Reason: No Need.

-----

**Q100.(#SRE)**

Your organization has strict requirements to control access to Google Cloud projects. You need to enable your Site Reliability Engineers (SREs) to approve requests from the Google Cloud support team when an SRE opens a support case. You want to follow Google-recommended practices. What should you do?

- A. Add your SREs to roles/iam.roleAdmin role.
- B. Add your SREs to roles/accessapproval.approver role.
- C. Add your SREs to a group and then add this group to roles/iam.roleAdmin.role.
- D. Add your SREs to a group and then add this group to roles/accessapproval.approver role.

***My choice is D.***

Reason: https://cloud.google.com/iam/docs/understanding-roles#access-approval-roles.

----

**Q101.(#ComputeEngine)**

You need to host an application on a Compute Engine instance in a project shared with other teams. You want to prevent the other teams from accidentally causing downtime on that application. Which feature should you use?

- A. Use a Shielded VM.
- B. Use a Preemptible VM.
- C. Use a sole-tenant node.
- D. Enable deletion protection on the instance.

***My choice is D.***

Reason: https://cloud.google.com/compute/docs/instances/preventing-accidental-vm-deletion. 

---

**Q102.(#BigQuery)**

Your organization needs to grant users access to query datasets in BigQuery but prevent them from accidentally deleting the datasets. You want a solution that follows Google-recommended practices. What should you do?

- A. Add users to roles/bigquery user role only, instead of roles/bigquery dataOwner.
- B. Add users to roles/bigquery dataEditor role only, instead of roles/bigquery dataOwner.
- C. Create a custom role by removing delete permissions, and add users to that role only.
- D. Create a custom role by removing delete permissions. Add users to the group, and then add the group to the custom role.

My choice is D.

Reason: The predefined role for answer A grants the user to delete any dataset they create, as they are assigned the owner. That alone seems to remove A from consideration. B. Would work as well and may be fine if it's a single user, however, it makes sense to create the custom role in case you need to add additional users to the role. from https://cloud.google.com/bigquery/docs/access-control Additionally, allows the creation of new datasets within the project; the creator is granted the BigQuery Data Owner role (roles/bigquery.dataOwner) on these new datasets.

----

**Q103.(#Plan)**

You have a developer laptop with the Cloud SDK installed on Ubuntu. The Cloud SDK was installed from the Google Cloud Ubuntu package repository. You want to test your application locally on your laptop with Cloud Datastore. What should you do?

- A. Export Cloud Datastore data using gcloud datastore export.
- B. Create a Cloud Datastore index using gcloud datastore indexes create.
- C. Install the google-cloud-sdk-datastore-emulator component using the apt get install command.
- D. Install the cloud-datastore-emulator component using the gcloud components install command.

***My choice is C.***

Reason: https://cloud.google.com/sdk/docs/downloads-apt-get.

-----

**Q104.(#Plan)**

Your company set up a complex organizational structure on Google Cloud. The structure includes hundreds of folders and projects. Only a few team members should be able to view the hierarchical structure. You need to assign minimum permissions to these team members, and you want to follow Google-recommended practices. What should you do?

- A. Add the users to roles/browser role.
- B. Add the users to roles/iam.roleViewer role.
- C. Add the users to a group, and add this group to roles/browser.
- D. Add the users to a group, and add this group to roles/iam.roleViewer role.

***My choice is C.***

Reason: We need to apply the GCP Best practices. roles/browser Browser Read access to browse the hierarchy for a project, including the folder, organization, and IAM policy. This role doesn't include permission to view resources in the project. https://cloud.google.com/iam/docs/understanding-roles.

----

**Q105.(#CloudIdentity)**

Your company has a single sign-on (SSO) identity provider that supports Security Assertion Markup Language (SAML) integration with service providers. Your company has users in Cloud Identity. You would like users to authenticate using your company's SSO provider. What should you do?

- A. In Cloud Identity, set up SSO with Google as an identity provider to access custom SAML apps.
- B. In Cloud Identity, set up SSO with a third-party identity provider with Google as a service provider.
- C. Obtain OAuth 2.0 credentials, configure the user consent screen, and set up OAuth 2.0 for Mobile & Desktop Apps.
- D. Obtain OAuth 2.0 credentials, configure the user consent screen, and set up OAuth 2.0 for Web Server Applications.

***My choice is B.***

Reason: https://support.google.com/a/answer/6349809. When you use SSO for Cloud Identity or Google Workspace, your external IdP is the SAML IdP and Google is the SAML service provider.

-----

**Q106.(#Role)**

Your organization has a dedicated person who creates and manages all service accounts for Google Cloud projects. You need to assign this person the minimum role for projects. What should you do?

- A. Add the user to roles/iam.roleAdmin role.
- B. Add the user to roles/iam.securityAdmin role.
- C. Add the user to roles/iam.serviceAccountUser role.
- D. Add the user to roles/iam.serviceAccountAdmin role.

***My choice is D.***

Reason: Service Account Admin (roles/iam.serviceAccountAdmin): Includes permissions to list service accounts and get details about a service account. Also includes permissions to create, update, and delete service accounts, and to view or change the IAM policy on a service account.

-----

**Q107.(#CloudStorage)**

You are building an archival solution for your data warehouse and have selected Cloud Storage to archive your data. Your users need to be able to access this archived data once a quarter for some regulatory requirements. You want to select a cost-efficient option. Which storage option should you use?

- A. Coldline Storage
- B. Nearline Storage
- C. Regional Storage
- D. Multi-Regional Storage

***My choice is B***

Reason: coldline provides access once a year.

-----

**Q108.(#GKE)**

A team of data scientists infrequently needs to use a Google Kubernetes Engine (GKE) cluster that you manage. They require GPUs for some long-running, non- restartable jobs. You want to minimize cost. What should you do?

- A. Enable node auto-provisioning on the GKE cluster.
- B. Create a VerticalPodAutscaler for those workloads.
- C. Create a node pool with preemptible VMs and GPUs attached to those VMs.
- D. Create a node pool of instances with GPUs, and enable autoscaling on this node pool with a minimum size of 1.

***My choice is D.***

Reason: for long-running, non- restartable jobs you dont use preemptible VMs.

-----

**Q109.(#Plan)**

Your organization has user identities in Active Directory. Your organization wants to use Active Directory as their source of truth for identities. Your organization wants to have full control over the Google accounts used by employees for all Google services, including your Google Cloud Platform (GCP) organization. What should you do?

- A. Use Google Cloud Directory Sync (GCDS) to synchronize users into Cloud Identity.
- B. Use the cloud Identity APIs and write a script to synchronize users to Cloud Identity.
- C. Export users from Active Directory as a CSV and import them to Cloud Identity via the Admin Console.
- D. Ask each employee to create a Google account using self signup. Require that each employee use their company email address and password.

***My choice is A***

Reason: See reference:https://cloud.google.com/solutions/federating-gcp-with-active-directory-introduction.

----

**Q110.(#CloudSQL)**

You have successfully created a development environment in a project for an application. This application uses Compute Engine and Cloud SQL. Now you need to create a production environment for this application. The security team has forbidden the existence of network routes between these 2 environments and has asked you to follow Google-recommended practices. What should you do?

- A. Create a new project, enable the Compute Engine and Cloud SQL APIs in that project, and replicate the setup you have created in the development environment.
- B. Create a new production subnet in the existing VPC and a new production Cloud SQL instance in your existing project, and deploy your application using those resources.
- C. Create a new project, modify your existing VPC to be a Shared VPC, share that VPC with your new project, and replicate the setup you have in the development environment in that new project in the Shared VPC.
- D. Ask the security team to grant you the Project Editor role in an existing production project used by another division of your company. Once they grant you that role, replicate the setup you have in the development environment in that project.

***My choice is A.***

Reason: it's a best practice "to have one project per application per environment." check this site: https://cloud.google.com/docs/enterprise/best-practices-for-enterprise-organizations#project-structure.

-----

**Q111.(#Plan)**

Your management has asked an external auditor to review all the resources in a specific project. The security team has enabled the Organization Policy called
Domain Restricted Sharing on the organization node by specifying only your Cloud Identity domain. You want the auditor to only be able to view, but not modify, the resources in that project. What should you do?

- A. Ask the auditor for their Google account, and give them the Viewer role on the project.
- B. Ask the auditor for their Google account, and give them the Security Reviewer role on the project.
- C. Create a temporary account for the auditor in Cloud Identity, and give that account the Viewer role on the project.
- D. Create a temporary account for the auditor in Cloud Identity, and give that account the Security Reviewer role on the project.

***My choice is C.***

Reason: https://cloud.google.com/iam/docs/roles-audit-logging#scenario_external_auditors.

----

**Q112.**

You have a workload running on Compute Engine that is critical to your business. You want to ensure that the data on the boot disk of this workload is backed up regularly. You need to be able to restore a backup as quickly as possible in case of disaster. You also want older backups to be cleaned automatically to save on cost. You want to follow Google-recommended practices. What should you do?

- A. Create a Cloud Function to create an instance template.
- B. Create a snapshot schedule for the disk using the desired interval.
- C. Create a cron job to create a new disk from the disk using gcloud.
- D. Create a Cloud Task to create an image and export it to Cloud Storage.

***My choice is B.***

Reason: https://cloud.google.com/compute/docs/disks/snapshot-best-practices.

------

**Q113.(#IAM)**

You need to assign a Cloud Identity and Access Management (Cloud IAM) role to an external auditor. The auditor needs to have permissions to review your
Google Cloud Platform (GCP) Audit Logs and also to review your Data Access logs. What should you do?

- A. Assign the auditor the IAM role roles/logging.privateLogViewer. Perform the export of logs to Cloud Storage.
- B. Assign the auditor the IAM role roles/logging.privateLogViewer. Direct the auditor to also review the logs for changes to Cloud IAM policy.
- C. Assign the auditorג€™s IAM user to a custom role that has logging.privateLogEntries.list permission. Perform the export of logs to Cloud Storage.
- D. Assign the auditorג€™s IAM user to a custom role that has logging.privateLogEntries.list permission. Direct the auditor to also review the logs for changes to Cloud IAM policy.

***My choice is B.***

Reason: roles/logging.privateLogViewer (Private Logs Viewer) includes roles/logging.viewer, plus the ability to read Access Transparency logs and Data Access audit logs. This role applies only to the _Required and _Default buckets.

------

**Q114.**

You are managing several Google Cloud Platform (GCP) projects and need access to all logs for the past 60 days. You want to be able to explore and quickly analyze the log contents. You want to follow Google-recommended practices to obtain the combined logs for all projects. What should you do?

- A. Navigate to Stackdriver Logging and select resource.labels.project_id="*"
- B. Create a Stackdriver Logging Export with a Sink destination to a BigQuery dataset. Configure the table expiration to 60 days.
- C. Create a Stackdriver Logging Export with a Sink destination to Cloud Storage. Create a lifecycle rule to delete objects after 60 days.
- D. Configure a Cloud Scheduler job to read from Stackdriver and store the logs in BigQuery. Configure the table expiration to 60 days.

***My choice is B.*** 

Reason: https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging. 

---

**Q115.**

You need to reduce GCP service costs for a division of your company using the fewest possible steps. You need to turn off all configured services in an existing
GCP project. What should you do?

- A. 1. Verify that you are assigned the Project Owners IAM role for this project. 2. Locate the project in the GCP console, click Shut down and then enter the project ID.
- B. 1. Verify that you are assigned the Project Owners IAM role for this project. 2. Switch to the project in the GCP console, locate the resources and delete them.
- C. 1. Verify that you are assigned the Organizational Administrator IAM role for this project. 2. Locate the project in the GCP console, enter the project ID and then click Shut down.
- D. 1. Verify that you are assigned the Organizational Administrators IAM role for this project. 2. Switch to the project in the GCP console, locate the resources and delete them.

***My choice is A.***

Reason: Ref: https://cloud.google.com/resource-manager/docs/organization-resource-management#delete-projects.

-----

**Q116.(#VM)**

You are configuring service accounts for an application that spans multiple projects. Virtual machines (VMs) running in the web-applications project need access to BigQuery datasets in crm-databases-proj. You want to follow Google-recommended practices to give access to the service account in the web-applications project. What should you do?

- A. Give ג€project ownerג€ for web-applications appropriate roles to crm-databases-proj.
- B. Give ג€project ownerג€ role to crm-databases-proj and the web-applications project.
- C. Give ג€project ownerג€ role to crm-databases-proj and bigquery.dataViewer role to web-applications.
- D. Give bigquery.dataViewer role to crm-databases-proj and appropriate roles to web-applications.

***My choice is D.***

Reason: No need any Owner access permission.

---

Q117.

An employee was terminated, but their access to Google Cloud Platform (GCP) was not removed until 2 weeks later. You need to find out this employee accessed any sensitive customer information after their termination. What should you do?

- A. View System Event Logs in Stackdriver. Search for the userג€™s email as the principal.
- B. View System Event Logs in Stackdriver. Search for the service account associated with the user.
- C. View Data Access audit logs in Stackdriver. Search for the userג€™s email as the principal.
- D. View the Admin Activity log in Stackdriver. Search for the service account associated with the user.

***My choice is C.***

Reason: https://cloud.google.com/logging/docs/audit.

----

**Q118.(#IAM)**

You need to create a custom IAM role for use with a GCP service. All permissions in the role must be suitable for production use. You also want to clearly share with your organization the status of the custom role. This will be the first version of the custom role. What should you do?

- A. Use permissions in your role that use the ג€˜supportedג€™ support level for role permissions. Set the role stage to ALPHA while testing the role permissions.
- B. Use permissions in your role that use the ג€˜supportedג€™ support level for role permissions. Set the role stage to BETA while testing the role permissions.
- C. Use permissions in your role that use the ג€˜testingג€™ support level for role permissions. Set the role stage to ALPHA while testing the role permissions.
- D. Use permissions in your role that use the ג€˜testingג€™ support level for role permissions. Set the role stage to BETA while testing the role permissions.

***My choice is A.***

Reason: beacuse it contains SUPPORTED which we must see when creating custom roles and as it first version we must set it to ALPHA

----

**Q119.**

Your company has a large quantity of unstructured data in different file formats. You want to perform ETL transformations on the data. You need to make the data accessible on Google Cloud so it can be processed by a Dataflow job. What should you do?

- A. Upload the data to BigQuery using the bq command line tool.
- B. Upload the data to Cloud Storage using the gsutil command line tool.
- C. Upload the data into Cloud SQL using the import function in the console.
- D. Upload the data into Cloud Spanner using the import function in the console.

***My choice is B.***

Reason: Reference:https://cloud.google.com/solutions/performing-etl-from-relational-database-into-bigquery.

---

**Q120.(#CLI)**

You need to manage multiple Google Cloud projects in the fewest steps possible. You want to configure the Google Cloud SDK command line interface (CLI) so that you can easily manage multiple projects. What should you do?

- A. 1. Create a configuration for each project you need to manage. 2. Activate the appropriate configuration when you work with each of your assigned Google Cloud projects.
- B. 1. Create a configuration for each project you need to manage. 2. Use gcloud init to update the configuration values when you need to work with a non-default project
- C. 1. Use the default configuration for one project you need to manage. 2. Activate the appropriate configuration when you work with each of your assigned Google Cloud projects.
- D. 1. Use the default configuration for one project you need to manage. 2. Use gcloud init to update the configuration values when you need to work with a non-default project.

***My choice is A.***

Reason:  You need to create a separate config for each project and use that config to make further changes in CLI. Cloud SDK comes with a default configuration. To create multiple configurations, use gcloud config configurations create, and gcloud config configurations activate to switch between them. https://cloud.google.com/sdk/gcloud/reference/config/set. 

-------

**Q121.**

Your managed instance group raised an alert stating that new instance creation has failed to create new instances. You need to maintain the number of running instances specified by the template to be able to process expected application traffic. What should you do?

- A. Create an instance template that contains valid syntax which will be used by the instance group. Delete any persistent disks with the same name as instance names.
- B. Create an instance template that contains valid syntax that will be used by the instance group. Verify that the instance name and persistent disk name values are not the same in the template.
- C. Verify that the instance template being used by the instance group contains valid syntax. Delete any persistent disks with the same name as instance names. Set the disks.autoDelete property to true in the instance template.
- D. Delete the current instance template and replace it with a new instance template. Verify that the instance name and persistent disk name values are not the same in the template. Set the disks.autoDelete property to true in the instance template.

***My choice is D.***

Reason: We can not update an instance template when it is in use. see this:https://cloud.google.com/compute/docs/instance-templates#how_to_update_instance_templates. 

-----

**Q122.**

Your company is moving from an on-premises environment to Google Cloud. You have multiple development teams that use Cassandra environments as backend databases. They all need a development environment that is isolated from other Cassandra instances. You want to move to Google Cloud quickly and with minimal support effort. What should you do?

- A. 1. Build an instruction guide to install Cassandra on Google Cloud. 2. Make the instruction guide accessible to your developers.
- B. 1. Advise your developers to go to Cloud Marketplace. 2. Ask the developers to launch a Cassandra image for their development work.
- C. 1. Build a Cassandra Compute Engine instance and take a snapshot of it. 2. Use the snapshot to create instances for your developers.
- D. 1. Build a Cassandra Compute Engine instance and take a snapshot of it. 2. Upload the snapshot to Cloud Storage and make it accessible to your developers. 3. Build instructions to create a Compute Engine instance from the snapshot so that developers can do it themselves.

***My choice is B.***

Reason: It is easier to launch from marketplace.  https://medium.com/google-cloud/how-to-deploy-cassandra-and-connect-on-google-cloud-platform-with-a-few-clicks-11ee3d7001d1. 

----

**Q123.(#ComputeEngine)**

You have a Compute Engine instance hosting a production application. You want to receive an email if the instance consumes more than 90% of its CPU resources for more than 15 minutes. You want to use Google services. What should you do?

- A. 1. Create a consumer Gmail account. 2. Write a script that monitors the CPU usage. 3. When the CPU usage exceeds the threshold, have that script send an email using the Gmail account and smtp.gmail.com on port 25 as SMTP server.
- B. 1. Create a Stackdriver Workspace, and associate your Google Cloud Platform (GCP) project with it. 2. Create an Alerting Policy in Stackdriver that uses the threshold as a trigger condition. 3. Configure your email address in the notification channel.
- C. 1. Create a Stackdriver Workspace, and associate your GCP project with it. 2. Write a script that monitors the CPU usage and sends it as a custom metric to Stackdriver. 3. Create an uptime check for the instance in Stackdriver.
- D. 1. In Stackdriver Logging, create a logs-based metric to extract the CPU usage by using this regular expression: CPU Usage: ([0-9] {1,3})% 2. In Stackdriver Monitoring, create an Alerting Policy based on this metric. 3. Configure your email address in the notification channel.

***My choice is B.***

Reason: plus also GCP are all about automation and ease and are not likely to expect you to create scripts for such simple but highly requested tasks. https://cloud.google.com/monitoring/alerts/ui-conditions-ga. 

-----

**Q124.(#CloudSpanner)**

You have an application that uses Cloud Spanner as a backend database. The application has a very predictable traffic pattern. You want to automatically scale up or down the number of Spanner nodes depending on traffic. What should you do?

- A. Create a cron job that runs on a scheduled basis to review Cloud Monitoring metrics, and then resize the Spanner instance accordingly.
- B. Create a Cloud Monitoring alerting policy to send an alert to oncall SRE emails when Cloud Spanner CPU exceeds the threshold. SREs would scale resources up or down accordingly.
- C. Create a Cloud Monitoring alerting policy to send an alert to Google Cloud Support email when Cloud Spanner CPU exceeds your threshold. Google support would scale resources up or down accordingly.
- D. Create a Cloud Monitoring alerting policy to send an alert to webhook when Cloud Spanner CPU is over or under your threshold. Create a Cloud Function that listens to HTTP and resizes Spanner resources accordingly.

***My choice is D.***

Reason: https://cloud.google.com/architecture/autoscaling-cloud-spanner.

------

**Q125.(#ComputeEngine)**

Your company publishes large files on an Apache web server that runs on a Compute Engine instance. The Apache web server is not the only application running in the project. You want to receive an email when the egress network costs for the server exceed 100 dollars for the current month as measured by Google Cloud.
What should you do?

- A. Set up a budget alert on the project with an amount of 100 dollars, a threshold of 100%, and notification type of ג€email.ג€
- B. Set up a budget alert on the billing account with an amount of 100 dollars, a threshold of 100%, and notification type of ג€email.ג€
- C. Export the billing data to BigQuery. Create a Cloud Function that uses BigQuery to sum the egress network costs of the exported billing data for the Apache web server for the current month and sends an email if it is over 100 dollars. Schedule the Cloud Function using Cloud Scheduler to run hourly.
- D. Use the Cloud Logging Agent to export the Apache web server logs to Cloud Logging. Create a Cloud Function that uses BigQuery to parse the HTTP response log data in Cloud Logging for the current month and sends an email if the size of all HTTP responses, multiplied by current Google Cloud egress prices, totals over 100 dollars. Schedule the Cloud Function using Cloud Scheduler to run hourly.

***My choice is C.***

Reason: A: Not correct as there are other services that can generate egress B: A billing account is always linked on project level, so it contains other services C: A bit complex, but this is the right choice D: Again, not filtered for the Apach web server egress.

-----

**Q126.(#Plan)**

You have designed a solution on Google Cloud that uses multiple Google Cloud products. Your company has asked you to estimate the costs of the solution. You need to provide estimates for the monthly total cost. What should you do?

- A. For each Google Cloud product in the solution, review the pricing details on the products pricing page. Use the pricing calculator to total the monthly costs for each Google Cloud product.
- B. For each Google Cloud product in the solution, review the pricing details on the products pricing page. Create a Google Sheet that summarizes the expected monthly costs for each product.
- C. Provision the solution on Google Cloud. Leave the solution provisioned for 1 week. Navigate to the Billing Report page in the Cloud Console. Multiply the 1 week cost to determine the monthly costs.
- D. Provision the solution on Google Cloud. Leave the solution provisioned for 1 week. Use Cloud Monitoring to determine the provisioned and used resource amounts. Multiply the 1 week cost to determine the monthly costs.

***My choice is A.***

Reason: No reason.

-------

**Q127.(#LoadBalancing)**

You have an application that receives SSL-encrypted TCP traffic on port 443. Clients for this application are located all over the world. You want to minimize latency for the clients. Which load balancing option should you use?

- A. HTTPS Load Balancer
- B. Network Load Balancer
- C. SSL Proxy Load Balancer
- D. Internal TCP/UDP Load Balancer. Add a firewall rule allowing ingress traffic from 0.0.0.0/0 on the target instances.

***My choice is C.***

Reason: The type of traffic that you need your load balancer to handle is another factor in determining which load balancer to use: HTTP and HTTPS traffic: External HTTP(S) Load Balancing / Regional external HTTP(S) / load balancer Internal HTTP(S) Load Balancing TCP traffic: TCP Proxy Load Balancing / External TCP/UDP Network Load Balancing / Internal TCP/UDP Load Balancing / SSL traffic: SSL Proxy Load Balancing UDP traffic: External TCP/UDP Network Load Balancing / Internal TCP/UDP Load Balancing. See this:https://cloud.google.com/load-balancing/docs/ssl.

----

**Q128.(#Plan)**

You have an application on a general-purpose Compute Engine instance that is experiencing excessive disk read throttling on its Zonal SSD Persistent Disk. The application primarily reads large files from disk. The disk size is currently 350 GB. You want to provide the maximum amount of throughput while minimizing costs.
What should you do?

- A. Increase the size of the disk to 1 TB.
- B. Increase the allocated CPU to the instance.
- C. Migrate to use a Local SSD on the instance.
- D. Migrate to use a Regional SSD on the instance.

***My choice is C.***

Reason: see this: https://cloud.google.com/compute/docs/disks/performance.

-----

**Q129.(#VPC)**

Your Dataproc cluster runs in a single Virtual Private Cloud (VPC) network in a single subnet with range 172.16.20.128/25. There are no private IP addresses available in the VPC network. You want to add new VMs to communicate with your cluster using the minimum number of steps. What should you do?

- A. Modify the existing subnet range to 172.16.20.0/24.
- B. Create a new Secondary IP Range in the VPC and configure the VMs to use that range.
- C. Create a new VPC network for the VMs. Enable VPC Peering between the VMsג€™ VPC network and the Dataproc cluster VPC network.
- D. Create a new VPC network for the VMs with a subnet of 172.32.0.0/16. Enable VPC network Peering between the Dataproc VPC network and the VMs VPC network. Configure a custom Route exchange.

***My choice is A.***

Reason: it is easiest. 

----

**Q130.(#BigQuery)**

You manage an App Engine Service that aggregates and visualizes data from BigQuery. The application is deployed with the default App Engine Service account.
The data that needs to be visualized resides in a different project managed by another team. You do not have access to this project, but you want your application to be able to read data from the BigQuery dataset. What should you do?

- A. Ask the other team to grant your default App Engine Service account the role of BigQuery Job User.
- B. Ask the other team to grant your default App Engine Service account the role of BigQuery Data Viewer.
- C. In Cloud IAM of your project, ensure that the default App Engine service account has the role of BigQuery Data Viewer.
- D. In Cloud IAM of your project, grant a newly created service account from the other team the role of BigQuery Job User in your project.

***My choice is B.***

Reason:The Owner, Editor, and Viewer primitive roles include the BigQuery Admin (roles/bigquery.dataOwner), BigQuery Data Editor (roles/bigquery.dataEditor), and
BigQuery Data Viewer (roles/bigquery.dataViewer) roles, respectively. This means the Owner, Editor, and Viewer primitive roles have BigQuery access as defined for the respective BigQuery roles. Reference: https://cloud.google.com/bigquery/docs/access-control.

---

**Q131.(#VirtualMachine)**

You need to create a copy of a custom Compute Engine virtual machine (VM) to facilitate an expected increase in application traffic due to a business acquisition.
What should you do?

- A. Create a Compute Engine snapshot of your base VM. Create your images from that snapshot.
- B. Create a Compute Engine snapshot of your base VM. Create your instances from that snapshot.
- C. Create a custom Compute Engine image from a snapshot. Create your images from that image.
- D. Create a custom Compute Engine image from a snapshot. Create your instances from that image.

***My choice is D.***

Reason: A custom image belongs only to your project. To create an instance with a custom image, you must first have a custom image. Reference: https://cloud.google.com/compute/docs/instances/create-start-instance.

----

**Q132.(#Plan)**

You have deployed an application on a single Compute Engine instance. The application writes logs to disk. Users start reporting errors with the application. You want to diagnose the problem. What should you do?

- A. Navigate to Cloud Logging and view the application logs.
- B. Connect to the instanceג€™s serial console and read the application logs.
- C. Configure a Health Check on the instance and set a Low Healthy Threshold value.
- D. Install and configure the Cloud Logging Agent and view the logs from Cloud Logging.

***My choice is D.***

Reason: https://cloud.google.com/logging/docs/agent/installation.  "The VM images for Compute Engine and Amazon Elastic Compute Cloud (EC2) don't include the Logging agent, so you must complete these steps to install it on those instances, and If your VMs are running in Google Kubernetes Engine or App Engine, the agent is already included in the VM image, so you can skip this page."

---

**Q133.(#VM)**

An application generates daily reports in a Compute Engine virtual machine (VM). The VM is in the project corp-iot-insights. Your team operates only in the project corp-aggregate-reports and needs a copy of the daily exports in the bucket corp-aggregate-reports-storage. You want to configure access so that the daily reports from the VM are available in the bucket corp-aggregate-reports-storage and use as few steps as possible while following Google-recommended practices. What should you do?

- A. Move both projects under the same folder.
- B. Grant the VM Service Account the role Storage Object Creator on corp-aggregate-reports-storage.
- C. Create a Shared VPC network between both projects. Grant the VM Service Account the role Storage Object Creator on corp-iot-insights.
- D. Make corp-aggregate-reports-storage public and create a folder with a pseudo-randomized suffix name. Share the folder with the IoT team.

***My choice is B.***

Reason: Basically, you are giving the permissions to the VM Service Account to create a copy of the daily report on the bucket that the other team has access.

Predefined roles The following table describes Identity and Access Management (IAM) roles that are associated with Cloud Storage and lists the permissions that are contained in each role. Unless otherwise noted, these roles can be applied either to entire projects or specific buckets. 

Storage Object Creator (roles/storage.objectCreator) Allows users to create objects. Does not give permission to view, delete, or overwrite objects. 

See this: https://cloud.google.com/storage/docs/access-control/iam-roles#standard-roles.

---

**Q134.(#VM)**

You built an application on your development laptop that uses Google Cloud services. Your application uses Application Default Credentials for authentication and works fine on your development laptop. You want to migrate this application to a Compute Engine virtual machine (VM) and set up authentication using Google- recommended practices and minimal changes. What should you do?

- A. Assign appropriate access for Google services to the service account used by the Compute Engine VM.
- B. Create a service account with appropriate access for Google services, and configure the application to use this account.
- C. Store credentials for service accounts with appropriate access for Google services in a config file, and deploy this config file with your application.
- D. Store credentials for your user account with appropriate access for Google services in a config file, and deploy this config file with your application.

***My choice is A, but B also seems Correct.***

Reason: choosing A because you don't need to create another service account for this application; choosing B though the question does not state that is using the default service accounts and you could therefore assume one has previously been made.

-----

**Q135.(#ComputeEngine)**

You need to create a Compute Engine instance in a new project that doesn't exist yet. What should you do?

- A. Using the Cloud SDK, create a new project, enable the Compute Engine API in that project, and then create the instance specifying your new project.
- B. Enable the Compute Engine API in the Cloud Console, use the Cloud SDK to create the instance, and then use the --project flag to specify a new project.
- C. Using the Cloud SDK, create the new instance, and use the --project flag to specify the new project. Answer yes when prompted by Cloud SDK to enable the Compute Engine API.
- D. Enable the Compute Engine API in the Cloud Console. Go to the Compute Engine section of the Console to create a new instance, and look for the Create In A New Project option in the creation form.

***My choice is A.***

Reason: Creating a New Instance Using the Command Line Before you begin 1. In the Cloud Console, on the project selector page, select or create a Cloud project. 2. Make sure that billing is enabled for your Google Cloud project. Learn how to confirm billing is enabled for your project. 

To use the gcloud command-line tool for this quickstart, you must first install and initialize the Cloud SDK: 1. Download and install the Cloud SDK using the instructions given on Installing Google Cloud SDK. 2. Initialize the SDK using the instructions given on Initializing Cloud SDK. To use gcloud in Cloud Shell for this quickstart, first activate Cloud Shell using the instructions given on Starting Cloud Shell. 

See this site: https://cloud.google.com/ai-platform/deep-learning-vm/docs/quickstart-cli#before-you-begin. 

----------

**Q136.(#Plan)**

Your company runs one batch process in an on-premises server that takes around 30 hours to complete. The task runs monthly, can be performed offline, and must be restarted if interrupted. You want to migrate this workload to the cloud while minimizing cost. What should you do?

- A. Migrate the workload to a Compute Engine Preemptible VM.
- B. Migrate the workload to a Google Kubernetes Engine cluster with Preemptible nodes.
- C. Migrate the workload to a Compute Engine VM. Start and stop the instance as needed.
- D. Create an Instance Template with Preemptible VMs On. Create a Managed Instance Group from the template and adjust Target CPU Utilization. Migrate the workload.

***My choice is C.***

Reason: Preemptible VM cannot run more than 24 hours and its mentioned that it takes 30 hours to complete a job so the answer is C.

---

**Q137.**

You are developing a new application and are looking for a Jenkins installation to build and deploy your source code. You want to automate the installation as quickly and easily as possible. What should you do?

- A. Deploy Jenkins through the Google Cloud Marketplace.
- B. Create a new Compute Engine instance. Run the Jenkins executable.
- C. Create a new Kubernetes Engine cluster. Create a deployment for the Jenkins image.
- D. Create an instance template with the Jenkins executable. Create a managed instance group with this template.

***My choice is A.***

Reason: A is the easiest method.

---

**Q138.**

You have downloaded and installed the gcloud command line interface (CLI) and have authenticated with your Google Account. Most of your Compute Engine instances in your project run in the europe-west1-d zone. You want to avoid having to specify this zone with each CLI command when managing these instances.
What should you do?

- A. Set the europe-west1-d zone as the default zone using the gcloud config subcommand.
- B. In the Settings page for Compute Engine under Default location, set the zone to europeג€"west1-d.
- C. In the CLI installation directory, create a file called default.conf containing zone=europeג€"west1ג€"d.
- D. Create a Metadata entry on the Compute Engine page with key compute/zone and value europeג€"west1ג€"d.

***My choice is A.***

Reason: You can change the default zone and region in your metadata server by making a request to the metadata server. 

For example: gcloud compute project-info add-metadata \ --metadata google-compute-default-region=europe-west1,google-compute-default-zone=europe-west1-b 

The gcloud command-line tool only picks up on new default zone and region changes after you rerun the gcloud init command. After updating your default metadata, run gcloud init to reinitialize your default configuration. See this: https://cloud.google.com/compute/docs/gcloud-compute#change_your_default_zone_and_region_in_the_metadata_server.

----

**Q139.**

The core business of your company is to rent out construction equipment at large scale. All the equipment that is being rented out has been equipped with multiple sensors that send event information every few seconds. These signals can vary from engine status, distance traveled, fuel level, and more. Customers are billed based on the consumption monitored by these sensors. You expect high throughput `" up to thousands of events per hour per device `" and `" need to retrieve consistent data based on the time of the event `" and   `"Storing and retrieving individual signals should be atomic.`" What should you do?

- A. Create a file in Cloud Storage per device and append new data to that file.
- B. Create a file in Cloud Filestore per device and append new data to that file.
- C. Ingest the data into Datastore. Store data in an entity group based on the device.
- D. Ingest the data into Cloud Bigtable. Create a row key based on the event timestamp.

***My choice is D.***

Reason: You may find following keywords: High Throughput, consistent, Large Scale customer, export data and this is an IOT case = BigTable. 

 If Data is huge, unstructured and related time,  Bigtable is best option.

---

**Q140.**

You are asked to set up application performance monitoring on Google Cloud projects A, B, and C as a single pane of glass. You want to monitor CPU, memory, and disk. What should you do?

- A. Enable API and then share charts from project A, B, and C.
- B. Enable API and then give the metrics.reader role to projects A, B, and C.
- C. Enable API and then use default dashboards to view all projects in sequence.
- D. Enable API, create a workspace under project A, and then add projects B and C.

***My choice is D.***

Reason: Workspace is made for monitoring multiple projects. See this:https://cloud.google.com/monitoring/workspaces. 

-------

**Q141.(#CloudBilling)**

You created several resources in multiple Google Cloud projects. All projects are linked to different billing accounts. To better estimate future charges, you want to have a single visual representation of all costs incurred. You want to include new cost data as soon as possible. What should you do?

- A. Configure Billing Data Export to BigQuery and visualize the data in Data Studio.
- B. Visit the Cost Table page to get a CSV export and visualize it using Data Studio.
- C. Fill all resources in the Pricing Calculator to get an estimate of the monthly cost.
- D. Use the Reports view in the Cloud Billing Console to view the desired cost information.

***My choice is A.***

Reason: https://cloud.google.com/billing/docs/how-to/visualize-data. 

----

**Q142.(#VPC)**

Your company has workloads running on Compute Engine and on-premises. The Google Cloud Virtual Private Cloud (VPC) is connected to your WAN over a
Virtual Private Network (VPN). You need to deploy a new Compute Engine instance and ensure that no public Internet traffic can be routed to it. What should you do?

- A. Create the instance without a public IP address.
- B. Create the instance with Private Google Access enabled.
- C. Create a deny-all egress firewall rule on the VPC network.
- D. Create a route on the VPC to route all traffic to the instance over the VPN tunnel.

***My choice is A.***

Reason: When you are creating the instance you could configure external IP to none, to avoid external Internet access.

-----

**Q143.(#DeploymentManger)**

Your team maintains the infrastructure for your organization. The current infrastructure requires changes. You need to share your proposed changes with the rest of the team. You want to follow Google's recommended best practices. What should you do?

- A. Use Deployment Manager templates to describe the proposed changes and store them in a Cloud Storage bucket.
- B. Use Deployment Manager templates to describe the proposed changes and store them in Cloud Source Repositories.
- C. Apply the changes in a development environment, run gcloud compute instances list, and then save the output in a shared Storage bucket.
- D. Apply the changes in a development environment, run gcloud compute instances list, and then save the output in Cloud Source Repositories.

***My choice is B.***

Reason: https://cloud.google.com/source-repositories/docs/features. 

---

**Q144.(#Snapshot)**

You have a Compute Engine instance hosting an application used between 9 AM and 6 PM on weekdays. You want to back up this instance daily for disaster recovery purposes. You want to keep the backups for 30 days. You want the Google-recommended solution with the least management overhead and the least number of services. What should you do?

- A. 1. Update your instancesג€™ metadata to add the following value: snapshotג€"schedule: 0 1 * * * 2. Update your instancesג€™ metadata to add the following value: snapshotג€"retention: 30
- B. 1. In the Cloud Console, go to the Compute Engine Disks page and select your instanceג€™s disk. 2. In the Snapshot Schedule section, select Create Schedule and configure the following parameters: - Schedule frequency: Daily - Start time: 1:00 AM ג€" 2:00 AM - Autodelete snapshots after: 30 days
- C. 1. Create a Cloud Function that creates a snapshot of your instanceג€™s disk. 2. Create a Cloud Function that deletes snapshots that are older than 30 days. 3. Use Cloud Scheduler to trigger both Cloud Functions daily at 1:00 AM.
- D. 1. Create a bash script in the instance that copies the content of the disk to Cloud Storage. 2. Create a bash script in the instance that deletes data older than 30 days in the backup Cloud Storage bucket. 3. Configure the instanceג€™s crontab to execute these scripts daily at 1:00 AM.

***My choice is B.***

Reason: Use snapshot schedules as a best practice to back up your Compute Engine workloads. After creating a snapshot schedule, you can apply it to one or more persistent disks. See this:  https://cloud.google.com/compute/docs/disks/scheduled-snapshots. 

-----

**Q145.(#GKE)**

Your existing application running in Google Kubernetes Engine (GKE) consists of multiple pods running on four GKE n1`"standard`"2 nodes. You need to deploy additional pods requiring n2`"highmem`"16 nodes without any downtime. What should you do?

- A. Use gcloud container clusters upgrade. Deploy the new services.
- B. Create a new Node Pool and specify machine type n2ג€"highmemג€"16. Deploy the new pods.
- C. Create a new cluster with n2ג€"highmemג€"16 nodes. Redeploy the pods and delete the old cluster.
- D. Create a new cluster with both n1ג€"standardג€"2 and n2ג€"highmemג€"16 nodes. Redeploy the pods and delete the old cluster.

***My choice is B.***

Reason: When you need to change the machine profile of your Compute Engine cluster, you can create a new node pool and then migrate your workloads over to the new node pool.

----

**Q146.(#CloudSpanner #CloudTable)**

You have an application that uses Cloud Spanner as a database backend to keep current state information about users. Cloud Bigtable logs all events triggered by users. You export Cloud Spanner data to Cloud Storage during daily backups. One of your analysts asks you to join data from Cloud Spanner and Cloud
Bigtable for specific users. You want to complete this ad hoc request as efficiently as possible. What should you do?

- A. Create a dataflow job that copies data from Cloud Bigtable and Cloud Storage for specific users.
- B. Create a dataflow job that copies data from Cloud Bigtable and Cloud Spanner for specific users.
- C. Create a Cloud Dataproc cluster that runs a Spark job to extract data from Cloud Bigtable and Cloud Storage for specific users.
- D. Create two separate BigQuery external tables on Cloud Storage and Cloud Bigtable. Use the BigQuery console to join these tables through user fields, and apply appropriate filters.

**My choice is D.**

Reason: BigQuery supports: Cloud Bigtable, Cloud Storage, Google Drive, Cloud SQL. See this:https://cloud.google.com/bigquery/external-data-sources. 

----

**Q147.(#VM)**

You are hosting an application from Compute Engine virtual machines (VMs) in us`"central1`"a. You want to adjust your design to support the failure of a single
Compute Engine zone, eliminate downtime, and minimize cost. What should you do?

- A. ג€" Create Compute Engine resources in usג€"central1ג€"b. ג€" Balance the load across both usג€"central1ג€"a and usג€"central1ג€"b.
- B. ג€" Create a Managed Instance Group and specify usג€"central1ג€"a as the zone. ג€" Configure the Health Check with a short Health Interval.
- C. ג€" Create an HTTP(S) Load Balancer. ג€" Create one or more global forwarding rules to direct traffic to your VMs.
- D. ג€" Perform regular backups of your application. ג€" Create a Cloud Monitoring Alert and be notified if your application becomes unavailable. ג€" Restore from backups when notified.

***My choice is A.***

Reason: in order to remediate to the problem of single point of failure, we have to replicate VMs within multiple zones. Only A choice consider this concern.

------

**Q148.(#SecurityCheck)**

A colleague handed over a Google Cloud Platform project for you to maintain. As part of a security checkup, you want to review who has been granted the Project
Owner role. What should you do?

- A. In the console, validate which SSH keys have been stored as project-wide keys.
- B. Navigate to Identity-Aware Proxy and check the permissions for these resources.
- C. Enable Audit Logs on the IAM & admin page for all resources, and validate the results.
- D. Use the command gcloud projects getג€"iamג€"policy to view the current role assignments.

***My choice is D.***

Reason: gcloud projects get-iam-policy.

-----

**Q149.(#VPC #GKE)**

You are running multiple VPC-native Google Kubernetes Engine clusters in the same subnet. The IPs available for the nodes are exhausted, and you want to ensure that the clusters can grow in nodes when needed. What should you do?

- A. Create a new subnet in the same region as the subnet being used.
- B. Add an alias IP range to the subnet used by the GKE clusters.
- C. Create a new VPC, and set up VPC peering with the existing VPC.
- D. Expand the CIDR range of the relevant subnet for the cluster.

***My choice is D.***

Reason: https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/expand-ip-range.

----

**Q150.(#VM)**

You have a batch workload that runs every night and uses a large number of virtual machines (VMs). It is fault-tolerant and can tolerate some of the VMs being terminated. The current cost of VMs is too high. What should you do?

- A. Run a test using simulated maintenance events. If the test is successful, use preemptible N1 Standard VMs when running future jobs.
- B. Run a test using simulated maintenance events. If the test is successful, use N1 Standard VMs when running future jobs.
- C. Run a test using a managed instance group. If the test is successful, use N1 Standard VMs in the managed instance group when running future jobs.
- D. Run a test using N1 standard VMs instead of N2. If the test is successful, use N1 Standard VMs when running future jobs.

***My choice is A.***

Reason: https://cloud.google.com/compute/docs/instances/create-start-preemptible-instance. 

---

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



























































































