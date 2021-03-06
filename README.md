## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Zarghoon2122/Elk_Project/blob/master/Diagram/Diagram.JPG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly exist, in addition to restricting permission to the network.
-What aspect of security do load balancers protect? What is the advantage of a jump box?_
Avalibilities and restrcition in the network. The Jump Box restricts the IP's access.  
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jump Box and system System logs.
- What does Filebeat watch for? It manages log files
- What does Metricbeat record? monitor system and memory usage elastic search 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name            | Function | IP Address | Operating System |
|-----------------|----------|------------|------------------|
| Jump Box        | Gateway  | 10.0.0.4   | Linux            |
| Web-1           |   DVWA   | 10.0.0.5   | Linux            |
| Web-2           |   DVWA   | 10.0.0.6   | Linux            |
| Elk-Project     |   DVWA   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Host machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
67.166.168.138

Machines within the network can only be accessed by Jump Box.
Which machine did you allow to access your ELK VM? Web-1 and Web-b What was its IP address? 10.0.0.5 and 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |        No           | 10.0.0.5 10.0.0.6    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
-  In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-  name: install filebeat deb
   command: dpkg -i filebeat-7.4.0-amd64.d

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
https://github.com/Zarghoon2122/Elk_Project/blob/master/Diagram/Elk-PS.JPG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
Jump Box- 10.0.0.4, Web-1 10.0.0.5, Web-3 10.0.0.4

We have installed the following Beats on these machines:
-  Specify which Beats you successfully installed_
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collect data from the file system. Metricbeat collect machine metrics. Ex: CPU usage, memory usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ssh-keygen file to ssh public key.
- Update the Security rule file to include the IP adress
- Run the playbook, and navigate to Gitbash to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Filebeat Where do you copy it? All the webservers
- _Which file do you update to make Ansible run the playbook on a specific machine? Host conf. file.  How do I specify which machine to install the ELK server on versus which to install Filebeat on? update tasks hosts groups, Elk or Webservers
- _Which URL do you navigate to in order to check that the ELK server is running? http://23.99.9.119:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook filebeat-playbook.yml
nano ansible.cfg to update (remote_user: sysadmin)
nano hosts to update webservers and elk IPS Ex:
[webservers]
## alpha.example.org
## beta.example.org
## 192.168.1.100
## 192.168.1.110

10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.6 ansible_python_interpreter=/usr/bin/python3
10.0.0.7 ansible_python_interpreter=/usr/bin/python3
[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3
