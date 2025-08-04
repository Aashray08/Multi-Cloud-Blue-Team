### SETTING UP: AWS Logging & Monitoring

* * *

This project demonstrates the setup of a centralized logging and monitoring pipeline for Amazon Web Services (AWS) using the Elastic Stack (Elasticsearch, Logstash, and Kibana). The objective is to enable real-time collection, analysis, and visualization of AWS logs to support cloud security monitoring and incident response.

By integrating AWS-native services with ELK, this implementation provides a scalable solution for:

- Gaining visibility into cloud activities such as authentication events, API calls, and network traffic
    
- Investigating security incidents through structured log analysis
    
- Monitoring system behavior to detect misconfigurations, unauthorized access, and anomalous patterns
    
- Establishing a detection-driven workflow aligned with blue team and SOC operations
    

This setup reflects real-world practices in security operations and showcases how to operationalize AWS telemetry for threat detection and forensic analysis.

> This project is particularly relevant for those pursuing roles in cloud security, security operations, or threat detection engineering.

### ARCHITECTURE OVERVIEW

* * *

<img width="1226" height="552" alt="image" src="https://github.com/user-attachments/assets/dabfcee9-ccad-4c58-a66e-84eda8ce8d36" />


## AWS Services Used

* * *

This project integrates the following AWS services to enable centralized logging, secure storage, and reliable log delivery:

1.  **AWS CloudTrail**  
    Enables governance, compliance, and operational and risk auditing by recording account activity across AWS infrastructure. Used here to capture and deliver detailed logs of API calls made within the environment.
    
2.  **Amazon S3 (Private Bucket)**  
    Serves as a centralized, access-controlled storage location for collected CloudTrail logs. Ensures secure, persistent retention of log data for further analysis and compliance purposes.
    
3.  **Amazon Simple Queue Service (SQS)**  
    Acts as an intermediary buffer to decouple log producers from consumers. Ensures reliable and scalable delivery of log data to downstream components (e.g., Logstash or Filebeat) for ingestion into the ELK stack.
    

## CloudTrail Configuration

* * *

This section outlines the step-by-step process for configuring AWS CloudTrail to collect and forward logs to a centralized logging pipeline.

### Step 1: Navigating to CloudTrail

From the AWS Console, search for and open the **CloudTrail** service. This is where logging will be configured.

### Step 2: Creating the Trail

Select the **Create trail** option. On the configuration page, provide a trail name and select an S3 bucket for log storage. A private bucket is recommended to ensure secure access. KMS encryption can be enabled if required.

<img width="1595" height="724" alt="image" src="https://github.com/user-attachments/assets/7e082d29-3d8f-49f1-90dc-b6f155bf9199" />


### Step 3: Selecting Event Types

The setup allows selection of specific event types to be logged by CloudTrail:

- **Management Events** – Tracks create, update, and delete operations on AWS resources
    
- **Data Events** – Logs detailed activity such as S3 object access or Lambda executions (may produce high log volume)
    
- **Insights Events** – Detects unusual patterns in API calls and errors
    
- **Network Activity Events** – Monitors changes to networking components like subnets and security groups
    

It is recommended to enable only the event types relevant to monitoring goals to optimize log volume and cost.

<img width="1337" height="884" alt="image" src="https://github.com/user-attachments/assets/fcd7ccd7-7640-462f-9d9d-9b8e55a49c97" />


### Step 4: Finalizing the Setup

After configuring the trail, review the settings and create the trail. A success message will confirm that CloudTrail logging has been enabled and is actively collecting logs.

<img width="1791" height="462" alt="image" src="https://github.com/user-attachments/assets/f774148b-fb65-4506-973e-8d1da54bc62d" />


### Step 5: Validating Log Storage in S3

To confirm that CloudTrail logs are being delivered correctly:

- Navigate to the **S3** service in the AWS Console.
    
- Locate the designated bucket configured during the CloudTrail setup.
    
- Ensure that logs are being delivered into the expected folder structure (`AWSLogs/<account-id>/CloudTrail/...`).
    

This step verifies that log delivery from CloudTrail to the S3 bucket is active and correctly configured.

<img width="1620" height="596" alt="image" src="https://github.com/user-attachments/assets/bd70d600-d686-475f-8e69-5390706a7d03" />


### Step 6: Configuring SQS for Log Forwarding

The Simple Queue Service (SQS) is used to queue log events and forward them to the SIEM system or log processor.

#### Step 6.1: Creating the Queue

- Navigate to the **SQS** service from the AWS Console.
    
- Select **Create queue** and proceed with the default configuration settings.
    
- For basic logging and monitoring use cases, default settings are sufficient.
    
- After creation, verify that the SQS queue is successfully provisioned.
    

