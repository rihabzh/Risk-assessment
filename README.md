## ASSET-ORIENTED RISK ASSESSMENT OF STORAGE ASSETS IN AWS AND AZURE
# Objective
To identify storage assets in AWS S3 and Microsoft Azure Blob Storage, identify possible vulnerabilities and threats, and assess their likelihood, impact, and risk level.

# 1. Software / Cloud Services Required
•	AWS Account 
•	Microsoft Azure Account 
•	Web Browser 
•	Internet Connection
# Cloud Services Used
Cloud Platform	Storage Service
AWS	Amazon S3
Microsoft Azure	Azure Blob Storage
# PART A — AWS S3 STORAGE ASSESSMENT
# Step 1: Login to AWS
1.	Open the AWS Management Console. 
2.	Sign in using your AWS account. 
3.	Search for S3. 
4.	Select Amazon S3. 

# Step 2: Select the S3 Bucket
1.	Click Buckets. 
2.	Select the S3 bucket created in the previous experiment. 
3.	Record: 
o	Bucket name 
o	AWS Region 
o	Number/type of objects 
<img width="1906" height="840" alt="Screenshot 2026-09-08 225212" src="https://github.com/user-attachments/assets/e3ce4269-3d1c-42f9-9381-d965e7409035" />



# Step 3: Check Block Public Access
1.	Open the S3 bucket. 
2.	Select Permissions. 
3.	Locate Block public access (bucket settings). 
4.	Check Block all public access. 
Record:
•	ON → Secure configuration 
•	OFF → Potential public-access risk 
<img width="1905" height="805" alt="Screenshot 2026-09-08 225308" src="https://github.com/user-attachments/assets/f17150c7-5a45-464e-8444-a19867c4c9be" />


# Step 4: Check Bucket Versioning
1.	Select the Properties tab. 
2.	Locate Bucket Versioning. 
3.	Record whether it is: 
o	Enabled 
o	Disabled 
Security purpose
Versioning helps recover previous versions of objects after accidental deletion or modification.
<img width="1907" height="853" alt="Screenshot 2026-09-08 225358" src="https://github.com/user-attachments/assets/b9f90176-c685-451b-abee-31b77b2ee978" />


Step 5: Check Default Encryption
1.	Stay in the Properties tab. 
2.	Locate Default encryption. 
3.	Record the encryption type. 
Possible configurations include:
•	SSE-S3 
•	SSE-KMS 
•	DSSE-KMS 
Security purpose
Encryption protects stored data from unauthorized disclosure.
Screenshot: Default Encryption.
<img width="937" height="777" alt="Screenshot 2026-09-08 225439" src="https://github.com/user-attachments/assets/8ad615ca-1d5e-480b-8d48-1b0217dd7ee2" />

Step 6: Check Bucket Policy
1.	Select Permissions. 
2.	Locate Bucket policy. 
3.	Check whether a bucket policy exists. 
Record:
•	Policy exists 
•	No policy 
Note
A missing bucket policy is not automatically a vulnerability. Access may be controlled through IAM and other AWS security mechanisms.
Screenshot: Bucket Policy section.
<img width="911" height="743" alt="Screenshot 2026-09-08 225515" src="https://github.com/user-attachments/assets/7ff3df65-3f00-48f6-b414-7bd6981ed893" />

Step 7: Check Object Ownership and ACL
1.	In Permissions, locate Object Ownership. 
2.	Record the current configuration. 
A common secure configuration is:
Bucket owner enforced
This means:
•	ACLs are disabled. 
•	Objects are owned by the bucket owner. 
•	Access is controlled using policies. 
Screenshot: Object Ownership.
<img width="916" height="753" alt="Screenshot 2026-09-08 225536" src="https://github.com/user-attachments/assets/16137c23-7096-4521-8f2d-5781c58a4a91" />

Step 8: Check Server Access Logging
1.	Go to Properties. 
2.	Locate Server access logging. 
3.	Record whether it is: 
o	Enabled 
o	Disabled 
Security purpose
Logging helps investigate suspicious or unauthorized access to the bucket.
Screenshot: Server Access Logging.
<img width="925" height="763" alt="Screenshot 2026-09-08 225610" src="https://github.com/user-attachments/assets/b4e60a4d-f41e-4715-b865-8e7cb9c52391" />

# PART B — AWS RISK ASSESSMENT
After checking the S3 configuration, identify possible vulnerabilities and threats.
Risk Formula
Risk Score = Likelihood × Impact

| Asset | Vulnerability | Threat | Likelihood | Impact | Risk Score | Risk Level | Recommended Mitigation |
| :--- | :--- | :--- | :---: | :---: | :---: | :--- | :--- |
| S3 Bucket | Versioning disabled | Accidental/malicious data deletion | 3 | 4 | 12 | High | Enable versioning |
| S3 Bucket | Access logging disabled | Difficult investigation of unauthorized activity | 3 | 3 | 9 | Medium | Enable appropriate logging |
| S3 Bucket | Public access enabled* | Unauthorized data access | 4 | 5 | 20 | Critical | Enable Block Public Access |
| S3 Bucket | Weak access permissions* | Unauthorized modification/access | 3 | 4 | 12 | High | Apply least privilege |

