#  Cyber Range Lab (SOC + Active Directory Environment)

Built a hands-on cybersecurity lab to simulate real-world attacks and detection using SIEM and endpoint monitoring.

---

##  Technologies Used
- Proxmox (virtualization)
- Active Directory (Domain Controller)
- Kali Linux (attack machines)
- Windows endpoints
- Wazuh (SIEM)
- Sysmon (endpoint logging)
- Apache Guacamole (remote access)
- VPN (remote connectivity)

---

##  Lab Architecture
- Multiple Kali Linux machines used for offensive testing  
- Windows systems joined to an Active Directory domain  
- Domain Controller managing authentication and policies  
- Group Policy (GPO) used to deploy Wazuh agents  
- Centralized logging and alerting through Wazuh  
- Remote access provided via Apache Guacamole  

---

##  Attack Scenarios
- Network enumeration (Nmap)  
- AS-REP Roasting (Active Directory attack)  
- Lateral movement between systems  
- Password cracking using Hashcat  

---

##  Detection & Monitoring
- Wazuh used to detect suspicious activity and generate alerts  
- Sysmon configured for detailed endpoint logging  
- Analyzed logs to identify attacker behavior  

---

##  Lab Screenshots (coming soon)
- Wazuh alerts dashboard  
- Proxmox environment  
- Kali attack activity  
- Guacamole remote sessions  

---

##  What I’m Working Toward
- Tier 2 SOC Analyst Internship  
- Incident detection and response  
- Active Directory attack detection and defense  
