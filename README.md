# Mediawiki - RHEL 8
This repository contains the Ansible Playbook to setup Mediawiki on RHEL 8. Mediawiki is a LAMP application.

## File Details
* **Mediawiki_Playbook.yml** : Playbook for setting up pre-requisites, installing & configuring Mediawiki.
* **roles** : Different roles which are used by Mediawiki_Playbook.yml
* **RHEL-8-Ansible.template** : AWS CLoudFormation template to setup RHEL 8 EC2 server with Ansible.
* **Mediawiki LAMP - AWS CFT and Ansible.docx** - How to execute this Repo, Screenshots and results.

## How to Use?
One must use the CLoudFormation template and it will create RHEL 8 based EC2 infra followed by installing/configuring Mediawiki.

### AWS CloudFormation Template
1. Before running this CFT, create a key pair in EC2 
2. Before running this CFT, create an IAM role for cloudformation
3. Upload the template in S3 and use the S3 URL to create the stack via coudformation **or** copy the content in cloudformation's stack designer to create the stack.
4. As this install multiple items (yum update, yum install ansible git python3 etc, application setup etc.), process takes time.

### Ansible Playbook
CloudFormation pulls this repository for the ansible playbook and execute it as user data, automatically.

### CI:CD Pipeline
Execute the CFT template via CLI from a job in CI:CD pipline and it will internally install ansible & setup mediawiki via playbook.

### Scaling of Mediawiki
1. Host a centralised DB on a seperate set of servers.
2. Add servers to App & DB as per the load.
3. Keep all the servers in a same network.
