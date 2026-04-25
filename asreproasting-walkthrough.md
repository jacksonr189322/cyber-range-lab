#  AS-REP Roasting

##  What This Attack Does

AS-REP Roasting checks if any users can authenticate **without Kerberos pre-authentication**.

If successful:
- The Domain Controller returns a **TGT hash**
- The hash can be cracked offline using:
  - Hashcat
  - John the Ripper  

---

##  What the Attack Targets

This attack targets **Kerberos pre-authentication**.

- Normally: user must verify identity before getting a TGT  
- If disabled: DC sends AS-REP response without verification  

 This creates a weakness in Kerberos that attackers can exploit.
 <img width="2880" height="1800" alt="disable_preauthentication" src="https://github.com/user-attachments/assets/10a3dbef-dcbc-481a-ae08-aeea8833752b" />


---

## How the Attack Works

1. Gather valid usernames  
2. Place them into a text file  
3. Send requests to the Domain Controller  
4. Identify users with pre-authentication disabled  
5. Extract AS-REP hashes  

---

## Example User List

- Administrator  
- mleak  
- hjohnson  
- ljackson  
- SQLService  
- Guest  

---

## Running the Attack

**Location of tool on Kali:**

---

## Attack Command & Output


---

**Command used:**
```bash
python3 GetNPUsers.py CyberEye.local/ -usersfile /home/randy/users.txt -no-pass -dc-ip <>
![AS-REP Attack Output](https://github.com/user-attachments/assets/3dd68797-bf11-40f7-b916-3cb422a7a255)
This command sends authentication requests to the Domain Controller and identifies users with pre-authentication disabled.

Retrieved Hashes
![AS-REP Hashes](https://github.com/user-attachments/assets/f3d1d916-72c4-4002-ac0f-7ed0bf9fff0)




Users observed:
mleak
administrator
hjohnson

Phase 2 – Cracking the Hash

1. Save hash:
nano hashes.txt

2. Navigate to wordlist:
cd /usr/share/wordlists

3. Unzip:
gunzip rockyou.txt.gz

4.Run Hashcat:
hashcat -m 18200 hashes.txt /usr/share/wordlists/rockyou.txt

Key Takeaway
AS-REP Roasting is a simple but powerful attack that exploits weak Active Directory configurations.
Proper configuration and monitoring are critical to prevent this.
