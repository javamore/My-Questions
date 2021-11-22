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

![Q94](balabalaaaa)

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

My choice is C.

Reason: see this:  https://cloud.google.com/kubernetes-engine/sandbox.

------------------

**Q98(#CloudSpanner)**

Your customer has implemented a solution that uses Cloud Spanner and notices some read latency-related performance issues on one table. This table is accessed only by their users using a primary key. The table schema is shown below.

![Q98](balabla....)

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













































