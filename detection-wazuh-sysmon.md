##  Sysmon Setup and Integration with Wazuh

### 1️ Install Sysmon on Windows Endpoint

#### Option A – Manual Install
- Download Sysmon from Microsoft Sysinternals  
- Extract the zip file to a directory (ex: `C:\Tools\Sysmon`)  

#### Option B – PowerShell Install
Run PowerShell as Administrator:

```powershell
mkdir C:\Tools\Sysmon
cd C:\Tools\Sysmon

Invoke-WebRequest `
-Uri "https://download.sysinternals.com/files/Sysmon.zip" `
-OutFile "Sysmon.zip"

Expand-Archive Sysmon.zip -DestinationPath

### 2 Apply a Sysmon Configuration
Invoke-WebRequest `
-Uri "https://raw.githubusercontent.com/SwiftOnSecurity/sysmon-config/master/sysmonconfig-export.xml" `
-OutFile sysmonconfig.xml

### 3 Install Sysmon with Config
.\Sysmon64.exe -accepteula -i sysmonconfig.xml

### 4 Verify Sysmon Logs
Location:
Event Viewer → Applications and Services Logs → Microsoft → Windows → Sysmon → Operational

### 5 Wazuh Integration
File:
C:\Program Files (x86)\ossec-agent\ossec.conf

<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>

Restart Wazuh agent.
