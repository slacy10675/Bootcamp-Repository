## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/NetworkDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - elkplaybook.yml.

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
- Load balancers protect the security aspect of availability. A jump box helps restrict access to specific machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat watches for logs related to specific files
- Metricbeat records machine metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function   | IP Address | Operating System |   |
|----------------------|------------|------------|------------------|---|
| Jump-Box-Provisioner | Gateway    | 10.0.0.4   | Linux            |   |
| Web1                 | Web server | 10.0.0.5   | Linux            |   |
| Web2                 | Web server | 10.0.0.6   | Linux            |   |
| ELKStack             | ELK Stack  | 10.1.0.4   | Linux            |   |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.32.208.226

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Jump-Box-Provisioner can access ELKStack with IP address 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses                     |
|----------------------|---------------------|------------------------------------------|
| Jump-Box-Provisioner | Yes                 | 10.0.0.5 10.0.0.6 10.1.0.4 73.32.208.226 |
| Web1                 | No                  | 10.0.0.4                                 |
| Web2                 | No                  | 10.0.0.4                                 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Less chance of human error

The playbook implements the following tasks:
- Install docker
- Increase memory
- Download docker container
- Enable docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/dockerps_results_from_elk_server.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4
- 10.0.0.5

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data from specific files which we use to track events related to that file or software

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible container.
- Update the playbook file to include...
- Run the playbook, and navigate to  to check that the installation worked as expected.

- Playbook is a YAML file. Copy it to Ansible container
- Update the playbook file to run on specific machine. Change value of "hosts" to "elk" to run on elk server or to "webservers" to run on web servers
- Go to http://<Elk.server.external.IP>:5601/app/kibana to check that ELK server is running

