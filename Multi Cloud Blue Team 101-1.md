# **Introduction to Multi Cloud Blue Teaming**

An enterprise might use AWS for its scalability, Azure for seamless integration with Microsoft services, and GCP for advanced data analytics. Multi cloud architectures are designed to provide flexibility.

An effective multi-cloud architecture enables organizations to optimize their use of multiple cloud providers while ensuring cost efficiency and operational resilience.

**On-premise advantages:**

Full control over hardware, software, and data.  
Optimized for latency-sensitive applications with direct access to local resources.  
Predictable costs after initial investment in hardware and infrastructure.  
Deployments are slower due to hardware provisioning and setup.

**Multi-Cloud Advantages:**

Flexibility to use the best services from multiple providers  
Scalable resources can handle spikes and heavy workloads across multiple regions.  
Pay-as you go pricing enables cost optimization and flexibility without large capital investments.  
Rapid deployment of services and applications with pre-configured cloud solutions

**On-prem Infrastructure**

Enterprises manage and maintain all hardware, software, and networking resources within their physical facilities. This approach was the standard for IT operations before the rise of cloud computing.

**Multi Cloud Infrastructure**

Multi-cloud infrastructure involves the strategic use of multiple cloud service providers, such as AWS, Azure and Google cloud platform to manage workloads, applications and data. It provides organizations with flexibility, redundancy and access to the unique features of different providers while reducing reliance on a single vendor.

* * *

# Multi-Cloud Security Challenges

**Common Misconfiguration**

Multi-cloud environments inherently involve multiple platforms and services, each with its configurations, APIs and security controls, creating a larger attack surface for adversaries to exploit.   
Here, are some statistics that are associated with multi-cloud attacks.  
43% of cloud intrusions via Valid Account   
47% of critical misconfigurations over IAM  
67% of cloud security incidents involve attempts at privilege escalation  
36% of cloud environments had insecure cloud service provider default settings

Threats targeting multi-cloud infrastructure

**Resource Hijacking**

Unauthorized use of an organization's cloud computing resources for malicious purposes. Typically, adversaries target cloud infrastructure to consume computational power, storage, or network bandwidth, often without the knowledge or consent of the cloud resource owner.  
AWS EC2 - C5.large (Compute-optimized) ⚬ Monthly cost: $0.096 × 24 × 30 = ~$69.12. • GCP - N2D-Standard-4 (High-performance) ⚬ Monthly cost: $0.173 × 24 × 30 = ~$124.56. • Azure - F4s_v2 (Compute-optimized) ⚬ Monthly cost: $0.085 × 24 × 30 = ~$61.20

![988de6d705eef642ccc29c2f223b97d1.png](../_resources/988de6d705eef642ccc29c2f223b97d1-1.png)

**Data Destruction**

Intentional deletion of sensitive data stored within cloud infrastructure. This can result from malicious activities or alternatively Sophisticated attackers may corrupt data during long-term infiltration campaigns to disrupt operations.  
Data destruction in the cloud poses significant risks to organizations, from operational disruptions to reputational damage.

![0af627e7a6c629da307ee30c2393c72a.png](../_resources/0af627e7a6c629da307ee30c2393c72a-1.png)

**IMDS CREDENTIAL ACCESS**

The Instance Metadata Service (IMDS) is a critical component in cloud environments that provides instance-specific metadata, including temporary credentials for accessing cloud services. While essential for many legitimate operations, it is a prime target for attackers seeking to exploit misconfigurations or vulnerabilities to gain unauthorized access to cloud resources.

![bd9f856ce1e301500927bad580d25c75.png](../_resources/bd9f856ce1e301500927bad580d25c75-1.png)

**CLOUD-SPECIFIC RANSOMWARE**

Ransomware targeting data and services hosted in cloud environments. Unlike traditional ransomware, which primarily focuses on on-premises systems and endpoints, cloud ransomware exploits the unique characteristics and vulnerabilities of cloud infrastructure.

![a37224bef22f86ea424bdae32cb78339.png](../_resources/a37224bef22f86ea424bdae32cb78339-1.png)

Threat landscape: Three major adversaries that target multi-cloud environment   
SCATTERED SPIDER UNC3944  
COZY BEAR APT29  
COSMIC WOLF UNC1326

![4d07fb3b7746781bfca883751f2ef84e.png](../_resources/4d07fb3b7746781bfca883751f2ef84e-1.png)

**MITRE CLOUD MATRIX**

![b512b1265a8c18c643a7aa1c65dfddd4.png](../_resources/b512b1265a8c18c643a7aa1c65dfddd4-1.png)

**LACK OF MONITORING AND LOGGING**

Monitoring and logging are crucial components of a comprehensive security and operational strategy for any  
cloud environment. They provide organizations with real-time insights into the health, performance, and security  
of their systems, allowing them to detect issues early, prevent potential breaches, and ensure compliance.

In a multi-cloud environment, effective monitoring and logging become even more important, as they help unify visibility across disparate cloud platforms, making it easier to detect and respond to incidents promptly.

1\. Threat Detection and Incident Response  
2\. Compliance and Auditing  
3\. Operational Visibility and Performance Monitoring  
4\. Detecting Misconfigurations and Vulnerabilities  
5\. Threat Hunting and Security Posture Management

&nbsp;