Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram (2)](https://user-images.githubusercontent.com/84087947/137778822-56bd6f55-dea8-42e6-91f9-83668ab24615.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/Alvarez0280/Week-13-Project-1/blob/main/Ansible/Playbook%20for%20installing%20Elk

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly avaiable, in addition to restricting inbound access to the network.

- Load Balancers protect the virtual network against DDoS attacks by shifting attack traffic between the virtual servers.
- The advantage of the Jump-Box is that it is "hidden" from the public. It can only be accessed by the administrator to perform tasks on the rest of the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file of the VM's on the network and system metrics.

- Filebeat collects data about the file system.
- Metricbeat collects machine metrics, such as uptime.


The configuration details of each machine may be found below.

| Name      | Function   | IP Address | Operating System |
|-----------|------------|------------|------------------|
| Jump Box  | Gateway    | 10.0.0.1   | Linux            |
| Web-1     | Web Server | 10.0.0.5   | Linux            |
| Web-2     | Web Server | 10.0.0.6   | Linux            |
| Elk       | Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My Public IP

Machines within the network can only be accessed by Jump Box VM.
- My Public IP

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | My Public IP         |
| VMS      | NO                  | 10.0.0.4             |
| ELK      | NO                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Using Ansible in this way allows us to quickly install, update, and add web servers to our network using the same playbooks.

The playbook implements the following tasks:
- Install docker.io and pip3
- Install Docker python module
- Increase the memory
- Download and launch docker elk container

![image](https://user-images.githubusercontent.com/84087947/138614873-7e061d70-3b5d-4d5b-b4cf-85cf733a0960.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.5
- Web-2: 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat watches for log files/locations and collect log events.
- Metricbeat records metrics and statistical data from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration files to /etc/ansible/files.
- Update the configuration files to include the IP address of the Elk Server VM and webservers
- Run the playbook, and navigate to ELK-Server-PublicIP:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? 
- Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
