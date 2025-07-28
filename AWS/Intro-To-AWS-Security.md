# Introduction to AWS Security

### AWS Security Services 

AWS security can be broadly classified into categories such as Identity Management, Threat Detection, and Infrastructure Protection. Each category is associated with multiple AWS services that cater to its specific security needs.

<img width="457" height="535" alt="image" src="https://github.com/user-attachments/assets/f2c38a02-765c-488a-92ce-fb7d59a62357" />


### AWS IAM

AWS Identity and Access Management (IAM) is a service that allows organizations to securely manage access to AWS resources.  
It plays a crucial role in ensuring security and proper access management in AWS infrastructure.  
1\. AWS organizations  
2\. Users Group  
3\. Roles  
4\. Policy

<img width="648" height="460" alt="image" src="https://github.com/user-attachments/assets/9f1b18f6-bb2b-471b-ab54-9a8dc618fd7b" />


**IAM (Identity and Access Management)** security is crucial for ensuring the integrity, confidentiality, and availability of resources in cloud environments.  
1\. IAM enforces strict access controls, ensuring only authorized users and applications can access resources.  
2\. It ensures that only users or systems with the appropriate permissions can view, modify, or delete critical data.  
3\. By managing access at a granular level, IAM reduces the potential for exploitation by limiting what resources a compromised account can access.

**Access Analyzer:** It analyzes permissions to provide insights into who can access your resources, helping you ensure they are securely configured and aligned with the principle of least privilege.  
<br/>**Resource Control Policy**: Policies that directly control access to specific  
AWS resources by defining the permissions associated with them.  
<br/>**Service Control Policy**: SCPs act as a guardrail to enforce security and  
governance by restricting or explicitly allowing specific actions across all accounts or organizational units (OUs).

### AWS Guard-Duty

AWS GuardDuty is a managed threat detection service that continuously monitors your AWS environment for malicious activity, unauthorized behavior, and potential security risks. It uses machine learning, anomaly detection, and integrated threat intelligence to identify and prioritize security threats across your AWS accounts, workloads, and data.

<img width="1007" height="288" alt="image" src="https://github.com/user-attachments/assets/0a63a1f8-802e-43e5-8169-819d720860ec" />


### AWS Detective

AWS Detective is a managed security analysis and investigation service that helps you quickly identify, analyze, and investigate the root cause of security issues in your AWS environment.  
It automatically collects and organizes security-relevant data, such as log and event information, and uses machine learning and graph-based analysis to visualize relationships and patterns for effective threat investigation.

<img width="659" height="250" alt="image" src="https://github.com/user-attachments/assets/e2f6fa3b-8127-4962-b61d-7f06740a5414" />


### AWS Network Security

**WAF / AWS Shield / Network Firewall**

<img width="1053" height="419" alt="image" src="https://github.com/user-attachments/assets/50b5af9f-edc2-4d53-bf99-11d519938b22" />


# AWS Logs & It's Types

Logs are critical to securing your AWS environment as they provide visibility into activities and events across your cloud infrastructure. Proper log collection, monitoring, and analysis enable you to detect, investigate, and respond to security incidents effectively.

<img width="446" height="379" alt="image" src="https://github.com/user-attachments/assets/74099ee0-e520-43d4-89be-ab401ff75e30" />


### CLOUDTRAIL

*Tracks API calls and activities performed in your AWS account.*

<img width="1098" height="343" alt="image" src="https://github.com/user-attachments/assets/e2083d59-724c-48a1-9825-c5af0a2aafc3" />


<img width="1190" height="371" alt="image" src="https://github.com/user-attachments/assets/4d3f0fe8-a94c-4b29-b8ab-5c5acae1af60" />


**CLOUDWATCH**

*Centralized logging service for AWS and custom application logs*

<img width="1130" height="376" alt="image" src="https://github.com/user-attachments/assets/63aa163e-dce7-4f71-a338-ee351b941a1e" />


<img width="1085" height="538" alt="image" src="https://github.com/user-attachments/assets/72242ef5-0555-4fe6-838b-d1400b2dcd3e" />


<img width="1168" height="348" alt="image" src="https://github.com/user-attachments/assets/70094968-4002-4e86-897e-91530cac1562" />


### VPC FLOW LOGS & ROUTE 53

*Captures network / DNS traffic metadata for resources in a Virtual Private Cloud (VPC).*

<img width="1106" height="439" alt="image" src="https://github.com/user-attachments/assets/546a94ad-1c4c-4d37-a4a7-b51fc61e8587" />


<img width="1055" height="421" alt="image" src="https://github.com/user-attachments/assets/7e20a278-fbd2-4079-b921-b589fef80e52" />


### AWS S3 ACCESS LOGS

*Logs access requests to S3 buckets.*

<img width="1157" height="422" alt="image" src="https://github.com/user-attachments/assets/7ee03381-a206-4c69-8571-0eac398e54f8" />


<img width="1098" height="292" alt="image" src="https://github.com/user-attachments/assets/880324d8-4a6c-4ce0-9ade-3084e869c956" />


