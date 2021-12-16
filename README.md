# Elk-Stack-Project
Elk-Stack-Project


![network diagram](https://user-images.githubusercontent.com/88988729/146433056-65a4123b-4af7-45ad-9c7d-0aba4087e145.PNG)

In this project I configured an ELK stack server in order to set up a cloud monitoring system. Deployed containers using Ansible and Docker, Deployed Filebeat using Ansible.

and deployed the ELK stack on a server.


Docker is a software that offers a set of platform-as-a-service products for developing and deploying applications by packaging software in containers.

Containers are lightweight, portable, virtual environments that developers can share without risking inconsistencies in development. Due to these incredibly useful features, many organizations have switched from using virtual machines to Docker containers.

Activities involved the following:

* Created a new vNet in Azure in a different region, within the same resource group.
* Created a peer-to-peer network connection between the vNets.
* Created a new VM in the new vNet that has 2vCPUs and a minimum of 4GiB of memory.
* Added the new VM to Ansible’s hosts file in the provisioner VM.
* Created an Ansible playbook that installs Docker and configures an ELK container.
* Run the playbook to launch the container.
* Restricted access to the ELK VM.

Activities involve the following:

* Navigate to the ELK server’s GUI to view Filebeat installation instructions.
* Create a Filebeat configuration file.
* Create an Ansible playbook that copies this configuration file to the DVWA VMs and then installs Filebeat.
* Run the playbook to install Filebeat.
* Confirm that the ELK Stack is receiving logs.
