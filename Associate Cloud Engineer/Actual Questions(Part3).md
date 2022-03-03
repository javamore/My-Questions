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

***My choice is B.***

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

***My choice is A***

Reason: coldline provides access once a QUARTER.

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

















