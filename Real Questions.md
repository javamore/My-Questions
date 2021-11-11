**Q1. (Plan related)**

Every employee of your company has a Google account. Your operational team needs to manage a large number of instances on Compute Engine. Each member of this team needs only administrative access to the servers. Your security team wants to ensure that the deployment of credentials is operationally efficient and must be able to determine who accessed a given instance. What should you do?

- A. Generate a new SSH key pair. Give the private key to each member of your team. Configure the public key in the metadata of each instance.
- B. Ask each member of the team to generate a new SSH key pair and to send you their public key. Use a configuration management tool to deploy those keys on each instance.
- C. Ask each member of the team to generate a new SSH key pair and to add the public key to their Google account. Grant the ג€compute.osAdminLoginג€ role to the Google group corresponding to this team.
- D. Generate a new SSH key pair. Give the private key to each member of your team. Configure the public key as a project-wide public SSH key in your Cloud Platform project and allow project-wide public SSH keys on each instance.

***My choice is C***

Reason: Some would choose D, but D is hard to "determine who accessed a given instance", and sending private keys to users is not safe, more details see this website: https://cloud.google.com/compute/docs/instances/managing-instance-access.



Q2.(IP related)

You need to create a custom VPC with a single subnet. The subnet's range must be as large as possible. Which range should you use?

- A. 0.0.0.0/0
- B. 10.0.0.0/8
- C. 172.16.0.0/12
- D. 192.168.0.0/16

My choice is B.

