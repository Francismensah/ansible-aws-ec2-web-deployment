## Jenkins Installation Playbook (install-jenkins.yml)

This document provides an overview of the Ansible playbook (`install-jenkins.yml`) for installing and configuring Jenkins on a single server.

**Requirements:**

* Ansible installed and configured
* EC2 instance accessible by Ansible with user permissions

**Inventory:**

The `inventory` file defines the target server:

* **jenkins-server:** This group specifies the server with the IP address `172.31.21.202` (you can modify this to match your actual server IP).

**Ansible Configuration (ansible.cfg):**

The `ansible.cfg` file sets some default values for Ansible:

* **remote_user:** This specifies the user to connect to the remote server (default: `ec2-user`).
* **inventory:** This defines the location of the inventory file.
* **private_key_file:** This sets the path to your SSH private key file (default: `~/.ssh/id_rsa`).
* **host_key_checking:** This disables host key checking for demonstration purposes (**WARNING:** not recommended for production environments).

**Playbook (install-jenkins.yml):**

The `install-jenkins.yml` playbook defines the tasks for installing and configuring Jenkins:

1. **Update Packages (yum):** Updates all installed packages on the target server.
2. **Add Jenkins Repository:** Downloads the Jenkins repository file and places it in the appropriate location.
3. **Import Jenkins Key:** Imports the GPG key from Jenkins to verify package authenticity.
4. **Update Packages (again):** Updates the package list after adding the Jenkins repository.
5. **Install Java:** Installs Java OpenJDK 11 using the Amazon Linux Extras package manager.
6. **Install Jenkins:** Installs the Jenkins package using yum.
7. **Start Jenkins:** Starts the Jenkins service using systemd.

**Security Note:**

Disabling host key checking in the `ansible.cfg` is for demonstration purposes only. In a production environment, you should always enable host key checking to ensure you're connecting to the intended server.

**Usage:**

1. Ensure you have properly configured Ansible and have the necessary SSH key configured for access.
2. Update the `inventory` file with the correct IP address for your Jenkins server if needed.
3. Run the following command to execute the playbook:

```
ansible-playbook install-jenkins.yml
```

This will install and start the Jenkins service on your target server. 