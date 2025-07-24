### DEPLOYING A MULTI-CLOUD SECURITY MONITORING STACK

* * *

As a part of the monitoring lab, I will be deploying the necessary services and installing procedures to set up a centralized multi-cloud SecOps environment.

<img width="1343" height="794" alt="image" src="https://github.com/user-attachments/assets/021cf199-b724-41ba-b18b-0c1fd8d19436" />

### DEPLOYMENT SUMMARY

* * *

Local or Cloud Instance Machine: Initial Requirements for Monitoring Lab Deployment  
● Set up the environment: Deploy a suitable cloud-based instance.  
● Install ELK Stack: Download and install Elasticsearch, Logstash, and Kibana to create a functional SIEM system.  
● Add Filebeat: Install Filebeat to collect and forward logs to Elasticsearch for real-time monitoring.  
● Integrate Cloud Services: Configure cloud services to send logs and security events to the lab.

### LAB Prerequisites

* * *

<img width="1552" height="783" alt="image" src="https://github.com/user-attachments/assets/f89743eb-3271-4c02-8479-501abc755875" />

### Deploying EC2 Instance and Establishing SSH Session

* * *

**Step 1: Configure the instance**  
The first and most important step is to create an EC2 instance, following the prerequisites mentioned above.

<img width="1508" height="819" alt="image" src="https://github.com/user-attachments/assets/29335cfe-9098-45fa-ae61-54c4ada46f37" />

**Step 2: Choosing the appropriate instance type**  
If the Elastic service requires higher compute capacity, it is recommended to use an instance type of at least t2.xlarge.  
It is recommended to check the pricing and billing for the service before setting it up and running.

**Step 3 : Network configuration**  
For network configuration, it is recommended to enable the Public IP and allow SSH access.  
Once the cloud instance is deployed and initiated, we need to modify or enable the ports required for Elastic and Kibana services.

<img width="1667" height="888" alt="image" src="https://github.com/user-attachments/assets/b27185f3-a3ca-4fec-81fc-cd9f1eb88b4d" />

**Step 4: Launch Instance**  
After successfully configuring as per the above mentioned recommendations we can get to be launch our EC2 and proceed taking the SSH session over the deployed EC2 instance.

<img width="1759" height="843" alt="image" src="https://github.com/user-attachments/assets/99e3dbe2-228d-4e4a-baed-525e6f3f7341" />

Then, open command line and take over the SSH session using the command highlighted.

<img width="1726" height="867" alt="image" src="https://github.com/user-attachments/assets/1e2b07a0-3bab-46f0-9d32-9812f3faefd4" />

### Installing the ELK: SIEM

* * *

**Step 1: Configuring Elastic Repository over the base machine**  
Before configuring Elastic/Kibana, it is recommended to set up the required repositories for the installation.  
`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg`  
<br/>`echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg]`  
`https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list`  
<br/><img width="1237" height="688" alt="image" src="https://github.com/user-attachments/assets/b24244ca-44fd-4532-9358-95248487c539" />

**Step 2: Install Elasticsearch over the instance**  
`sudo apt install elasticsearch`

<img width="1190" height="704" alt="image" src="https://github.com/user-attachments/assets/faf3e8f4-f41d-4f54-8d49-4a5f19b1c13c" />
 
<br/>Once the installation is successfully completed, we can enable the Elastic service and start Elasticsearch.  
<br/>`sudo systemctl enable elasticsearch.service`  
`sudo systemctl start elasticsearch.service`  
<br/><img width="1091" height="615" alt="image" src="https://github.com/user-attachments/assets/0ef9fb9b-07b6-4cc2-97a4-32343a169343" />

**Step 3: configuring the elasticsearch.yml**  
After the service is successfully installed, we can proceed with modifying the configuration located in the /etc/elasticsearch/elasticsearch.yml directory.  
`sudo nano /etc/elasticsearch/elasticsearch.yml`

<img width="984" height="632" alt="image" src="https://github.com/user-attachments/assets/d3679c3f-ca40-4154-8a4e-0aa75aa2c24b" />