<img width="1494" height="400" alt="image" src="https://github.com/user-attachments/assets/178bf458-0ec9-4e59-bd6d-e170d379e99b" />


#### Step 6.2: Setting Access Permissions

To allow S3 to send messages (log events) to the SQS queue, an access policy must be added.

- Go to the **Access Policy** section of the newly created SQS queue.
    
- Click **Edit** and update the policy with appropriate permissions:
    

`{ "Version": "2012-10-17", "Id": "example-ID", "Statement": [ { "Sid": "example-statement-ID", "Effect": "Allow", "Principal": "*", "Action": "SQS:SendMessage", "Resource": "arn:aws:sqs:us-east-1:123456789:sample", "Condition": { "StringEquals": { "aws:SourceAccount": "123456789" }, "ArnLike": { "aws:SourceArn": "arn:aws:s3:*:*:cwllablog" } } } ]}`

> Note: Ensure all comments are removed before applying the JSON policy. Comments will cause the policy to be rejected due to invalid formatting.

Once the access policy is applied, the integration between S3 and SQS is complete, and the system is ready to forward log events for ingestion.

<img width="1405" height="898" alt="image" src="https://github.com/user-attachments/assets/f720b461-1f2a-4461-8445-8f70c684c277" />


### Step 7: Integrating S3 with SQS Queue

After setting up CloudTrail, the S3 bucket, and SQS with the correct access policy, the next step is to link the S3 bucket to the SQS queue through event notifications.

#### Step 7.1: Navigate to the S3 Bucket

Open the **S3** service from the AWS Console and select the bucket that was configured to receive CloudTrail logs.

#### Step 7.2: Configure Event Notifications

Go to the **Properties** tab of the S3 bucket. Scroll down to the **Event notifications** section and select **Create event notification**.

#### Step 7.3: Define Event Settings

On the configuration page, provide a name for the event notification and select the types of events to trigger notifications.  
It is recommended to select all event types (e.g., `PUT`, `POST`, `DELETE`, `CompleteMultipartUpload`) to ensure full visibility into log delivery.

#### Step 7.4: Choose the SQS Target

Under the **Destination** section, select **SQS queue** and choose the queue that was previously created for this logging setup.

#### Step 7.5: Save Configuration

After verifying the settings, save the event notification. This completes the integration between the S3 bucket and SQS.

<img width="1600" height="948" alt="image" src="https://github.com/user-attachments/assets/c9be2dbc-2636-4e0f-859c-08a2b70ae982" />


Once this is complete, the next step is to integrate the SQS queue with **Filebeat** for log collection and forwarding into the ELK stack.

### Step 8: Filebeat Configuration for AWS Log Ingestion

This section describes how to configure Filebeat on a monitoring server to collect logs from AWS and forward them to the ELK stack.

#### Step 8.1: Create IAM User for Log Access

Before configuring Filebeat, create a dedicated **IAM user** with the following permissions:

- `AmazonSQSFullAccess`
    
- `CloudTrail Read Access`
    
- `AmazonS3FullAccess`
    

Generate the **Access Key ID** and **Secret Access Key** for the user. These credentials will be required during Filebeat setup.

#### Step 8.2: Connect to Monitoring Server

Establish an SSH connection to the monitoring server or lab environment where Filebeat is installed.

#### Step 8.3: Enable AWS Module in Filebeat

Run the following command to enable the AWS module in Filebeat:

`filebeat modules enable aws`

<img width="1068" height="402" alt="image" src="https://github.com/user-attachments/assets/40d7cd54-8ea0-4734-98e6-d4e1bc4d712c" />


#### Step 8.4: Configure the AWS Module

Locate and open the `aws.yml` module file, typically found in:

`/etc/filebeat/modules.d/aws.yml`

Within the configuration, enable the **CloudTrail** section and set the following parameters:

- `enabled: true`
    
- `var.queue_url`: AWS SQS Queue URL
    
- `var.access_key_id`: IAM Access Key ID
    
- `var.secret_access_key`: IAM Secret Access Key
    
- `var.session_token` (optional): For temporary credentials, if using STS
    
- Ensure other optional services like S3 access, EC2, or VPC logs are commented out or disabled unless required.
    

#### Step 8.5: Restart Filebeat

After saving the configuration, restart the Filebeat service to apply changes:

`sudo systemctl restart filebeat`

#### Step 8.6: Validate in Kibana

To confirm successful log ingestion:

- Open **Kibana**
    
- Navigate to **Discover** and select the Filebeat index
    
- Verify that CloudTrail logs are being received and parsed correctly
    

* * *

###  Conclusion

This configuration establishes a secure and scalable log ingestion pipeline from AWS into the ELK stack using Filebeat. It enables real-time monitoring, detection, and visibility across AWS infrastructure.


&nbsp;

&nbsp;
