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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.

* Filebeat monitors specified log files, collects log events, and forwards the events to a log collector
* Metricbeat collects metrics from the OS and running services, and fowards the events to a log collector

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

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
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
