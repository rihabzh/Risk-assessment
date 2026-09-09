## EXPERIMENT 5
# AUDITING CLOUD ACTIVITY USING AWS CLOUDTRAIL
# Objective

To audit and monitor cloud activity in AWS using AWS CloudTrail by viewing and analyzing recorded AWS events and identifying important audit information such as user identity, event name, event time, AWS service, region, and operation status.

# 1. Requirements
•	AWS Account 
•	Web Browser 
•	Internet Connection 
•	Amazon S3 access 
•	AWS CloudTrail 

# PART A — ACCESS AWS CLOUDTRAIL
# Step 1: Login to AWS
1.	Open the AWS Management Console. 
2.	Sign in using your AWS account. 
3.	In the AWS search bar, type CloudTrail. 
4.	Select AWS CloudTrail. 
Screenshot 1: AWS CloudTrail dashboard.
<img width="1895" height="759" alt="Screenshot 2026-09-09 002206" src="https://github.com/user-attachments/assets/bf6daea3-d77a-41c2-ba28-c77960d4b51c" />

# Step 2: Open Event History
1.	In the CloudTrail navigation menu, select Event history. 
2.	CloudTrail displays recent AWS activity. 
3.	Review the available events. 
The Event History page may display information such as:
•	Event time 
•	Username 
•	Event name 
•	Event source 
•	Resource type 
•	Resource name 
Screenshot 2: CloudTrail Event History.
<img width="1907" height="867" alt="Screenshot 2026-09-09 002240" src="https://github.com/user-attachments/assets/a1418dea-edb1-4e94-8e9e-2fcd1d19f4d5" />

# PART B — ANALYZE A CLOUDTRAIL EVENT
# Step 3: Select an Event
1.	From the Event History list, select an S3-related event. 
2.	Click the event to open its details. 
3.	Examine the event information and the event record/JSON. 
For this experiment, a CreateBucket event can be used.
# Step 4: Analyze the CreateBucket Event
The CreateBucket event indicates that an Amazon S3 bucket creation operation occurred.
Record the following information:
Parameter	Observation
| Field | Value |
|---|---|
| Event Time | 2026-08-05T05:38:01Z |
| User Name | rihabzh |
| Event Name | CreateBucket |
| Event Source | s3.amazonaws.com |
| AWS Region | eu-north-1 |
| Activity | S3 bucket creation |


Meaning of Important Fields

| Field | Meaning |
|---|---|
| Event Time | Time at which the activity occurred |
| User Name | User/identity associated with the activity |
| Event Name | AWS operation that was performed |
| Event Source | AWS service that generated the event |
| AWS Region | Region where the activity occurred |
| Read-only | Indicates whether the event was only a read operation or involved a change |
| Error Code | Indicates whether an error occurred |

Screenshot 3: CreateBucket event details.
<img width="1261" height="389" alt="Screenshot 2026-09-09 002617" src="https://github.com/user-attachments/assets/2ece67a5-734a-470e-b275-58a04dec8334" />

# PART C — IDENTIFY ANOTHER CLOUDTRAIL EVENT
# Step 5: Select Another Event
1.	Return to CloudTrail → Event history. 
2.	Select another event. 
3.	Open its details. 
4.	Record the important fields. 
For example, an event such as:
AutomatedDefaultVpcCreation
may be present.
This event is associated with Amazon EC2.
# Step 6: Analyze the Second Event

Record:
Parameter	Observation
Event Time	2026-08-05T05:33:58Z
User Name	rihab zh
Event Name	AutomatedDefaultVpcCreation
Event Source	ec2.amazonaws.com
AWS Region	eu-north-1
Read-only	false
Activity	Automated default VPC creation

Screenshot 4: Second CloudTrail event details.
<img width="943" height="589" alt="Screenshot 2026-09-09 002739" src="https://github.com/user-attachments/assets/87ae8828-9d5a-4efd-bfed-d8be751c1163" />


# PART D — COMPARE THE EVENTS
# Step 7: Prepare the Audit Comparison
Compare the two CloudTrail events.

| Parameter | Event 1 | Event 2 |
|---|---|---|
| Event Time | 2026-08-05T05:38:01Z | 2026-08-05T05:33:58Z |
| User Name | rihabzh | rihab zh |
| Event Name | CreateBucket | AutomatedDefaultVpcCreation |
| Event Source | s3.amazonaws.com | ec2.amazonaws.com |
| AWS Region | eu-north-1 | eu-north-1 |
| Read-only | false | false |
| Error Code | None | None |
| Activity | S3 bucket creation | Automated default VPC creation |

# PART E — SECURITY AUDIT ANALYSIS
# Step 8: Identify Who, What, When and Where

| Question | Event 1 — CreateBucket | Event 2 — AutomatedDefaultVpcCreation |
|---|---|---|
| **WHO?** | rihabzh | rihab zh |
| **WHAT?** | CreateBucket — S3 bucket creation | AutomatedDefaultVpcCreation — Automated default VPC creation |
| **WHEN?** | 2026-08-05 05:38:01 UTC | 2026-08-05 05:33:58 UTC |
| **WHERE?** | eu-north-1 | eu-north-1 |
| **RESULT?** | Successful — no error indicated | Successful — no error indicated |

# Step 9: Prepare the Final Audit Table

| Event Time | User | Event Name | Service | Region | Read-only | Result | Activity |
|---|---|---|---|---|---|---|---|
| 2026-08-05T05:38:01Z | rihabzh | CreateBucket | Amazon S3 | eu-north-1 | false | Successful | S3 bucket creation |
| 2026-08-05T05:33:58Z | rihab zh | AutomatedDefaultVpcCreation | Amazon EC2 | eu-north-1 | false | Successful | Automated VPC creation |

# RESULT
The cloud activities in AWS were successfully audited using AWS CloudTrail Event History. Different AWS events were examined based on event time, user identity, event name, event source, AWS Region, read-only status, and error status. The experiment demonstrated how AWS CloudTrail provides an audit trail for monitoring, accountability, and investigation of cloud activities.
