# 02 — Virtualization: The Foundation 🖥️

## One physical server, multiple virtual environments.

This is where the infrastructure started taking shape.

The virtualization layer was built around VMware ESXi and vCenter, allowing us to deploy multiple virtual hosts and manage the environment centrally.

Instead of working with several physical servers, the project used a nested virtualization architecture hosted on a single physical HPE server.

## ⚙️ The environment

The physical server used for the project had the following specifications:

| Component | Specification |
|---|---|
| Processor | Intel Xeon E5-2660 v4 @ 2.00 GHz |
| RAM | 223.75 GB |
| Local storage | 2.69 TB |
| Physical hypervisor | VMware ESXi |

The initial hardware preparation, including RAID, BIOS and boot configuration, was performed using Hewlett Packard Intelligent Provisioning.

## 🧩 Deploying the ESXi hosts

Two virtual machines were created on the main physical ESXi host to run nested VMware ESXi:

- `esxi-01`
- `esxi-02`

Each host received allocated CPU, RAM and disk resources, followed by ESXi installation and static network configuration.

**Software versions documented:**
- VMware ESXi 6.7
- VMware vCenter Server 7.0

## 🎛️ Centralized management with vCenter

Once the ESXi hosts and DNS services were configured, VMware vCenter Server Appliance (VCSA) was deployed on the main ESXi host.

The environment was then organized through vCenter:

1. Created a datacenter named `MDC-DataCenter`.
2. Created a cluster named `MDC-Cluster`.
3. Added `esxi01` and `esxi02` to the cluster.
4. Added a separate ESXi replication host to the infrastructure.

This provided a centralized point for managing hosts, virtual machines and infrastructure resources.

## 🔄 Cluster features and vMotion

The cluster configuration included VMware vSphere features such as:

- **vSphere HA:** High availability and automatic VM restart following host failure.
- **vSphere DRS:** Distribution and balancing of workloads across hosts.
- **vMotion:** Live migration of virtual machines between ESXi hosts.

One particularly interesting validation step was migrating a virtual machine from `esxi02` to `esxi01` using vMotion.

The migration was completed successfully.

## 🧠 What I learned

- How nested virtualization works.
- How to deploy and configure VMware ESXi hosts.
- How vCenter centralizes infrastructure management.
- How datacenters and clusters organize virtual resources.
- How vMotion enables live virtual machine migration.
- How cluster features contribute to infrastructure availability and resource management.

## 📸 Technical evidence

Selected screenshots from the original project report will be added here.

---

*This section documents the virtualization implementation described in Chapter 3 of the internship report.*
