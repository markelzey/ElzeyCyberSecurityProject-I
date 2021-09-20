## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
- Load balancers protect a web server(s) by ensuring the incoming traffic is split between the web servers and may help protect from DDoS attacks and provide redundancy. A jumb box can limit access to an internal network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs as well as monitor system metrics like CPU usage, attempted logins, etc.
-  Filebeat watches for changes to system log files.
-  Metricbeat records metrics and statistics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.1.0.4   | Linux            |
| DVWA1    | Web Server | 10.1.0.7   | Linux            |
| DVWA2    | Web Server | 10.1.0.8   | Linux            |
| ELK      | Monitoring | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 67.210.178.131

Machines within the network can only be accessed by other machines in the network.
- The Jump-Box machine has SSH access to the ELK VM.  

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 67.210.178.131       |
| ELK      | No                  | 10.0.0.1 - 254       |
| DVWA1    | No                  | 10.1.0.1 - 254       |
| DVWA2    | No                  | 10.1.0.1 - 254       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage to using Ansible to configure ELK is that it saves time and reduces the chances for configuration errors.
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Install Python
- Configure memory
- Setup to start at system start

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- The IP addresses of the machines being monitored are 10.1.0.7 and 10.1.0.8

We have installed the following Beats on these machines:
- Filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
-  Filebeat watches for changes to system and log files on the VMs while metricbeat monitors system metrics like CPU usage, attempted logins, etc


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-install.yml file to the ansible container.
- Update the hosts file to include VM IP addresses of the webhosts.
- Run the playbook, and navigate to https://65.52.198.53:5601 to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._