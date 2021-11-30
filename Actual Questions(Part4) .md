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

Q141......











































