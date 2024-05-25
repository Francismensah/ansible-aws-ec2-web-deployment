# Ansible Project Readme

This project sets up and deploys a simple web application using Ansible. The architecture diagram is located in the root directory of the project.

## Architecture Diagram

![Architecture Diagram](./Reference%20Architecture.jpg)

## Steps

### 1. Create the Ansible Machine Security Group (SG)

- Configure the security group to allow SSH access from your IP.

### 2. Create the Server Security Group (SG)

- Configure the security group to allow:
  - **SSH** access from the Ansible security group.
  - **HTTP** access on port 80 from the internet.

### 3. Launch the Ansible Machine

- Use Amazon Linux 2 for the Ansible machine.

### 4. Create Key Pairs on the Ansible Machine

- Generate an SSH key pair:

  ```sh
  ssh-keygen -t rsa -b 2048

### 5. Import Public Key into the EC2 Console

- Import the public key generated in the previous step into the EC2 console with the name ansible-public-key.

### 6. Launch the Servers

- Use the key pair ansible-pub-key.
- Attach the server-sg security group.

### 7. Test Connection

- Test the SSH connection to the servers using their private IPs.

### 8. Install Ansible on the Ansible Machine

- Update the package repository and install Ansible:

  ```sh
    sudo yum update -y
    sudo amazon-linux-extras install ansible2 -y

### 9. Create Inventory File

- List the private IPs of the servers in the inventory file named inventory.

### 10. Create Playbook

- Write an Ansible playbook named deploy-website.yml to deploy the website.

### 11. Test Ansible Connection

- Use the following command to test the connection:

  ```sh
  ansible all --key-file ~/.ssh/id_rsa -i inventory -m ping -u ec2-user

### 12. Create Ansible Configuration File

- Create an ansible.cfg file

### 13. Run the Ansible Playbook

- Execute the playbook to deploy the website:

  ```sh
  ansible-playbook deploy-website.yml

## Usage

- Follow the steps outlined in the Steps section to set up your Ansible environment and deploy the website.

- You have the architecture diagram in the root directory to understand the infrastructure setup better.

- Run the provided commands and use the configuration files as described.

## About

This Ansible project automates the setup and deployment of a web application on AWS EC2 instances.
