# 06 — Monitoring & Security: Keeping an Eye on Everything 👀

## An infrastructure is only as good as its visibility.

Building an infrastructure is one thing. Knowing what's happening inside it is another.

For this part of the project, we integrated two complementary solutions:

- **PRTG Network Monitor** for infrastructure and performance monitoring.
- **Wazuh** for centralized security monitoring and threat visibility.

They served different purposes, but together they helped provide a clearer picture of the environment.

---

# 📡 Part 1 — PRTG Network Monitor

## Watching infrastructure performance

PRTG was deployed on a virtual machine running Windows Server 2019.

The project used the free edition, limited to 100 sensors, which was sufficient for the target infrastructure.

### What was monitored?

Different sensor types were configured to monitor infrastructure components:

| Sensor category | Examples |
|---|---|
| Network | Ping, HTTP/HTTPS, TCP ports |
| VMware | Host Hardware Status, Performance Counter, vCenter Status |
| System | CPU, memory and storage via SNMP |
| Services | DNS, NFS and Windows services |

### Alerts and notifications

PRTG used configurable thresholds to identify abnormal conditions.

The monitored states included:

- 🟢 **Up:** The monitored component is operational.
- 🟠 **Warning:** A configured warning condition has been reached.
- 🔴 **Down:** The monitored component is unavailable.

Notification triggers could also be configured to react to performance thresholds, with actions such as email, SMS or script execution.

### Real-time monitoring

The PRTG dashboard provided:

- CPU and memory usage gauges.
- Sensor and active alarm counters.
- Performance graphs over 24-hour and 7-day periods.
- Device status and availability information.
- Detailed performance reports and SLA indicators.

The goal was to make infrastructure health easier to observe and potential problems easier to identify.

---

# 🛡️ Part 2 — Wazuh

## From infrastructure monitoring to security monitoring

This is where the project becomes particularly interesting from a cybersecurity perspective.

We deployed **Wazuh All-in-One** on a dedicated Ubuntu Server 22.04 virtual machine.

The installation brought together three main components:

| Component | Role |
|---|---|
| Wazuh Manager | Collects, analyzes and correlates logs |
| Wazuh Indexer | Stores and indexes security events |
| Wazuh Dashboard | Provides a graphical interface for monitoring and alerts |

### Connecting the agents

The Wazuh agents were installed on several critical infrastructure machines:

- Primary DNS server.
- Secondary DNS server.
- Veeam backup server.
- PRTG monitoring server.
- Ansible server.

This allowed events from different systems to be collected centrally.

### What did we monitor?

The report documents several monitoring capabilities:

- File Integrity Monitoring (FIM).
- Network connections and open ports.
- Critical services such as DNS, backup and PRTG.
- Suspicious authentication attempts.
- System errors and security events.

### Windows and Linux agent deployment

Agent installation was documented for both operating systems.

**Windows Server:**
- Agent installation using an MSI package.
- Registration with the Wazuh server.
- Connection verification through the dashboard.

**Ubuntu Linux:**
- Installation using `dpkg`.
- Agent configuration and registration.
- Connection verification.

### Security alerts

Collected events were analyzed and displayed in the Wazuh Dashboard.

The report distinguishes between lower or medium-severity events, such as normal system changes and service starts, and critical events, such as authentication failures, suspicious modifications and network attacks.

The centralized dashboard made it possible to observe security-related activity across the monitored infrastructure.

---

## 🔗 Two tools, two perspectives

| PRTG | Wazuh |
|---|---|
| Infrastructure health | Security events |
| Performance metrics | Log analysis |
| Availability | File integrity |
| Network and service monitoring | Authentication monitoring |
| Performance alerts | Security alerts |

Together, they provided complementary visibility into infrastructure performance and security.

---

## 🧠 What I learned

- Understanding infrastructure monitoring with PRTG.
- Configuring sensors and notification triggers.
- Monitoring CPU, memory, storage and network services.
- Deploying Wazuh All-in-One.
- Understanding the Manager, Indexer and Dashboard architecture.
- Deploying and connecting agents on Windows and Linux.
- Exploring File Integrity Monitoring and security alerts.
- Understanding the importance of centralized log collection.

## 📸 Technical evidence

Selected screenshots from the original report will be organized in:

- `assets/screenshots/prtg/`
- `assets/screenshots/wazuh/`

---

*Based on Chapters 3.7 and 3.8 — PRTG Deployment and Wazuh Monitoring, from the collaborative internship report.*

**Monitoring tells us when something is wrong. Security monitoring helps us understand what might be happening.** 🔐
