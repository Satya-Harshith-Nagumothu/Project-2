<h1 align="center">Project 2 for AWS Assignemnt</h1>
<p align="center">
Satya Harshith Nagumothu [2221973] <br>
University Canada West<br>
BUSI 653, Section 04<br>
Instructor: Mahmood Mortazavi Dehkordi<br>
</p>

___

# Project Description: Descriptive Analysis of Building Permit Records
In this assignment I show how i designed a Data Analytic Platform (DAP) and implemented it for the City of Vancouver project, i will also explain the datasets used and the various derivations and DAP design using the datasets I selected. I got my datasets from website [City of Vancouver Open Data Portal](https://opendata.vancouver.ca/explore/dataset/issued-building-permits/information/) related to the Vancouver City operations.

## Project Title: Understanding Building Permits Issued Percentages
The primary goal here is to conduct a descriptive analysis of the yearly trends in Building permits issued based on the datasets taken from [City of Vancouver Open Data Portal](https://opendata.vancouver.ca/explore/dataset/issued-building-permits/information/). I am planning to find the percentages of permits issued for each category or type over time, which can help inform operational strategies for see the probability of getting a permit.
## Project Objective:
* Design a dAP for Building Permits Issed using Building Permits Dataset.
* I decided this will be my dataset to get information related to percentages of permits issued for each category or type over time in city of Vancouver.
* The 11 steps of information is shown below: <br>
## Datasets
* There are two datasets which I used are .
* The first dataset is **"cummulative_issued-building-permits-2024"**, it contains information on all building permits issued:
  * [cummulative_issued-building-permits 2024.xlsx](https://github.com/user-attachments/files/17004724/cummulative_issued-building-permits.2024.xlsx) contains the information of all building permits issued.
* The second datset is **"Approved-issued-building-permits-2024"**, it Contains details on approved building permits issued:
  * [Approved-issued-building-permits-2024.xlsx](https://github.com/user-attachments/files/17004726/Approved-issued-building-permits-2024.xlsx) contains the information of approved building permits issued.
* Using both these datasets I will be planning my DAP for City of Vancouver.
## Methodology:
* I will explain the process of designing the DAP below for Buildign Permits of City of vancouver:
### Step 15: Data Protection
* This **Data Protection** involves safeguarding sensitive information from unauthorized access, misuse, or breaches.
* It is critical when handling datasets that may include personal information about building permits.
* For this we are creating KMS keys for encryption and decryption of data inthe S3 buckets.<br>
![fig02](https://github.com/user-attachments/assets/bad02961-a238-41d6-aa99-7b2df2e26cb9)
* The above image shows my newly created KMS key information.
* I am also enabling the Bucket Versioning and encrypting using the KMS key i created for both my S3 bucket and S3 backup bucket I created.<br>
![fig03](https://github.com/user-attachments/assets/26459c4e-0e83-4ff3-97e9-9b1808fd8691)
* The above images shows my S3 bucket properties information.<br>
![fig04](https://github.com/user-attachments/assets/a889da3d-ecab-417b-9605-7712c9c33342)
* The above images shows my S3 backup bucket properties information.<br>
* I am also configuring the backup option by doing a mirroring replication of my S3 bucket with another bucket.<br>
![fig05](https://github.com/user-attachments/assets/bc55a626-d8ad-4f8f-b06d-e59d70ee23db)
* The above image shows my replication information.
### Step 16: Data Governance
* Data governance refers to the policies, standards, and practices for managing and using data in a way that aligns with organizational goals and regulatory requirements.
* It ensures the quality, integrity, and security of data across its lifecycle.
* For this first I am creating Trusted folder where i can store data which has been masked to protect sensitive data information.<br>
![fig18](https://github.com/user-attachments/assets/33ccbc7e-e0d3-4ca3-bf9c-4f0754d0c457)
* The above image shows the Trusted folder created.
* I them create an ETL to convert the raw data available using ETL to identify and mask the sensitive information.<br>
![fig19](https://github.com/user-attachments/assets/8596cdd1-50a7-4623-9ddc-875fc42df64b)
* The above image shows the ETL pipeline for saving the trusted information from raw data.
* I then move on to storing the information retrieved from ETL into the trusted folder.<br>
![fig20](https://github.com/user-attachments/assets/ec37650f-6d91-4f80-a556-95fad9aaedea)
* The above image shows the resultant information stored as csv file in trusted folder.
### Step 17: Data Monitoring
* Data monitoring involves continuously tracking data usage and access to ensure compliance with governance policies, detect potential breaches, and maintain data integrity.
* Here we will be using "**AWS CloudWatch**" service to create a dashboard based on our needs.<br>
![fig30](https://github.com/user-attachments/assets/ae5a50ff-ff0c-4703-b0d3-3ad7ea130a81)
* The above image displays the dashboard of AWS CloudWatch
* I then move on to create a user activity trail using the "**AWS CloudTrail**" service, so that i can track user activities for any anomalies.<br>
![fig31](https://github.com/user-attachments/assets/ff49c1e4-5f5a-4a6c-a54f-a53529a43126)
* The above image shows the cloud trail created for tracking user activity.<br>
![fig32](https://github.com/user-attachments/assets/d0866e77-e861-4cc4-b886-cc5b207b2059)
* The above image displays the information of cloud trail saved in S3.
## Tools and Technologies:
* The lsit of Tools or technologies used are:
  * AWS-S3
  * AWS-Glue
  * AWS-IAM
  * AWS-KMS
  * AWS-CloudWatch
  * AWS-CloudTrail
