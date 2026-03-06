# 🌐 Azure High-Availability Web Infrastructure

### Implementing Load Balanced Architecture with Windows Server 2025

<p align="center">
  <img src="https://img.shields.io/badge/Cloud-Microsoft%20Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" />
  <img src="https://img.shields.io/badge/OS-Windows%20Server%202025-0078D6?style=for-the-badge&logo=windows&logoColor=white" />
  <img src="https://img.shields.io/badge/Automation-PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white" />
  <img src="https://img.shields.io/badge/Project-Completed-brightgreen?style=for-the-badge" />
</p>

---

# 📚 Table of Contents

- [📌 Project Overview](#-project-overview)
- [🏗️ Architecture](#️-architecture)
- [☁️ Infrastructure Components](#️-infrastructure-components)
- [🔁 High Availability Strategy](#-high-availability-strategy)
- [⚙️ Load Balancer Configuration](#️-load-balancer-configuration)
- [💻 Web Server Deployment](#-web-server-deployment)
- [🧪 Testing Load Balancing](#-testing-load-balancing)
- [📷 Project Screenshots](#-project-screenshots)
- [📊 Infrastructure Summary](#-infrastructure-summary)
- [🚀 Future Improvements](#-future-improvements)
- [🎓 Learning Outcomes](#-learning-outcomes)
- [🧑‍💻 Author](#-author)
- [⭐ Support](#-support)

---

# 📌 Project Overview

This project demonstrates how to build a **Highly Available Web Infrastructure in Microsoft Azure** using:

- **Azure Standard Load Balancer**
- **Windows Server 2025**
- **Availability Sets**
- **PowerShell Automation**

The architecture eliminates **Single Points of Failure (SPOF)** by distributing traffic across multiple backend servers.

### 🎯 Project Objectives

- Deploy multiple IIS Web Servers  
- Configure Azure Load Balancer  
- Implement High Availability using Fault Domains  
- Automate deployment using PowerShell  
- Verify traffic distribution and failover  

---

# 🏗️ Architecture

The following architecture shows how user traffic flows through the Azure infrastructure.

![Architecture Diagram](./Gemini_Generated_Image_d9q905d9q905d9q9.jpg)

---

# ☁️ Infrastructure Components

| Resource | Description |
|--------|-------------|
| **Virtual Network** | Private network for Azure resources |
| **Subnet** | Network segmentation for isolation |
| **Availability Set** | Provides VM redundancy |
| **Load Balancer** | Distributes traffic across servers |
| **Public IP** | Entry point for external users |
| **Network Security Group** | Controls inbound/outbound traffic rules |
| **Windows Server VMs** | Hosts the IIS Web Service |

---

# 🔁 High Availability Strategy

Both web servers are deployed in an **Azure Availability Set**. This ensures that:

- VMs are placed in **separate fault domains** (protection against hardware failure)
- Updates occur in **different update domains** (protection during maintenance)

### Distribution Details

| Configuration | Value |
|-------------|------|
| Fault Domains | 2 |
| Update Domains | 5 |

![Availability Set Configuration](./set%20availability.png)

---

# ⚙️ Load Balancer Configuration

The **Azure Standard Load Balancer** acts as the traffic orchestrator.

| Setting | Value |
|-------|------|
| **Frontend IP** | LB-Public-IP |
| **Backend Pool** | Web-Servers-Pool (VM Interfaces) |
| **Health Probe** | TCP Port 80 (Health Monitoring) |
| **Load Rule** | Port 80 → Port 80 (HTTP) |
| **Session Persistence** | Disabled (Round-Robin) |

---

# 💻 Web Server Deployment

Each VM hosts an **IIS Web Server** installed using **PowerShell**.

### 🖥️ Web Server 01 Setup

```powershell
Install-WindowsFeature -name Web-Server -IncludeManagementTools

Set-Content -Path "C:\inetpub\wwwroot\iisstart.htm" -Value "<h1>Welcome to Web Server 01</h1>"
```

### 🖥️ Web Server 02 Setup

```powershell
Install-WindowsFeature -name Web-Server -IncludeManagementTools

Set-Content -Path "C:\inetpub\wwwroot\iisstart.htm" -Value "<h1>Welcome to Web Server 02</h1>"
```

---

# 🧪 Testing Load Balancing

After deployment, access the Load Balancer Public IP.

Example:

```
http://20.105.34.114
```

### Expected Result

Refreshing the page will alternate between the servers, confirming successful traffic distribution.

---

# 📷 Project Screenshots

- Backend Pool Mapping  
- Load Balancer Rule Configuration  
- Remote PowerShell Execution (Run Command)

---

# 📊 Infrastructure Summary

| Resource | Quantity |
|--------|--------|
| Virtual Machines | 2 |
| Load Balancer | 1 |
| Public IP | 1 |
| Virtual Network | 1 |
| Availability Set | 1 |

---

# 🚀 Future Improvements

- [ ] Implement Azure Application Gateway for L7 load balancing  
- [ ] Enable HTTPS (SSL/TLS) for secure communication  
- [ ] Integrate Azure Key Vault for certificate management  
- [ ] Implement Virtual Machine Scale Sets (VMSS) for auto-scaling  
- [ ] Setup Azure Monitor & Log Analytics for real-time insights  

---

# 🎓 Learning Outcomes

- Hands-on experience with Azure Cloud Infrastructure deployment  
- Deep understanding of Load Balancing (L4) concepts  
- Implementing High Availability (HA) design patterns  
- Infrastructure management via PowerShell Automation  
- Configuring Fault-Tolerant architectures in the cloud  

---

# 🧑‍💻 Author

**Amal — CyberLab**

Cloud Engineering | Cybersecurity | Infrastructure Labs

---

# ⭐ Support

If you found this project helpful:

⭐ Star the repository  
🍴 Fork the project  
📢 Share with others
