Ansible Nginx EC2 Setup

Project Overview

This project demonstrates the use of Ansible to automate the configuration of an Nginx web server on an AWS EC2 Ubuntu instance.

Technologies Used

* AWS EC2
* Ubuntu Server 24.04 LTS
* Ansible
* Nginx
* YAML
* SSH

AWS Infrastructure

* Instance Name: Ansible-Nginx-server
* Instance Type: t3.micro
* Region: eu-north-1 (Europe Stockholm)
* Operating System: Ubuntu Server 24.04 LTS
* Web Server: Nginx
* HTTP Port: 80
* SSH Port: 22

Project Files

* inventory.ini – Defines the EC2 target server and SSH connection details.
* nginx-playbook.yml – Ansible playbook for installing and configuring Nginx.
* README.md – Project documentation.

Configuration and Deployment

1. Connect to the EC2 instance

Ansible connects to the Ubuntu EC2 instance using SSH key-based authentication.

2. Test Ansible connectivity

ansible -i inventory.ini webservers -m ping

3. Run the Ansible playbook

ansible-playbook -i inventory.ini nginx-playbook.yml

4. Verify Nginx

ansible -i inventory.ini webservers -m command -a "systemctl is-active nginx"

5. Verify HTTP response

ansible -i inventory.ini webservers -m command -a "curl -s -o /dev/null -w '%{http_code}\n' http://localhost"

Expected HTTP response: 200

Results

* Ansible successfully connected to the EC2 instance.
* Nginx was installed and configured to start automatically.
* Nginx service was verified as active.
* HTTP returned status code 200.
* The Nginx welcome page was accessible through the EC2 public IP.

Security Notes

* The SSH private key is stored locally and must never be uploaded to GitHub.
* SSH access should be restricted to trusted IP addresses.
* HTTP port 80 is publicly accessible for web testing.

Conclusion

This project demonstrates basic configuration management and web server automation using Ansible on AWS EC2.
