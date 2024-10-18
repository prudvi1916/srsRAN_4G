# **4G Private Network Development using USRP N321 and srsRAN 4G**

## **Project Overview**

This project focuses on the **design and development of a 4G Private Network** using the USRP N321 Software Defined Radio (SDR) hardware and the **srsRAN 4G** open-source software suite. The primary objective is to implement a functional eNodeB (base station), configure the EPC (Evolved Packet Core), and ensure mobile devices can connect securely to this private LTE network for communication and data services.

## **Table of Contents**
- [Objective and Goals](#objective-and-goals)
- [Project Team](#project-team)
- [Technologies Used](#technologies-used)
- [Architecture](#architecture)
- [Installation and Setup](#installation-and-setup)
- [Testing](#testing)
- [Future Work](#future-work)
- [References](#references)

---

## **Objective and Goals**

The main objectives are:
- To **design and implement a private 4G LTE network** using the USRP N321 SDR.
- To optimize and configure the **eNodeB** and **EPC** components for robust performance.
- To test and verify the network performance through **coverage** and **performance** tests with mobile devices.
  
### **Goals**:
- Setup eNodeB and EPC components (MME, HSS, SGW, PGW).
- Configure **mobile devices** and **programmable SIM** for network access.
- Perform **Uplink/Downlink testing** and validate **network performance**.

---

## **Project Team**
- **P. Prudvi Reddy** (BU21EECE0100361)
- **MC Mokshith** (BU21EECE0100391)
- **B. Gopal** (BU21EECE0100377)
  
**Mentor:**  
Dr. T Nagarjuna, Assistant Professor

---

## **Technologies Used**
- **Software:** srsRAN 4G (for LTE Network setup and management).
- **Hardware:** USRP N321 (Software Defined Radio).
- **Operating System:** Linux (Ubuntu for srsRAN setup).
- **Programming Languages:** CMake, Bash for installation and configuration scripts.
- **Tools/Utilities:**  
  - `srsran_4g_install_configs.sh` (to install LTE configuration files)
  - `gedit` for configuration file editing.

---

## **Architecture**

### **Structural Architecture**
- The **eNodeB** (eNB) handles radio communication with mobile devices, connected to the EPC for traffic routing and control.
- The EPC contains the **MME**, **SGW**, **HSS**, and **PGW** components to manage core network functions like subscriber authentication, data routing, and IP address allocation.

### **Behavioral Architecture**
- **eNodeB** processes LTE signals using SDR.
- **MME** manages authentication, handovers, and session management.
- **SGW and PGW** handle data routing between the LTE network and external networks (e.g., the internet).

---

## **Installation and Setup**

1. **Install srsRAN and dependencies:**
   ```bash
   git clone https://github.com/srsran/srsran_4g
   cd srsRAN_4G/build
   make clean
   cmake ..
   make
   sudo srsran_4g_install_configs.sh <user/service>
## Configure eNodeB

Edit the `enb.conf` file for proper eNodeB setup:

```bash
sudo gedit /root/.config/srsran/enb.conf