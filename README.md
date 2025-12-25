# attack_detect_and_seure_the_environment
# ☁️ Cloud-Based SIEM Implementation using Wazuh on Microsoft Azure

## 📌 Project Overview
This project demonstrates the **design, deployment, and validation of a cloud-based Security Information and Event Management (SIEM) system** using **Wazuh** on **Microsoft Azure**.  
The system provides **real-time security monitoring, log analysis, attack detection, and visualization** for multiple virtual machines deployed in a segmented cloud network.

The project simulates real-world attacks such as **SSH brute-force attempts, authentication failures, and file integrity violations**, and validates detection using **Wazuh Dashboard with MITRE ATT&CK mapping**.

---

## 🎯 Objectives
- Deploy a secure cloud infrastructure on Microsoft Azure
- Implement Wazuh SIEM for centralized security monitoring
- Configure Wazuh agents on monitored systems
- Detect and analyze real attack scenarios
- Visualize security alerts using dashboards
- Map detected threats to the MITRE ATT&CK framework

---

## 🏗️ Architecture Overview

### Cloud Infrastructure
- **Cloud Provider:** Microsoft Azure
- **Virtual Network:** Custom VNet with subnet segmentation

### Virtual Machines
| VM Name | Role |
|------|-----|
| VM3-SIEM | Wazuh Manager, Indexer, Dashboard |
| VM2-Web | Apache Web Server + Wazuh Agent |
| VM1-Internal | Internal monitored system + Wazuh Agent |

### Architecture Flow

Attack Activity
↓
Wazuh Agent (VM2-Web / VM1-Internal)
↓
Wazuh Manager (VM3-SIEM)
↓
Wazuh Indexer (OpenSearch)
↓
Wazuh Dashboard (Alerts & Visualization)


---

## 🧰 Technologies Used
- Microsoft Azure (IaaS)
- Ubuntu Server 22.04 LTS
- Wazuh SIEM (Manager, Indexer, Dashboard)
- Wazuh Agent
- OpenSearch
- Apache Web Server
- SSH
- MITRE ATT&CK Framework

---

## ⚙️ Implementation Steps

### 1️⃣ Azure Setup
- Created a custom Virtual Network (VNet)
- Configured DMZ and Internal subnets
- Deployed three Ubuntu virtual machines
- Configured Network Security Groups (NSG) to allow:
  - SSH (22)
  - HTTPS (443)
  - Wazuh Dashboard (5601)

---

### 2️⃣ Wazuh SIEM Installation (VM3-SIEM)
- Installed Wazuh using the official installation script
- Services deployed:
  - `wazuh-manager`
  - `wazuh-indexer`
  - `wazuh-dashboard`
- Verified services using `systemctl`

---

### 3️⃣ Agent Installation (VM2-Web & VM1-Internal)
- Installed Wazuh Agent on monitored systems
- Registered agents with SIEM server
- Verified agent connectivity and active status

---

## 🔴 Attack Simulation

### SSH Brute-Force Attack
Simulated multiple failed SSH login attempts:
```bash
ssh fakeuser@localhost
