# OPNsense-Firewall-Lab

OPNsense Firewall Lab — VirtualBox Setup Inspired by LS111 Cyber Security Education (Youtube)

A practical firewall lab environment built by following NetworkChuck's OPNsense tutorial. This project simulates a basic LAN/WAN setup using OPNsense 25.1 running on VirtualBox with host-only network access for secure web GUI management.


## 🛠️ Lab Setup and Configuration Steps

### 1. Download and Prepare VirtualBox

- Install Oracle VirtualBox from [https://www.virtualbox.org/](https://www.virtualbox.org/)
- Create a new VM for OPNsense:
  - Type: BSD
  - Version: FreeBSD (64-bit)
  - RAM: Minimum 2 GB recommended
  - HDD: At least 10 GB dynamically allocated

---

### 2. Configure Network Adapters

- Adapter 1 (WAN): Set to **NAT** (provides internet access)
- Adapter 2 (LAN): Set to **Host-only Adapter** (to communicate with host PC)
- Ensure the Host-only network adapter is enabled and configured in VirtualBox settings

---

### 3. Install OPNsense

- Download OPNsense ISO from [https://opnsense.org/download/](https://opnsense.org/download/)
- Mount the ISO to the VM's optical drive and boot
- Follow the installation prompts to install OPNsense on the VM’s virtual disk
- After installation, reboot the VM

---

### 4. Assign Interfaces

- Upon boot, the console will ask to assign interfaces:
  - `em0` → WAN
  - `em1` → LAN
- Confirm and proceed

---

### 5. Configure LAN IP Address

- Set LAN interface IP to `10.200.200.254/24`
- This IP will be used to access the OPNsense web GUI from your host PC

---

### 6. Set Static IP on Host PC

- Configure your host computer’s Host-only network adapter with a static IP in the same subnet, e.g.:
  - IP: `10.200.200.10`
  - Subnet mask: `255.255.255.0`
  - Gateway: Leave blank or set to `10.200.200.254`

---

### 7. Access OPNsense Web Interface

- Open a web browser on your host PC
- Visit: `https://10.200.200.254`
- Ignore any SSL warnings (self-signed cert)
- Login with default credentials:
  - Username: `root`
  - Password: `opnsense`

---

### 8. Update OPNsense (Optional but Recommended)

- From the OPNsense console menu, select option `12` to upgrade
- If you see long messages with “END” at the bottom, press `q` to quit the message pager
- Allow the update to complete and reboot the VM (`Option 6`)
- Access the web GUI again to confirm the update
