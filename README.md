# ELK-Project
SMU Project One - September 2021 CyberSecurity Bootcamp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[![RED TEAM RG.PNG](https://github.com/scruzy666/ELK-Project/blob/main/Images/RED%20TEAM%20RG.PNGzy666/ELK-Project/blob/main/Images/RED%20TEAM%20RG.PNG "RED TEAM RG.PNG")](https://github.com/scruzy666/ELK-Project/blob/main/Images/RED%20TEAM%20RG.PNG "RED TEAM RG.PNG")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [my-playbook.yml](http://https://github.com/scruzy666/ELK-Project/blob/main/Ansible/my-playbook.yml "my-playbook.yml")
  -[filebeat-config.yml](http://https://github.com/scruzy666/ELK-Project/blob/main/Ansible/filebeat-config.yml "filebeat-config.yml")
  -[filebeat-playbook.yml](http:/https://github.com/scruzy666/ELK-Project/blob/main/Ansible/filebeat-playbook.yml/ "filebeat-playbook.yml")
  -[install-elk.yml](http://https://github.com/scruzy666/ELK-Project/blob/main/Ansible/install-elk.yml "install-elk.yml")
  -[ansible.cfg](http://https://github.com/scruzy666/ELK-Project/blob/main/Ansible/ansible.cfg "ansible.cfg")

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting traffic to the network.
- Load balancers help the system when there are attacks from DDoS by sending traffic somewhere else. The main advantage of running a jumpbox is to improve security. Jumpbox prevents all Azure VM's from being exposed to the public by blocking IP addresses, thus improving security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Firebeat monitiors log files, collects log events, and forwards them to Elasticsearch. It is a lightweight shipper for forwarding and centralizing data. 
- Metricbeat is also a lightweight shipper that takes the metrics and statistics that it collects and ships them to the output the user specifies, such as, Elasticsearch.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web 1    | Web Server| 10.0.0.5   | Linux            |
| Web 2    | Web Server| 10.0.0.6   | Linux            |
| Elk VM   | ELK Server| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- *Home IP Address*

Machines within the network can only be accessed by SSH keys via port 22. Inbound groups have been created to keep the machines more secure.
- JumpBox is able to be accessed by IP: 52.165.192.71

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.4             |
| Web 1    | No                  | 10.0.0.5             |
| Web 2    | No                  | 10.0.0.6             |
| ELK VM   | No                  | 10.4.0.1             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- This allows developers, techs, and other users to quickly input commands to various servers from one playbook.

The playbook implements the following tasks:
- Installs docker.io 
- Installs python3-pip
- Install docker module
- Sets the vm.max_map_count to 262144
- Downloads & launches a docker Elk VM

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[![docker_ps_output](https://github.com/scruzy666/ELK-Project/blob/main/Images/elk%20docker%20ps.PNG "docker_ps_output")](http:https://github.com/scruzy666/ELK-Project/blob/main/Images/elk%20docker%20ps.PNG// "docker_ps_output")

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1: 10.0.0.5
- Web 2: 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- The Firebeat allow us to collect data about the files in the system, wheveras, Metricbeat collect the machines metrics over a period of time. Both of these machines are important for their own specific reason, however, they are an excellent visulization resource/tool for the users to see what is going on within the files & the system. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to /etc/ansible from your ELK VM.
- Update the hosts file within the ansible to include proper web servers + IP address for the Elk VM.
- Run the playbook, and navigate to kibana to check that the installation worked as expected.


