# 07 — Validation & Troubleshooting: Making Sure It Actually Works 🧪

## Building it is one thing. Testing it is another.

After integrating the different infrastructure components, we needed to verify that everything communicated correctly and that the services performed as expected.

This chapter documents the functional tests, validation results and technical problems described in the project report.

---

## 🧪 01. Functional validation

### Network connectivity

Ping tests were performed between the deployed virtual machines to verify network connectivity, VLAN configuration and routing.

**Result:** Connectivity between the VMs was validated.

### Infrastructure monitoring — PRTG

PRTG was used to monitor ESXi hosts, virtual machines and TrueNAS storage.

The validation included monitoring:

- CPU utilization.
- RAM usage.
- Network traffic.
- Infrastructure availability.
- Configured alerts.

**Result:** Infrastructure monitoring was operational.

### Automation — Ansible

Ansible was used to create multiple virtual machines automatically through vCenter.

**Result:** Automated VM provisioning was successfully demonstrated.

### Backup and replication — Veeam

The validation included:

- Backups of critical VMs.
- Backup storage on a TrueNAS datastore.
- Verification of backup job results.
- Daily scheduling and failure notifications.
- VM replication job execution.

**Result:** The report documents successful backup and replication job executions.

### Security monitoring — Wazuh

Wazuh agents were installed on several infrastructure VMs:

- DNS1
- DNS2
- Ansible
- PRTG
- Veeam

Installation was tested on both Windows and Linux.

**Result:** The agents were successfully connected and visible in the Wazuh Dashboard.

---

## 🔧 02. Problems encountered & how they were resolved

This is probably one of the most interesting parts of the project: not everything worked perfectly on the first attempt.

### Problem 1 — Connectivity between nested ESXi hosts

**The issue:** Connectivity problems occurred between nested ESXi hosts.

**The resolution:** VLAN and vSwitch configurations were adjusted to establish the required network connectivity.

### Problem 2 — TrueNAS NFS access

**The issue:** Access to the shared NFS storage required additional configuration.

**The resolution:** NFS export permissions and ESXi network configuration were adjusted.

### Problem 3 — Wazuh agent installation

**The issue:** Agent installation required different procedures depending on the operating system.

**The resolution:**
- Windows: Run the installer with administrator privileges.
- Linux: Use `dpkg` and a customized Bash script.

### Problem 4 — Ansible automation errors

**The issue:** Existing virtual machines caused automation errors, and playbooks needed to accommodate multiple ESXi hosts.

**The resolution:** The automation scripts were adapted to handle existing VMs and multiple hosts.

---

## 📊 03. Final validation summary

The report's validation chapter concludes that the following components were operational:

| Component | Validation |
|---|---|
| Network connectivity | Successful |
| PRTG monitoring | Operational |
| Ansible provisioning | Successful |
| Veeam backup | Successful |
| Veeam replication job | Successful |
| Wazuh agents | Connected and active |

These results demonstrate the integration of virtualization, automation, storage, backup, monitoring and security within one infrastructure.

---

## 🚀 04. What could be improved?

The report also identifies several possible future improvements.

These were proposed as development opportunities, not completed implementations.

| Area | Proposed improvement |
|---|---|
| Backup & Recovery | Advanced restoration testing and disaster recovery planning |
| High Availability | Further implementation of vSphere HA and vMotion |
| Monitoring | Centralized dashboards using Grafana or Kibana |
| Cloud | Extend monitoring to AWS, Azure and GCP |
| Automation | Explore Terraform and AWX |
| Cybersecurity | MFA, vulnerability assessment and CIS hardening |
| Log Management | Extend centralized log analysis |
| Scalability | Add physical hosts for additional capacity and redundancy |

---

## 💡 Final thoughts

One of the biggest lessons from this project was that infrastructure engineering isn't just about installing technologies and making them communicate.

It's about understanding how the components depend on one another, identifying what goes wrong and finding ways to make the entire environment more reliable.

From network configuration issues to automation errors, every challenge was another opportunity to understand the infrastructure a little better.

And that's what made this experience so valuable.

---

*Based on Chapter 4 — Technical Validation of the Infrastructure, from the collaborative internship report.*

**Build it. Test it. Break it. Understand it. Improve it.** 🔐