**Step 4: Testing the Deployed Elasticsearch Service**  
Once all the required installations and configurations are complete, validate the setup by either running the command below or accessing the service using the configured IP and port.  
`sudo systemctl status elasticsearch.service`

<img width="1588" height="790" alt="image" src="https://github.com/user-attachments/assets/98b8a94a-d972-4ac8-9300-eeac5f21ab00" />

Now, we go back to the AWS services to edit the inbound rules for the instance as follows and open port 5601 and 9200.

<img width="1642" height="537" alt="image" src="https://github.com/user-attachments/assets/8a8614f2-340d-4222-b1b5-d4e23827ab23" />

We can also check if the Elasticsearch is working properly by going to the URL. <img width="936" height="470" alt="image" src="https://github.com/user-attachments/assets/34de5132-e125-419c-81e7-6754bfe7f638" />


### Deploying and configuring the Kibana service

* * *

**Step 1: Installing the kibana service  
**  
`sudo apt install kibana`

<img width="1096" height="606" alt="image" src="https://github.com/user-attachments/assets/38391063-3622-48b1-bed5-49d1f7356794" />

**Step 2: Configuring the kibana.yml  
**  
Once configured, proceed to modify the settings in the /etc/kibana/kibana.yml file.  
`sudo nano /etc/kibana/kibana.yml`

<img width="1095" height="552" alt="image" src="https://github.com/user-attachments/assets/9de334b3-4659-4540-b7bb-38264ddf578c" />

Modifying the above-mentioned configuration allows global access to the Kibana service.   
`sudo systemctl restart kibana.service`

**Step 3: Starting the kibana service  
<br/>**Once all the required installations and configurations are complete, enable the Kibana service and start it.  
`sudo systemctl enable kibana`  
`sudo systemctl start kibana`

  
**Step 4: Validate the Deployed Kibana Service  
**  
After completing all the required installations and configurations, validate the setup by either running the command below or accessing the service using the configured IP and port.  
`sudo systemctl status kibana.service`

<img width="1103" height="604" alt="image" src="https://github.com/user-attachments/assets/c088af14-82b8-43ac-9a19-61f65db58069" />

Now, Also verify going to a browser and accessing the kibana port.  

<img width="1146" height="691" alt="image" src="https://github.com/user-attachments/assets/533dcfd3-3db6-4843-879e-f12f68ba3d75" />

<img width="1107" height="429" alt="image" src="https://github.com/user-attachments/assets/471cb1c2-2d8d-4467-8219-bae2977918a7" />

<img width="1063" height="675" alt="image" src="https://github.com/user-attachments/assets/8df2243f-3b6e-4524-9148-57aea44b8760" />

<img width="1127" height="686" alt="image" src="https://github.com/user-attachments/assets/4deafcfc-027f-4b74-8e7c-5da93be45f14" />

<img width="1103" height="393" alt="image" src="https://github.com/user-attachments/assets/93fd7a04-f0ae-4cc3-a45b-f1384779ac4f" />

<img width="1013" height="834" alt="image" src="https://github.com/user-attachments/assets/3c772b89-2607-4acb-ae46-3dddd56de829" />

### FileBeat Integration

* * *

Filebeat is an alternative to Elastic Agent, designed for collecting logs from multiple sources. It will be installed with default, built-in modules, including those for multi-cloud environments. We will utilize these pre-built modules to configure Filebeat for log collection.  
<br/>`curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.17.2-amd64.deb`  
Once Filebeat is downloaded, we can install the Filebeat service by executing the following command.  
`sudo dpkg -i filebeat-8.17.2-amd64.deb`  
To validate the installation, execute the following command on the deployed host machine.  
`sudo systemctl status filebeat.service`  
Once you receive a green signal, it confirms that Filebeat has been successfully deployed on the host machine.

<img width="1090" height="582" alt="image" src="https://github.com/user-attachments/assets/f1ac51a4-6768-4166-ad9d-2684d8318d1c" />
The information mentioned above provides a detailed overview of Filebeat deployment and its associated configuration. Now that we have deployed and validated Elastic, Kibana and Filebeat, it's time to integrate multi-cloud environments with the SIEM.

&nbsp;
