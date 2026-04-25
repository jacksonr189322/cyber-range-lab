#  Lab Setup – Cyber Range Network

##  Step 1 – Create Isolated Network in Proxmox

To separate the cyber range from my main environment, I created a dedicated network bridge inside Proxmox.


Bridge name: vmbr1

This allows all lab machines to communicate on an isolated internal network.

---

## ⚙️ Configuration Steps

### 1. Access Network Settings
- Select Proxmox node
- Navigate to:
  - System → Network

---

### 2. Create New Linux Bridge
- Click “Create” → Linux Bridge
- Set bridge name to: vmbr1

- Leave gateway blank (internal network only)

---

### 3. Apply Configuration
- Apply changes and restart network if needed

---

## 🌐 Internal Network Design

I used the following subnet for the cyber range: 10.50.0.0/24


---

##  IP Addressing Plan

| Host Name       | IP Address   | Role |
|----------------|-------------|------|
| CE-GUACAMOLE   | 10.50.0.5   | Remote access gateway |
| CE-DC01        | 10.50.0.10  | Domain Controller |
| CE-FILE01      | 10.50.0.20  | File Server |
| CE-WAZUH       | 10.50.0.50  | SIEM / Monitoring |
| CE-WS01        | 10.50.0.100 | Windows Workstation |
| CE-WS02        | 10.50.0.101 | Windows Workstation |
| CE-WS03        | 10.50.0.102 | Windows Workstation |
| CE-KALI01      | 10.50.0.200 | Attack Machine |

---

 🎯 Purpose

All systems are connected to **vmbr1** to simulate a real internal enterprise network.  

This setup allows me to:
- Practice Active Directory attacks  
- Monitor traffic and logs with Wazuh  
- Simulate lateral movement inside a network  
- Test detection and response scenarios  

---

##  Screenshots 
- Proxmox vm
  <img width="279" height="297" alt="vms png" src="https://github.com/user-attachments/assets/f680259f-210d-46ca-9a76-59c0defa8bd3" />
 configuration

- vmbr1 bridge setup
  <img width="1445" height="70" alt="proxmox-network png" src="https://github.com/user-attachments/assets/e504b28d-e344-421d-bd10-a349047cc842" />


- 
- VM network assignments  
