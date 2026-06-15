# Ansible Task Solutions

This repository contains solutions for a series of Ansible automation tasks covering playbooks, roles, templates, custom facts, repositories, and load balancing.

## Task 1 - Regular Tasks

### Goal
Create an hourly cron job.

### Solution
A playbook creates a cron job for the root user that appends the current date and time to `/var/log/time.log` every hour.

### Skills
- Ansible Playbooks
- Cron Module

---

## Task 2 - Repository Management

### Goal
Configure a MySQL YUM repository.

### Solution
A playbook creates the `mysql80-community` repository with GPG verification enabled.

### Skills
- Ansible Playbooks
- yum_repository Module

---

## Task 3 - Apache Role

### Goal
Create a reusable Apache role.

### Solution
The role installs Apache, PHP, and mod_ssl, configures the firewall, deploys a template-based web page, and restarts Apache when the page changes.

### Skills
- Ansible Roles
- Handlers
- Templates
- Firewalld

---

## Task 4 - HAProxy Load Balancer

### Goal
Configure HAProxy using an Ansible Galaxy role.

### Role Installation

```bash
sudo ansible-galaxy role install geerlingguy.haproxy -p /home/automation/plays/roles
```

### Solution
The playbook installs and configures HAProxy to distribute HTTP requests between web servers using the round-robin load-balancing method.

### Skills
- Ansible Galaxy
- HAProxy
- Load Balancing

---

## Task 5 - Custom Facts

### Goal
Create a custom Ansible fact.

### Solution
The playbook creates a local fact that stores the server role as `mysql` and makes it available through `ansible_local`.

### Skills
- Ansible Facts
- Setup Module

---

## Task 6 - Templates

### Goal
Generate configuration files using Jinja2 templates.

### Solution
The playbook creates `/etc/server_list.txt` dynamically from inventory data and applies the required ownership, permissions, and SELinux context.

### Skills
- Jinja2 Templates
- File Management
- SELinux

---

## Ansible Vault

Sensitive data such as sudo/become passwords are stored using Ansible Vault.

Encrypted variables are located under:

```text
automation/plays/group_vars/
```

Playbooks can be executed with:

```bash
ansible-playbook <playbook>.yml --ask-vault-pass
```

---

## Technologies Used

- Ansible
- Ansible Galaxy
- Jinja2
- Apache HTTP Server
- HAProxy
- Firewalld
- SELinux
- Linux