Reason: The private network range is defined by IETF (Ref: https://tools.ietf.org/html/rfc1918) and adhered to by all cloud providers. The supported internal IP Address ranges are 

1. 24-bit block 10.0.0.0/8 (16777216 IP Addresses)
2. 20-bit block 172.16.0.0/12 (1048576 IP Addresses)
3. 16-bit block 192.168.0.0/16 (65536 IP Addresses)
   10.0.0.0/8 gives you the most extensive range - 16777216 IP Addresses.



Q3. (SQL related)

You want to select and configure a cost-effective solution for relational data on Google Cloud Platform. You are working with a small set of operational data in one geographic location. You need to support point-in-time recovery. What should you do?

- A. Select Cloud SQL (MySQL). Verify that the enable binary logging option is selected.
- B. Select Cloud SQL (MySQL). Select the create failover replicas option.
- C. Select Cloud Spanner. Set up your instance with 2 nodes.
- D. Select Cloud Spanner. Set up your instance as multi-regional.

My choice is A.

Reason: You must enable binary logging to use point-in-time recovery. Enabling binary logging causes a slight reduction in write performance. See details here: https://cloud.google.com/sql/docs/mysql/backup-recovery/backups



Q4.(Plan related)

You want to configure autohealing for network load balancing for a group of Compute Engine instances that run in multiple zones, using the fewest possible steps.
You need to configure re-creation of VMs if they are unresponsive after 3 attempts of 10 seconds each. What should you do?

- A. Create an HTTP load balancer with a backend configuration that references an existing instance group. Set the health check to healthy (HTTP)
- B. Create an HTTP load balancer with a backend configuration that references an existing instance group. Define a balancing mode and set the maximum RPS to 10.
- C. Create a managed instance group. Set the Autohealing health check to healthy (HTTP)
- D. Create a managed instance group. Verify that the autoscaling setting is on.

My choice is C.

Reason: Using a health-check with a lb (option A) would only probe if the backend instances are receiving traffic, but won't recreate unhealthy instances which is a specific ask in the question. Reference here: https://cloud.google.com/compute/docs/tutorials/high-availability-autohealing. 



Q5.(Plan related)

You are using multiple configurations for gcloud. You want to review the configured Kubernetes Engine cluster of an inactive configuration using the fewest possible steps. What should you do?

- A. Use gcloud config configurations describe to review the output.
- B. Use gcloud config configurations activate and gcloud config list to review the output.
- C. Use kubectl config get-contexts to review the output.
- D. Use kubectl config use-context and kubectl config view to review the output.

My choice is D.

Reason: https://medium.com/google-cloud/kubernetes-engine-kubectl-config-b6270d2b656c. 



Q6.(Plan related)

Your company uses Cloud Storage to store application backup files for disaster recovery purposes. You want to follow Google's recommended practices. Which storage option should you use?

- A. Multi-Regional Storage
- B. Regional Storage
- C. Nearline Storage
- D. Coldline Storage

My choice is D.

Reason: Unless a withdraw frequency is mentioned, the recommended practice by google is to use "Archive Storage". However as this is not an available option, then "Coldline Storage" is the next best solution. Reference: https://cloud.google.com/storage/docs/storage-classes#nearline.



Q7. (Billing related)

Several employees at your company have been creating projects with Cloud Platform and paying for it with their personal credit cards, which the company reimburses. The company wants to centralize all these projects under a single, new billing account. What should you do?

- A. Contact cloud-billing@google.com with your bank account details and request a corporate billing account for your company.
- B. Create a ticket with Google Support and wait for their call to share your credit card details over the phone.
- C. In the Google Platform Console, go to the Resource Manage and move all projects to the root Organizarion.
- D. In the Google Cloud Platform Console, create a new billing account and set up a payment method.

My choice is D(though incomplete).

Reason:  C is incomplete. Moving projects under an organisation doesn't change their linked billing project. https://cloud.google.com/resource-manager/docs/migrating-projects-billing. Note: The link between projects and billing accounts is preserved, irrespective of the hierarchy. When you move your existing projects into the organization they will continue to work and be billed as they used to before the migration, even if the corresponding billing account has not been migrated yet.  D is incomplete as well, after setting the billing account in the organisation you need to link the projects to the new billing account.



Q8.(IP related)

You have an application that looks for its licensing server on the IP 10.0.3.21. You need to deploy the licensing server on Compute Engine. You do not want to change the configuration of the application and want the application to be able to reach the licensing server. What should you do?

- A. Reserve the IP 10.0.3.21 as a static internal IP address using gcloud and assign it to the licensing server.
- B. Reserve the IP 10.0.3.21 as a static public IP address using gcloud and assign it to the licensing server.
- C. Use the IP 10.0.3.21 as a custom ephemeral IP address and assign it to the licensing server.
- D. Start the licensing server with an automatic ephemeral IP address, and then promote it to a static internal IP address.

My choice is A.

Reason: IP 10.0.3.21 is internal by default, and to ensure that it will be static non-changing it should be selected as static internal ip address.



Q9.(Plan related)

You are deploying an application to App Engine. You want the number of instances to scale based on request rate. You need at least 3 unoccupied instances at all times. Which scaling type should you use?

- A. Manual Scaling with 3 instances.
- B. Basic Scaling with min_instances set to 3.
- C. Basic Scaling with max_instances set to 3.
- D. Automatic Scaling with min_idle_instances set to 3.

My choice is D.

Reason: Automatic scaling creates instances based on request rate, response latencies, and other application metrics. You can specify thresholds for each of these metrics, as well as a minimum number instances to keep running at all times. See this "App Engine calculates the number of instances necessary to serve your current application traffic based on scaling settings such as target_cpu_utilization and target_throughput_utilization. Setting min_idle_instances specifies the number of instances to run in addition to this calculated number. For example, if App Engine calculates that 5 instances are necessary to serve traffic, and min_idle_instances is set to 2, App Engine will run 7 instances (5, calculated based on traffic, plus 2 additional per min_idle_instances)." from: https://cloud.google.com/appengine/docs/standard/python/how-instances-are-managed.



Q10.(Plan related)

You have a development project with appropriate IAM roles defined. You are creating a production project and want to have the same IAM roles on the new project, using the fewest possible steps. What should you do?

- A. Use gcloud iam roles copy and specify the production project as the destination project.
- B. Use gcloud iam roles copy and specify your organization as the destination organization.
- C. In the Google Cloud Platform Console, use the ג€˜create role from roleג€™ functionality.
- D. In the Google Cloud Platform Console, use the ג€˜create roleג€™ functionality and select all applicable permissions.

My choice is A.

Reason: Copy roles to a "project", not "organization" as per question. The link provided, additionally has instructions on deploying roles into projects : https://cloud.google.com/sdk/gcloud/reference/iam/roles/copy gcloud iam roles copy --source="roles/spanner.databaseAdmin" --destination=CustomSpannerDbAdmin --dest-project=PROJECT_ID.



Q11.(Plan related)

You need a dynamic way of provisioning VMs on Compute Engine. The exact specifications will be in a dedicated configuration file. You want to follow Google's recommended practices. Which method should you use?

- A. Deployment Manager
- B. Cloud Composer
- C. Managed Instance Group
- D. Unmanaged Instance Group

My choice is A.

Reason: Deployment manager can create, update and delete resources inside GCP by simply using a config file.



Q12.(Plan related)

You have a Dockerfile that you need to deploy on Kubernetes Engine. What should you do?

- A. Use kubectl app deploy <dockerfilename>.
- B. Use gcloud app deploy <dockerfilename>.
- C. Create a docker image from the Dockerfile and upload it to Container Registry. Create a Deployment YAML file to point to that image. Use kubectl to create the deployment with that file.
- D. Create a docker image from the Dockerfile and upload it to Cloud Storage. Create a Deployment YAML file to point to that image. Use kubectl to create the deployment with that file.

My choice is C.

Reason: kubectl can't deploy "DockerFile", so A and B are App Engine which doesn't satisfy the use of GKE. You use Container Registry in the e2e process of deploying Docker on GKE.



Q13...........









