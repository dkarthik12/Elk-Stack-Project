# Elk-Stack-Project
Elk-Stack-Project


![image](https://user-images.githubusercontent.com/88988729/146611234-01d97bf5-ec76-4b01-9d3c-400191feef2f.png)


In this project I configured an ELK stack server in order to set up a cloud monitoring system. Deployed containers using Ansible and Docker, Deployed Filebeat using Ansible.

and deployed the ELK stack on a server.


Docker is a software that offers a set of platform-as-a-service products for developing and deploying applications by packaging software in containers.

Containers are lightweight, portable, virtual environments that developers can share without risking inconsistencies in development. Due to these incredibly useful features, many organizations have switched from using virtual machines to Docker containers.

These were the activities involved in setting up the whole process; 

* A new vnet was created in Azure in a different region, within the Azure resource group.
* Created a peer-to-peer network connection between the vNets.
* Added the new VM to Ansible’s hosts file in the jump box provisioner VM.
* Created an Ansible playbook that installs Docker and configures an ELK container.
* Ran the playbook to launch the container.
* Restricted access to the ELK VM.

Next we did the following; 

* Navigated to the ELK server’s GUI to view the Filebeat installation instructions.
* Created a Filebeat configuration file.
* Created an Ansible playbook that copies this configuration file to the DVWA VMs and then installs Filebeat.
* Ran the playbook to install Filebeat.
* Confirmed that the ELK Stack is receiving logs.

Description of the Topology

The main purpose of this network was to expose a load-balanced and monitored instance of DVWA, the Vulnerable Web Application. By utilizing one virtual machine as the Jump-Box-Provisioner ,the containers in other VMs can be easily modified if needed without having to login and go through each VM or container individually. Automated and simplified maintenance was the key aspect of creating this jump box provisioner. 

Load balancing ensures that the application will be highly efficient, in addition to keeping traffic in the network running smoothly. By distributing HTTP traffic between webservers, the webservers and the network will not be overwhelmed by hundreds or even thousands of user requests; this is why load balancers are so crucial in cyber security, as they not only help in applications running smoothly, but also help prevent attacks such as DoS attacks.

By intergrating our ELK applications with DVWA and modules such as Filebeat, the webservers can be easily monitored for further analysis, which will be useful in mitigating or spotting an attack.

*The ELK server was placed in its own virtual network, and required peering between networks in order to work with the webservers. However, the ELK server would also work if it were placed within the same virtual network.

![image](https://user-images.githubusercontent.com/88988729/146613271-c787a326-4860-4999-a8da-46ddb6d33587.png)

Access Policies
The machines on the internal network are not exposed to the public Internet. Only the Jumpbox machine can accept connections from the Internet. 

The Elk-Server is configured to monitor web-1 and web-2 virtual machines. 

We have installed filebeat on the virtual machines. Filebeat: can handle audit logs, deprecation logs, garbage collection (gc) logs, server logs, and slow logs.

Filebeat-Playbook - This playbook pulled the download, config file, and .yml file for Filebeat
Filebeat keeps the simple things simple.
Filebeat ships with modules for observability and security data sources that simplify the collection, parsing, and visualization of common log formats down to a single command. They achieve this by combining automatic default paths based on your operating system, with Elasticsearch Ingest Node pipeline definitions, and with Kibana dashboards. Plus, a few Filebeat modules ship with preconfigured machine learning jobs.

Access policies can be found in the table below;

![image](https://user-images.githubusercontent.com/88988729/146615020-a7a6ca06-bfa0-45c3-8d82-c0d38c89b3b5.png)

Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which limits the possibility of human error. However, it should be noted that the syntax or commands within configuration files and playbooks may need to be changed to better suit particular virtual machines or needs. For example, the command curl in the file filebeat-playbook.yml may need to be changed from to wget.

Filebeat Installation and Configuration:
Run docker container list -a to verify that the container is on in Gitbash.
Run: curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat >> /etc/ansible/filebeat-config.yml
After entering the information into the Filebeat configuration file and Ansible playbook, you should have run: ansible-playbook filebeat-playbook.yml

Filebeat Installation:
Filebeat helps generate and organize log files to send to Logstash and Elasticsearch. Specifically, it logs information about the file system, including which files have changed and when.

Filebeat is often used to collect log files from very specific files, such as those generated by Apache, Microsoft Azure tools, the Nginx web server, and MySQL databases.

Since Filebeat is built to collect data about specific files on remote machines, it must be installed on the VMs you want to monitor.

               The ELK server is receiving logs and I had successfully deployed a live, functional ELK stack and now have plays that can:

* Install and launch Docker containers on a host machine.
* Configure and deploy an ELK server.
* Install Filebeat on any Debian-flavored Linux server.


We then confirmed that the ELK stack was receiving logs. 

Beats in Use

This ELK server is configured to monitor "Web-1" (10.10.0.6) and "Web-2" (10.10.0.7); both VMs have Filebeat installed in order to send syslogs and auditd logs to Kibana for easy monitoring, but by simply editing or creating new playbooks, more modules (such as kafka or apache) or shippers (such as Metricbeat) can be installed to monitor other types of logs or data.



