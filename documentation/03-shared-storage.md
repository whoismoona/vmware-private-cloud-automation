# 03 — Shared Storage: Where Everything Lives 💾

## Giving the infrastructure a place to store its data

A virtual infrastructure needs more than computing resources. It also needs reliable, organized storage that can be accessed by the different components.

For this part of the project, we integrated **TrueNAS SCALE** as a virtualized storage solution within our nested environment.

The objective was to centralize storage and make it accessible to the VMware ESXi hosts.

## ⚙️ Installing TrueNAS

TrueNAS was deployed as a virtual machine using its installation ISO.

During the initial configuration, virtual disks were assigned to the VM:

- One disk dedicated to the TrueNAS operating system.
- Additional virtual disks dedicated to data storage.

This separation allowed us to keep the system and data storage organized independently.

## 🗄️ Storage pools and datasets

One of the interesting parts was organizing storage according to its intended use.

Three storage pools were configured:

| Pool | Purpose |
|---|---|
| `Storage` | Main pool for general data and filesystems |
| `TN-Data` | Secondary pool for critical data and specialized datasets |
| `Veeam` | Dedicated pool for backup storage |

A dataset named `TN-Data/Veeam1` was also created specifically for Veeam backup data.

This organization made storage management clearer and helped separate different data requirements.

## 🌐 Network configuration

TrueNAS was configured with a dedicated network interface to communicate with the other infrastructure components.

Network connectivity was important because the storage system needed to communicate with ESXi and services such as Ansible and Veeam.

## 🔗 Sharing storage through NFS

For the VMware environment, an NFS share was configured on TrueNAS.

The ESXi nested hosts mounted this shared storage as a datastore, allowing them to access centralized storage for virtual machine files.

The project also discusses other protocols supported by TrueNAS, including SMB and iSCSI. The documented implementation specifically describes the NFS share used by the ESXi hosts.

## 🔐 Users and permissions

User and group management was another important part of the configuration.

Specific accounts were created for services accessing the storage, including Veeam and Ansible.

The objective was to organize access and apply appropriate permissions rather than relying on unrestricted access.

## 🧠 What I learned

- Deploying TrueNAS in a virtualized environment.
- Understanding storage pools and datasets.
- Separating system disks from data disks.
- Configuring network interfaces for storage communication.
- Understanding how NFS provides shared storage to ESXi.
- Managing users, groups and storage permissions.

## 📸 Technical evidence

Selected screenshots from the original internship report will be added here.

---

*Based on Chapter 3.4 — Shared Storage with TrueNAS, from the collaborative internship project.*
