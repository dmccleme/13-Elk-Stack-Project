## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![Project 1 network diagram]( https://github.com/dmccleme/13-Elk-Stack-Project/blob/main/Diagrams/project%2001-network%20diagram.drawio)
  

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

* Elk-server.yml
* Filebeat-config.yml
* Filebeat-playbook.yml
* Metricbeat-config.yml
* metricbeat-playbook.yml


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

What aspect of security do load balancers protect? 
	Load Balancing plays an important security role as computing moves evermore to the cloud. The off-loading function of a load balancer defends an organization against distributed denial-of-service (DDoS) attacks. It does this by shifting attack traffic from the corporate server to a public cloud provider.

What is the advantage of a jump box?
	A jump box is a system on a network used to access and manage devices in a separate security zone. A jump server is a hardened and monitored device that spans two dissimilar security zones and provides a controlled means of access between them. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to their file systems and system metrics.

What does Filebeat watch for?
	Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them.

What does Metricbeat record?
	Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.






The configuration details of each machine may be found below.
NOT compact version kept spreading across rows

| Name | Function | IP Address | Operating <br>System |
|---|---|---|---|
| Jump-Box<br>Provisioner | Gateway | 10.0.0.8<br>20.222.16.149 | Linux |
| RedTeam-LB | Load Balancer | 20.210.216.165 | DVWA |
| Web-01 | Webserver | 10.0.0.9<br>20.210.216.165 | Linux |
| Web-02 | Webserver | 10.0.0.10<br>20.210.216.165 | Linux |
| Web-03 | Webserver | 10.0.0.11<br>20.210.216.165 | Linux |
| Elk-Server | Kibana | 10.1.0.4<br>20.219.26.73 | Linux |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 68.104.17.79 Machines within the network can only be accessed by SSH from the Jump Box Provisioner

A summary of the access policies in place can be found in the table below.

| Name                    | Publicly Accessible | Allowed IP Addresses |
|-------------------------|---------------------|----------------------|
| Jump-Box<br>Provisioner | Yes                 | 68.104.17.79         |
| Elk-Server              | Yes                 | 68.104.17.79:5601    |
| Web-01                  | No                  | 10.0.0.1-254         |
| Web-02                  | No                  | 10.0.0.1-254         |
| Web-03                  | No                  | 10.0.0.1-254         |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible?
       The main advantage of automating configuration with Ansible is that it enables IT administrators the ability to automate your daily work tasks and give the administrator more time to focus on the needs of the business.

The playbook implements the following tasks:
* configure to use more memory
* install docker.io
* install python3-pip
* install docker python module
* install elk stack
* enable docker service


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

* docker PS command
 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
* Web-01 (dvwa) 10.0.0.9
* Web-02 (dvwa) 10.0.0.10
* Web-03 (dvwa) 10.0.0.11

We have installed the following Beats on these machines:
* Filebeat
* Metricbeat

These Beats allow us to collect the following information from each machine:
* Filebeat collects system logs and one example would be audit logs for users
* Metricbeat collects machine metrics, some examples are CPU usage


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config file to /etc/ansible/
- Update the filebeat-config.ynl file to include the ELK-sever private IP
- update the host file to include the webservers and the elk server
- Run the playbook, and navigate to http://20.49.3.56:5601/app/kibana to check that the installation worked as expected.


_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_/etc/ansible/elk.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat /etc/ansible/hosts

- _Which URL do you navigate to in order to check that the ELK server is running? http://20.207.206.29:5601/app/kinana
 


