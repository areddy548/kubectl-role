# kubectl-role

This repository can be used to install kubectl on Virtual machine from Ansible-Galaxy Role **andrewrothstein.kubectl** .

These playbooks are intended to be a reference and starter's guide to building Ansible Playbooks for use with IBM Cloud and Schematics. These playbooks were tested on CentOS 7.x so we recommend that you use CentOS or RHEL to test these modules. In this deployment we install a kubectl on Vortual Machine.

Schematics Actions uses SSH to configure target VSIs on IBM Cloud. To ensure that all access to the target VSIs is secured it is assumed that SSH access is configured via a bastion host/jump server om IBM Cloud. This [IBM Cloud Automation repo](https://github.com/Cloud-Schematics) contains a number of example Terraform configs that deploy a VPC Gen 2 environment with bastion host access.

This playbook has been run and tested using VSIs in a VPC Gen2 environment, deployed using the IBM Cloud Multitier VPC Bastion LAMP example. To provision Multitier VPC Bastion LAMP on IBM cloud follow the steps [here](https://github.com/Cloud-Schematics/multitier-bastion-vpc-lamp)

## Prerequisites :

   - Ansible 1.2.9
   - [Multitier VPC Bastion LAMP](https://github.com/Cloud-Schematics/multitier-bastion-vpc-lamp)
   - SSH Key on IBM Cloud

## Running the playbook locally
 To run this example locally, create a hosts file in the root of the example folder and update it with the {target-host-ip}, {jump-server-ip} and respective ssh keys. Details of how to configure the host file manually can be found in the [Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html#inventory-basics-formats-hosts-and-groups). 
 The kubectl can be installed using the following 
- commands:
    - ansible-galaxy role install roles/requirements.yml -p roles
    - ansible-playbook kubectlplaybook.yml -i hosts


**Steps** : 

1. Create an Action from schematics, Select playbook from this repository *kubectlplaybook.yml* in Settings page.

2. Provide your Virtual machine details in IBMCloud Resource Inventory tab.

2. Click on Run Action which will download the role from ansible-galaxy and run ansible-playbook command to install the kubectl.

**Results** : 

Log into your Virtual machine and check whether Kubectl is installed or not.
