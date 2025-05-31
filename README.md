# 🚀 Ansible Automation

![Ansible](https://img.shields.io/badge/automation-ansible-%23174F85)  
Automate your infrastructure and deployments with Ansible playbooks.

## 📖 What is Ansible?

**Ansible** is an open-source automation tool that allows you to configure servers, deploy applications, and manage IT environments using simple, human-readable YAML files called **playbooks**. It’s agentless and connects via SSH, making it ideal for managing Linux and cloud infrastructure.

---


![ansible_example](https://github.com/user-attachments/assets/ce25cb4b-e84b-4b88-9f6e-006e7c9c72e6)


# Key features:
Agentless and SSH-based <br>
Uses YAML for configuration (playbooks) <br>
Automates provisioning, configuration, deployment, and orchestration <br>
Supports Linux, macOS, Windows, cloud (AWS, Azure, GCP), Docker, Kubernetes <br>

# Example:
Install and configure Nginx, Docker, databases <br>
Deploy apps (Node.js, Django, PHP, etc.) <br>
Manage users, firewalls, cron jobs <br>
Provision servers on AWS/GCP/Azure <br>

# 🛠 Requirements
Python 3 <br>
Ansible control node <br>
SSH access to remote hosts <br>
Sudo privileges on remote hosts <br>

## 📁 Project Structure
├── inventory.ini # Inventory of remote hosts <br>
├── nginx.yml # Example playbook to install Nginx <br>
└── README.md # This file <br>
---
## 📌	 SSH KEYs

Step 1: Generate SSH Key on Ansible node
```
ssh-keygen -t rsa -b 4096 
Press Enter to accept defaults (save in ~/.ssh/id_rsa)
```

Step 2: Copy Public Key to Remote Host 
```
ssh-copy-id MBaranekTech@192.168.1.10
ssh-copy-id MBaranekTech@192.168.1.11
```
Step 3: Set Correct Permissions
```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```
Step 4: Test Passwordless SSH
```
ssh MBaranekTech@192.168.1.10
ssh MBaranekTech@192.168.1.11
```
---
## 📚	 Test host connectivity
```
ansible all -i inventory.ini -m ping
```
## 🚀 Example Playbook: Install Nginx

```yaml
- name: Install and start Nginx
  hosts: client
  become: true
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start and enable Nginx
      service:
        name: nginx
        state: started
        enabled: true
```
---

## 📡 Inventory Example (inventory.ini)
```
[client]
192.168.1.10 ansible_user=MBaranekTech ansible_ssh_private_key_file=~/.ssh/id_rsa
192.168.1.11 ansible_user=MBaranekTech ansible_ssh_private_key_file=~/.ssh/id_rsa
```
## 🧪 How to Run a Playbook
```
ansible-playbook -i inventory.ini nginx-playbook.yml --ask-become-pass
```

