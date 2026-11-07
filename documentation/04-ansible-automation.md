# 04 — Ansible: Let Automation Do the Repetitive Work ⚙️

## Less clicking. More consistency.

One of my favourite parts of this project was exploring infrastructure automation.

Managing virtual machines, configuring networks and deploying applications can involve a lot of repetitive operations. Instead of performing every task manually, we used **Ansible** to automate parts of the VMware environment.

The idea was simple: describe the desired configuration in YAML, execute a playbook and let Ansible handle the tasks.

## 🧠 How did it work?

Ansible was installed on a dedicated Ubuntu virtual machine acting as the control node.

From this machine, Ansible communicated with:

- VMware vCenter through the `community.vmware` modules and its API.
- Linux virtual machines through SSH.

The project used a push-based automation approach: the control node sent instructions to the target systems.

## 📁 How the automation was organized

The report documents several groups of playbooks:

| Directory | Purpose |
|---|---|
| `create_vms/` | Automated virtual machine creation |
| `create_application/` | Application deployment inside VMs |
| `create_vmkernels/` | VMkernel interface configuration |
| `vmware-ansible/` | General VMware configuration |

Some of the documented playbooks include:

- `create_multi_vm.yml`
- `nginx.yml`
- `playbook_configure_vmkernel.yml`
- `vswitch_cluster.yml`
- `port_groups.yml`
- `expand_disk.yml`

The playbooks used YAML inventory and variable files to define target systems and configuration parameters.

## 🚀 What did we automate?

### 01. Virtual machine provisioning

A dedicated playbook was used to create multiple virtual machines through vCenter.

The VM parameters were defined in YAML files, and the execution results were visible in the vCenter interface.

### 02. Application deployment with NGINX

Once an Ubuntu VM was created, Ansible established an SSH connection and deployed an NGINX web server.

The playbook automated installation and configuration, followed by a service-status check.

The report also documents successful access to the deployed web server through a browser.

### 03. VMware network configuration

Automation was also used for infrastructure networking tasks:

- Creating virtual switches (vSwitches).
- Adding port groups.
- Configuring VMkernel interfaces.

These interfaces support infrastructure traffic such as vMotion and iSCSI.

### 04. Virtual disk expansion

The project also included a playbook for expanding virtual machine disks, with the result checked through vCenter.

## 🧪 Why was this useful?

Automation brought several advantages to the project:

- **Time saving:** Repetitive deployment tasks could be executed more quickly.
- **Consistency:** Standardized playbooks reduced manual configuration differences.
- **Flexibility:** Parameters could be adjusted through YAML variables.
- **Reusability:** Playbooks could be reused across different hosts and environments.

## 🧠 What I learned

- Working with Ansible inventories and YAML playbooks.
- Understanding the control-node and managed-node architecture.
- Using VMware automation modules.
- Automating virtual machine provisioning.
- Deploying applications through SSH.
- Managing vSwitches, port groups and VMkernel interfaces.
- Understanding Infrastructure as Code in a VMware environment.

## 📸 Technical evidence

Screenshots and selected implementation evidence from the original report will be organized in:

`assets/screenshots/ansible/`

---

*Based on Chapter 3.5 — Automatisation via Ansible, from the collaborative internship project.*

**Note:** The original Ansible scripts are not included in this repository. The file names and workflows documented here come from the internship report.
