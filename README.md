## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Nastri_CloudDiagram](https://user-images.githubusercontent.com/73609036/114790137-779ac980-9d41-11eb-9dfd-1e8f34c02b0f.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

 [install-docker.yml.txt](https://github.com/Matmoe-exe/DU_CyberSecurityProject1/files/6314110/install-docker.yml.txt)


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access and traffic to the network.

-What aspect of security do load balancers protect?
	
Load balancers protect the (A)vailability leg of the triad. It does so by ensuring the network traffic is displaced evenly, thus not allowing the dockers or machines to be overloaded.

-What is the advantage of a jump box?
	
A jump box or jump server is a hardened and monitored machine that spans accross two dissimila security zones, allowing controlled access between the zones.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.

What does Filebeat watch for?

Filebeat monitors the log files or locations that you specify for the machine. It then collects log events, and sends them over to Elasticsearch or Logstash for representation.

The configuration details of each machine may be found below.


| Name      | Function         | IP Address    | Operating System |
|-----------|------------------|---------------|------------------|
| Jump Box  | Gateway          | 52.137.65.113 | Linux            |
| Web-1     | Docker Server    | 10.0.0.5      | Linux            |
| Web-2     | Docker Server    | 10.0.0.6      | Linux            |
| Web-3     | Docker Server    | 10.0.0.7      | Linux            |
| ELK-Stack | Security Monitor | 10.1.0.4      | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the administrator's private IPv4 address.

Machines within the network can only be accessed by the Jump Box via SSH.

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Address   |
|-----------|---------------------|----------------------|
| Jump Box  | Gateway             | Admin's IP via SSH   |
| Web-1     | Docker Server       | Jump Box Internal IP |
| Web-2     | Docker Server       | Jump Box Internal IP |
| Web-3     | Docker Server       | Jump Box Internal IP |
| ELK-Stack | Security Monitor    | Admin's IP via HTTPS |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time, provides an easy to execute automation, and it is easily repeatable across multiple machines.

The playbook implements the following tasks:
- Installs the Docker application
- Installs the Python3 translator
- Installs the Elk docker
 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[install-elk.yml.txt](https://github.com/Matmoe-exe/DU_CyberSecurityProject1/files/6314219/install-elk.yml.txt)

This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify for the machine. It then collects log events, and sends them over to Elasticsearch or Logstash for representation.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml to the /etc/ansible/files directory.
- Update the /etc/ansible/hosts file to include the ELK category that contains the IP of the ELK machine.
- Run the playbook, and navigate to http://ELK_IP/app/kibana
