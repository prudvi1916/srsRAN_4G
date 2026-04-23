# **4G Private Network Development using USRP N321 and srsRAN 4G**12

## **Project Overview**

This project focuses on the **design and development of a 4G Private Network** using the USRP N321 Software Defined Radio (SDR) hardware and the **srsRAN 4G** open-source software suite. The primary objective is to implement a functional eNodeB (base station), configure the EPC (Evolved Packet Core), and ensure mobile devices can connect securely to this private LTE network for communication and data services.


![arch](https://github.com/user-attachments/assets/7a31fa7f-9fa3-4e75-9b96-53553a8dc00e)

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


![Screenshot 2024-10-18 150037](https://github.com/user-attachments/assets/26731e76-520e-442c-b301-4cbe80005f01)

---

## **Architecture**

### **Structural Architecture**
- The **eNodeB** (eNB) handles radio communication with mobile devices, connected to the EPC for traffic routing and control.
- The EPC contains the **MME**, **SGW**, **HSS**, and **PGW** components to manage core network functions like subscriber authentication, data routing, and IP address allocation.

![layout](https://github.com/user-attachments/assets/844f0970-7f2a-4cbe-a1dc-2c08e9a2769e)


![setup](https://github.com/user-attachments/assets/6554aea1-f09c-45e7-9550-1973daa80d1c)

### **Behavioral Architecture**
- **eNodeB** processes LTE signals using SDR.
- **MME** manages authentication, handovers, and session management.
- **SGW and PGW** handle data routing between the LTE network and external networks (e.g., the internet).

![Flowchart](https://github.com/user-attachments/assets/336c295f-8ecd-4286-887e-71bed922588e)

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

1. Edit the `enb.conf` file for proper eNodeB setup:

    ```bash
    sudo gedit /root/.config/srsran/enb.conf
    ```

2. Ensure lines 20-23 of the `enb.conf` file contain the following configuration:

    ```ini
    mcc = 001               # Mobile Country Code
    mnc = 01                # Mobile Network Code
    tac = 7                 # Tracking Area Code
    enb_id = 19             # eNodeB ID
    ```

3. Save and exit the file.

---

## Setup EPC Components

1. Configure the EPC components by editing the `epc.conf` file:

    ```bash
    sudo gedit /root/.config/srsran/epc.conf
    ```

---

## Configure User Equipment (UE)

1. Add User Equipment (UE) details such as MCC, MNC, and SIM authentication in the `user_db.csv` file:

    ```bash
    sudo gedit /root/.config/srsran/user_db.csv
    ```

2. Example content for `user_db.csv`:

    ```csv
    IMSI,K,OPC,AMF
    001010000000001,465B5CE8B199B49FAA5F0A2EE238A6BC,E8ED289DEBA952E4283B54E88E6183CA,8000
    ```

---

## Start eNodeB and EPC

1. Start the EPC and eNodeB processes with the following commands:

    ```bash
    sudo srsepc
    sudo srsenb
    ```

---

## Testing Use Cases

1. **Mobile Connectivity**: Set up mobile devices with a custom APN to connect to the private 4G network.
2. **Subscriber Management**: Use programmable SIMs for authentication and managing user identities.
3. **Private 4G Network**: Test secure and reliable data communication within the network.

---

## Test Cases

1. **eNodeB Setup Test**: Verify proper configuration and operation of the eNodeB.
2. **APN Configuration Test**: Ensure mobile devices can connect through the configured APN.
3. **SIM Authentication Test**: Confirm that programmable SIMs authenticate users and provide network access.

---

## Future Work

1. **Voice Call Integration**: Implement Asterisk to enable voice call functionality between connected mobile devices.
2. **Transition to 5G**: Explore upgrading the setup to support 5G by integrating 5G NR components in srsRAN.
3. **Vehicle-to-Everything Communication (C-V2X)**: Explore cellular-based communication protocols for vehicle-to-everything integration.

---

## References

- srsRAN 4G on GitHub: [https://github.com/srsran/srsRAN](https://github.com/srsran/srsRAN)
- Ettus Research – USRP N321: [https://www.ettus.com/all-products/usrp-n321/](https://www.ettus.com/all-products/usrp-n321/)
