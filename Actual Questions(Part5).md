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





