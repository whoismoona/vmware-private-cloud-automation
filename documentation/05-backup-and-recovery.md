# 05 — Backup & Recovery: Because Things Can Go Wrong 💾

## Building a safety net for virtual machines

A working infrastructure is great. Being able to recover it when something goes wrong is even better.

For this part of the project, we integrated **Veeam Backup & Replication** to protect virtual machines and explore backup, backup-copy and replication mechanisms.

## 🏗️ The setup

Veeam was deployed on a dedicated virtual machine hosted on the main ESXi environment.

It was integrated with:

- **VMware vCenter:** To discover and manage ESXi hosts and virtual machines.
- **VMware ESXi:** To access the virtual infrastructure.
- **TrueNAS:** To provide storage for backup files through an NFS repository.

The backup repository was configured on the `Veeam1` dataset.

## 📦 01. Configuring backup jobs

The ESXi hosts and their virtual machines were added to Veeam.

A backup job was configured with the following parameters:

| Parameter | Configuration |
|---|---|
| Backup type | Full + Incremental |
| Frequency | Daily |
| Destination | TrueNAS — `Veeam1` dataset |
| Management | Veeam Backup & Replication |

The infrastructure included critical VMs such as DNS servers and other service machines.

## 🔄 02. Backup Copy Job

A backup is useful, but having another copy in a separate destination adds another layer of protection.

We explored Veeam's Backup Copy Job functionality.

The process involved:

1. Selecting an existing backup as the source.
2. Defining the destination.
3. Configuring the synchronization time window.
4. Launching the copy operation.
5. Checking the execution result.

The report documents a successful completion notification for the Backup Copy Job.

## 🖥️ 03. Virtual Machine Replication

The project also explored VM replication to another ESXi host.

A third ESXi host was added specifically for replication.

Unlike a traditional backup, replication creates a copy of a virtual machine on another host, allowing a recovery option when the original VM becomes unavailable.

The report documents the replication workflow and a failover test involving the secondary DNS server.

## 🧪 04. Validation

The validation work included:

- Checking backup job execution through the Veeam console.
- Verifying backup storage on TrueNAS.
- Checking the Backup Copy Job result.
- Testing VM replication and failover.

These operations helped demonstrate the role of backup and replication in infrastructure continuity.

## 🧠 What I learned

- Integrating Veeam with VMware vCenter and ESXi.
- Configuring a backup repository using NFS storage.
- Understanding full and incremental backups.
- Configuring Backup Copy Jobs.
- Understanding the difference between backup and replication.
- Exploring VM recovery and failover scenarios.

## 📸 Technical evidence

Selected implementation screenshots will be organized in:

`assets/screenshots/veeam/`

---

*Based on Chapter 3.6 — Intégration de Veeam, and the technical validation chapter of the collaborative internship report.*

**A good infrastructure isn't just about keeping things running. It's also about knowing what to do when they don't.**
