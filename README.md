## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/calpoly1/cybersecurity/blob/main/Images/azure.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

* Load balancing is configured for high avalailability and security measures, such as DDoS attacks. 
* The advantage of using a jumpbox is to minimize the risk of exposing the entire network to the outside world.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

* Filebeat monitors specified log files, collects log events, and forwards the events to a log collector
* Metricbeat collects metrics from the OS and running services, and fowards the events to a log collector

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| JumpBox  | Gateway  | 10.0.0.4   | Linux 18.04      |
| Web1 VM  |  DVWA    | 10.0.0.5   | Linux 18.04      |
| Web2 VM  |  DVWA    | 10.0.0.6   | Linux 18.04      |
| web3 VM  |  DVWA    | 10.0.0.7   | Linux 18.04      |
| ELK-VM   |  ELK     | 10.1.0.4   | Linux 18.04      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine, the load balancer, and the ELK VM can accept connections from the Internet. Access to these machines is only allowed from the following IP addresses:
* IP: 160.194.24.63

Machines within the network can only be accessed by the JumpBox to minimize network exposure.  Any VM on the network can be access through the JumpBox. The IP address of the JumpBox, as stated above, is 10.0.0.4.

A summary of the access policies in place can be found in the table below. Web1-3 can be access via the load balancer's public IP, which will bring up the DVWA websites.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| JumpBox  | Yes                 | 160.194.24.63        |
| Web1 VM  | No                  | 10.0.0.4             |
| Web2 VM  | No                  | 10.0.0.4             |
| Web3 VM  | No                  | 10.0.0.4             |
| ELK VM   | Yes                 | 160.194.24.63        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because multiple configurations can be made automatically.  By using automating configurations, we can troubleshoot and monitor installations from one source, eliminating points of failure.

The playbook implements the following tasks:

* Configure ELK VM with a Docker installation
* Install Python 3 pip module
* Use the pip module to install a Docker module
* Direct the ELK VM to increase virtual memory
* Download and launch a docker ELK container with published ports set to 9200, 5844, and 5601 for Elasticsearch, Logstash, and Kibana respectively.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![alt text](https://github.com/calpoly1/cybersecurity/blob/main/Images/docker_status.PNG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
* Web-1 (10.0.0.5), Web-2 (10.0.0.6), and Web-3 (10.0.0.7)

We have installed the following Beats on these machines:
* Filebeat
* Metricbeat

These Beats allow us to collect the following information from each machine:
* Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

* Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to /etc/ansible/files
- Update the config file to include the host and port number
- Run the playbook, and navigate to the destination VM to check for the application.

* The config files are located in /etc/ansible/files
* The playbook files are located in /etc/ansible/roles
* To specify the servers that get either filebeat or metricbeat, you must update the "hosts" section within the playbook files

To connect to the Elk Server to use Kibana, you can navigate to the public facing IP: 23.100.46.201:5601
