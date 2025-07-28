# Introduction to AWS Security

### AWS Security Services 

AWS security can be broadly classified into categories such as Identity Management, Threat Detection, and Infrastructure Protection. Each category is associated with multiple AWS services that cater to its specific security needs.

![3f8c2a8ab60d3964b03f334ff60dbcf4.png](:/41fff50c81dc4bf5aa856522a1121df8)

### AWS IAM

AWS Identity and Access Management (IAM) is a service that allows organizations to securely manage access to AWS resources.  
It plays a crucial role in ensuring security and proper access management in AWS infrastructure.  
1\. AWS organizations  
2\. Users Group  
3\. Roles  
4\. Policy

![b553c059e35792901048b7dfb97e212b.png](:/8b2363b73b7c4257810778763b2ce62d)

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

![f477fbc6f2e96615c6748793e85dc793.png](:/c553c9f823884082963dbfba8a4b68ee)

### AWS Detective

AWS Detective is a managed security analysis and investigation service that helps you quickly identify, analyze, and investigate the root cause of security issues in your AWS environment.  
It automatically collects and organizes security-relevant data, such as log and event information, and uses machine learning and graph-based analysis to visualize relationships and patterns for effective threat investigation.

![c0135ac66f3396ac3f829a6cca3e5500.png](:/f81239224ca24c6bb7df6513785cecbe)

### AWS Network Security

**WAF / AWS Shield / Network Firewall**

![6d572f676dc7da37f38aea917917ee78.png](:/988a5e2c48704559a75ebe765fb836bd)

# AWS Logs & It's Types

Logs are critical to securing your AWS environment as they provide visibility into activities and events across your cloud infrastructure. Proper log collection, monitoring, and analysis enable you to detect, investigate, and respond to security incidents effectively.

![1442b6ace93311241fdadacb7414c2ca.png](:/630767f31d72476dbbf4415bf8bb88ec)

### CLOUDTRAIL

*Tracks API calls and activities performed in your AWS account.*

![73a09b281fd885698f935280fa057d56.png](:/b7def34107464a6eb0ea5b67ef6bce7b)

![0a94f93b5e853bfa60e88f93839fabe7.png](:/5043a5a057604a23a0545c7b89d08aff)

**CLOUDWATCH**

*Centralized logging service for AWS and custom application logs*

*![5a26ee8c74139256e129f46b57fa0b0d.png](:/43c4c51154ec47b9a7c9e4fa7823fe2e)*

*![b31dcc4d4254492bc58f58195796991d.png](:/a97fda1734e94e90812ed68983e0e4c8)*

*![560124ed7569511a0d533c1c475d9953.png](:/c0b894aa8adf4d4dbaf8886ba034014f)*

### VPC FLOW LOGS & ROUTE 53

*Captures network / DNS traffic metadata for resources in a Virtual Private Cloud (VPC).*

*![ac6be32e4800f09dcdd1a1e1b73a5e6a.png](:/105c60c48cd3421c83977f8964964b01)*

*![86bf6029f63e6f269c3c689532b78e88.png](:/87b5b603937747c3a16b50fc34e94e4e)*

### AWS S3 ACCESS LOGS

*Logs access requests to S3 buckets.*

*![2e75576c2adc60afce241e1d81977fea.png](:/0bc2db6c0a294f5f9bc2a338eef512da)*

*![ddcdba0f6d204c540953f45683cb2e75.png](:/045652c0ae0c4d76bdcee9770daf564a)*

*AWS Logging & Monitoring*
