## Jupiter Website Deployment Playbook

This README file provides an overview of the Ansible playbook for deploying a Jupiter website on an EC2 instance.

**Requirements:**

* Ansible installed and configured
* EC2 instances accessible by Ansible

**Inventory:**

The `inventory` file included specifies the IP addresses of the target EC2 instances:

```
172.31.21.202
172.31.24.40
172.31.20.88
172.31.18.103
```

**Playbook:**

The `playbook.yml` file defines the deployment tasks:

1. **Update Packages:** Updates all installed packages on the target instances using `yum`.
2. **Install Apache Server:** Installs the Apache web server using `yum`.
3. **Change Directory:** Navigates to the Apache document root directory (`/var/www/html`).
4. **Download Website Files:** Downloads the Jupiter website files from a GitHub repository URL using `get_url`.
5. **Unzip Downloaded Archive:** Extracts the downloaded ZIP archive using `unarchive`.
6. **Copy Website Files:** Copies the extracted website files to the document root directory.
7. **Clean Up:** Removes the extracted directory and the downloaded ZIP archive.
8. **Start Apache Service:** Starts the Apache service if it's not already running.

**Notes:**

* This playbook assumes the website files are located in the `main` branch of a GitHub repository. 
* The playbook uses `root` user for execution. Ensure proper access control is implemented in production environments.

**Usage:**

To deploy the Jupiter website, run the following command:

```
ansible-playbook playbook.yml
```
