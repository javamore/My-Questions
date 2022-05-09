**Q1. **

Your company has decided to make a major revision of their API in order to create better experiences for their developers. They need to keep the old version of the API available and deployable, while allowing new customers and testers to try out the new API. They want to keep the same SSL and DNS records in place to serve both APIs.
What should they do?

- A. Configure a new load balancer for the new version of the API
- B. Reconfigure old clients to use a new endpoint for the new API
- C. Have the old API forward traffic to the new API based on the path
- D. Use separate backend pools for each API path behind the load balancer

***My choice is D.***

Reason: HTTP(S) load balancer can direct traffic reaching a single IP to different backends based on the incoming URL.

------

**Q2.**

Your company plans to migrate a multi-petabyte data set to the cloud. The data set must be available 24hrs a day. Your business analysts have experience only with using a SQL interface.
How should you store the data to optimize it for ease of analysis?

- A. Load data into Google BigQuery
- B. Insert data into Google Cloud SQL
- C. Put flat files into Google Cloud Storage
- D. Stream data into Google Cloud Datastore

***My choice is A.***

Reason: B isn't correct because Cloud SQL does not scale to that volume. Cloud SQL storage is limited to a maximum of 30,720GB. (0.03072PetaBytes)

-----

**Q3. **

The operations manager asks you for a list of recommended practices that she should consider when migrating a J2EE application to the cloud.
Which three practices should you recommend? (Choose three.)

- A. Port the application code to run on Google App Engine
- B. Integrate Cloud Dataflow into the application to capture real-time metrics
- C. Instrument the application with a monitoring tool like Stackdriver Debugger
- D. Select an automation framework to reliably provision the cloud infrastructure
- E. Deploy a continuous integration tool with automated testing in a staging environment
- F. Migrate from MySQL to a managed NoSQL database like Google Cloud Datastore or Bigtable

***My choice is C,D,E.*** 

Reason: https://cloud.google.com/appengine/docs/standard/java/tools/uploadinganapp;  https://cloud.google.com/appengine/docs/standard/java/building-app/cloud-sql

-----

**Q4.**

A news feed web service has the following code running on Google App Engine. During peak load, users report that they can see news articles they already viewed.
What is the most likely cause of this problem?

pic-q04.jpg

- A. The session variable is local to just a single instance
- B. The session variable is being overwritten in Cloud Datastore
- C. The URL of the API needs to be modified to prevent caching
- D. The HTTP Expires header needs to be set to -1 stop caching

***My choice is A.***

Reason:  There is nothing related to datastore here for answer B.

-----

**Q5.**

An application development team believes their current logging tool will not meet their needs for their new cloud-based product. They want a better tool to capture errors and help them analyze their historical log data. You want to help them find a solution that meets their needs.
What should you do?

- A. Direct them to download and install the Google StackDriver logging agent
- B. Send them a list of online resources about logging best practices
- C. Help them define their requirements and assess viable logging tools
- D. Help them upgrade their current tool to take advantage of any new features

***My choice is C.***

Reason:  It is not clearly mentioned if the cloud based solution is Google Cloud or some other cloud.

-----

**Q6.**

You need to reduce the number of unplanned rollbacks of erroneous production deployments in your company's web hosting platform. Improvement to the QA/
Test processes accomplished an 80% reduction.
Which additional two approaches can you take to further reduce the rollbacks? (Choose two.)

- A. Introduce a green-blue deployment model
- B. Replace the QA environment with canary releases
- C. Fragment the monolithic platform into microservices
- D. Reduce the platform's dependency on relational database systems
- E. Replace the platform's relational database systems with a NoSQL database

***My choice is A,C.***

Reason: D) and E) are pointless in this context. C) is certainly a good practice. Now between A) and B) .

A) Blue green deployment is an application release model that gradually transfers user traffic from a previous version of an app or microservice to a nearly identical new release—both of which are running in production. 

C) In software, a canary process is usually the first instance that receives live production traffic about a new configuration update, either a binary or configuration rollout. The new release only goes to the canary at first. The fact that the canary handles real user traffic is key: if it breaks, real users get affected, so canarying should be the first step in your deployment process, as opposed to the last step in testing in production. " While both green-blue and canary releases are useful, B) suggests "replacing QA" with canary releases - which is not good. QA got the issue down by 80%. Hence A) and C).

----

**Q7. **

To reduce costs, the Director of Engineering has required all developers to move their development infrastructure resources from on-premises virtual machines
(VMs) to Google Cloud Platform. These resources go through multiple start/stop events during the day and require state to persist. You have been asked to design the process of running a development environment in Google Cloud while providing cost visibility to the finance department.
Which two steps should you take? (Choose two.)

- A. Use the - -no-auto-delete flag on all persistent disks and stop the VM
- B. Use the - -auto-delete flag on all persistent disks and terminate the VM
- C. Apply VM CPU utilization label and include it in the BigQuery billing export
- D. Use Google BigQuery billing export and labels to associate cost to groups
- E. Store all state into local SSD, snapshot the persistent disks, and terminate the VM
- F. Store all state in Google Cloud Storage, snapshot the persistent disks, and terminate the VM

***My choice is A,D.***

Reason:  https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-disk-auto-delete#--auto-delete ; https://cloud.google.com/billing/docs/how-to/export-data-bigquery



**Q8.**

Your company wants to track whether someone is present in a meeting room reserved for a scheduled meeting. There are 1000 meeting rooms across 5 offices on 3 continents. Each room is equipped with a motion sensor that reports its status every second. The data from the motion detector includes only a sensor ID and several different discrete items of information. Analysts will use this data, together with information about account owners and office locations.
Which database type should you use?

- A. Flat file
- B. NoSQL
- C. Relational
- D. Blobstore

***My choice is B.***

Reason: Relational databases were not designed to cope with the scale and agility challenges that face modern applications, nor were they built to take advantage of the commodity storage and processing power available today.
NoSQL fits well for:
✑ Developers are working with applications that create massive volumes of new, rapidly changing data types ג€" structured, semi-structured, unstructured and polymorphic data.
Incorrect Answers:
D: The Blobstore API allows your application to serve data objects, called blobs, that are much larger than the size allowed for objects in the Datastore service.
Blobs are useful for serving large files, such as video or image files, and for allowing users to upload large data files.





