# PART C — MICROSOFT AZURE BLOB STORAGE
# Step 9: Login to Azure
1.	Open the Azure Portal. 
2.	Sign in using your Microsoft Azure account. 
3.	Search for Storage accounts. 
4.	Select Storage accounts. 

# Step 10: Create a Storage Account
If you don't already have a Storage Account:
1.	Click Create. 
2.	Select your available Subscription. 
3.	Select or create a Resource Group. 
4.	Enter a unique Storage account name. 
5.	Select an appropriate Region. 
6.	Keep the recommended/default performance and redundancy settings unless instructed otherwise. 
7.	Review the configuration. 
8.	Click Create. 
9.	Wait until deployment is completed. 
10.	Click Go to resource. 
Screenshot: Successfully created Storage Account.
Important
Use only the resources required for this experiment and delete them later if they are no longer required, especially if the subscription can incur charges.

# Step 11: Check Azure Storage Configuration
Open the newly created Storage Account.
Go to:
Settings → Configuration
Locate:
Allow Blob anonymous access
Record whether it is:
•	Enabled 
•	Disabled 
Security purpose
Anonymous access can allow users to access blob data without authentication.
For a normal secure configuration, anonymous access should generally be disabled unless specifically required.
Screenshot: Allow Blob anonymous access.

# Step 12: Check Encryption
Inside the Storage Account, locate the Encryption settings.
Record:
•	Encryption status 
•	Key management configuration 
Azure Storage provides encryption at rest for stored data.
Screenshot: Encryption settings.

# Step 13: Check Data Protection
Open:
Data protection
Check available options such as:
•	Blob soft delete 
•	Container soft delete 
•	Blob versioning 
•	Point-in-time recovery, where available 
Record whether the relevant protection mechanisms are enabled or disabled.
Security purpose
Data protection features help recover data after accidental deletion or modification.
Screenshot: Data Protection settings.

# Step 14: Check Access Control
Go to:
Access control (IAM)
Review the assigned roles.
Look for excessive permissions such as unnecessary:
•	Owner 
•	Contributor 
•	Storage-related administrative permissions 
Security principle
Use Least Privilege:
Users should receive only the permissions required to perform their tasks.
Screenshot: Access Control (IAM).

# Step 15: Check Networking
Go to:
Networking
Check how the storage account can be accessed.
Record whether access is allowed through:
•	Public networks 
•	Selected networks 
•	Private endpoints, if configured 
Security consideration
Unrestricted network access can increase the attack surface.
Screenshot: Networking configuration.

# PART D — AZURE RISK ASSESSMENT

| Asset | Vulnerability | Threat | Likelihood | Impact | Risk Score | Risk Level | Recommended Mitigation |
| :--- | :--- | :--- | :---: | :---: | :---: | :--- | :--- |
| Azure Blob Storage | Anonymous access enabled* | Unauthorized data access | 4 | 5 | 20 | Critical | Disable anonymous access |
| Azure Storage | Data protection disabled* | Permanent data loss | 3 | 4 | 12 | High | Enable appropriate protection |
| Azure Storage | Excessive permissions* | Unauthorized modification | 3 | 4 | 12 | High | Apply least privilege |
| Azure Storage | Unrestricted network access* | External attack/access | 3 | 4 | 12 | High | Restrict network access |


# PART E — COMPARISON OF AWS AND AZURE

| Security Control | AWS S3 | Azure Blob Storage |
| :--- | :--- | :--- |
| Public access control | Block Public Access | Anonymous access control |
| Encryption | SSE-S3 / SSE-KMS | Azure Storage encryption |
| Versioning | S3 Versioning | Blob Versioning |
| Data recovery | Versioning / other controls | Soft Delete / Versioning |
| Access control | IAM / Bucket policies | RBAC / Access policies |
| Logging/Monitoring | S3 logging / Cloud monitoring | Azure monitoring/logging |
| Network security | Bucket/network controls | Storage networking / private endpoints |


# PART F — FINAL RISK SUMMARY

| Cloud | Asset | Major Risk | Risk Level | Mitigation |
| :--- | :--- | :--- | :---: | :--- |
| AWS | S3 Bucket | Versioning disabled | High | Enable versioning |
| AWS | S3 Bucket | Logging disabled | Medium | Enable appropriate logging |
| Azure | Blob Storage | Anonymous access* | Critical | Disable anonymous access |
| Azure | Blob Storage | Data protection* | High | Enable protection mechanisms |

# RESULT
The storage assets in AWS S3 and Microsoft Azure Blob Storage were identified and analyzed. Various security configurations, vulnerabilities, threats, likelihood, and impacts were evaluated. Risk scores were calculated using the Likelihood × Impact method, and appropriate security mitigation measures were recommended.
