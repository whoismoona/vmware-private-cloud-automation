# ☁️ Building My Own Little Cloud

### VMware | Virtualization | Automation | Infrastructure Monitoring

> Some projects teach you technologies. Others make you fall in love with the field.

This was one of those projects. 💙

During my summer internship at **Maroc DataCenter (MDC)**, I had the opportunity to explore the world of private cloud infrastructure and discover how all the different pieces of an IT infrastructure work together.

From VMware virtualization to automated provisioning, shared storage, monitoring and security, this experience was packed with technical discoveries, problem-solving and teamwork.

But beyond the technologies, it was also about the people I met, the knowledge they shared and the conversations that made me even more curious about this field.

And that's exactly why I wanted to document this project here!

---

## 🏗️ So, what did we build?

A private cloud infrastructure designed to centralize resource management, automate virtual machine provisioning and monitor the environment.

The architecture brought together:

| Component | Technology | Purpose |
|---|---|---|
| Virtualization | VMware ESXi | Host virtual machines |
| Centralized management | vCenter | Manage ESXi hosts and resources |
| Shared storage | TrueNAS | Centralize storage |
| Automation | Ansible | Automate provisioning and configuration |
| Backup & Recovery | Veeam | Protect and replicate VMs |
| Infrastructure monitoring | PRTG | Monitor infrastructure health |
| Security monitoring | Wazuh | Collect logs and monitor security events |

## 🔍 Exploring the infrastructure

### 01. Virtualization & Management
Two ESXi hosts managed through a centralized vCenter environment, with cluster configuration and vMotion.

### 02. Shared Storage
TrueNAS integration to provide shared storage for the virtual infrastructure.

### 03. Automation
Ansible playbooks to automate virtual machine provisioning, network configuration and application deployment.

### 04. Backup & Recovery
Veeam integration for VM backups, backup copy jobs and replication.

### 05. Monitoring & Security
PRTG for infrastructure monitoring and Wazuh for centralized security monitoring and alert visibility.

---

## 🧠 What I learned

- Understanding how enterprise virtualization environments are structured.
- Working with VMware ESXi and vCenter.
- Exploring Infrastructure as Code through Ansible.
- Understanding shared storage and network services.
- Discovering backup, replication and recovery mechanisms.
- Exploring infrastructure monitoring and security event collection.

## 🛠️ Technologies

`VMware ESXi` `vCenter` `TrueNAS` `Ansible` `Veeam` `PRTG` `Wazuh` `Linux` `DNS` `NTP`

---

## 📸 Behind the scenes

Technical diagrams, selected screenshots and project documentation will be added here.

---

### A little note 💙

This repository is a technical showcase based on a collaborative internship project. It documents the architecture, technologies, concepts and lessons from the experience.

Some configurations and examples may be reconstructed for educational purposes and will be identified accordingly.

*Still curious. Still learning. Still building.*

**— Moona** 👾
