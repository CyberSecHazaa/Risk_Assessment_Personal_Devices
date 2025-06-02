# Risk_Assessment_Personal_Devices
**Scope**: Personal Devices, excluding Router
**Assessor**: CyberSecHazaa
**Date**: 5/27/25
**Scan Tools Used**: Nmap (Nmap -A -O, Nmap --script vuln, Nmap -sV, Nmap, -sT)

1. **Introduction**
	- **Purpose**: As an upcoming Cybersecurity Professional, I value security for my devices and ensure that they're as secure as they can be to minimize any potential threats. Using Kali-Linux Tools and NIST CSF to identify, evaluate and mitigate device vulnerabilities.
	-  **Scope**: This assessment evaluates all personal devices that are owned which are listed below 
		- ==Notice==: To ensure personal-security since for this Assessment since it will be public, Router will not be included as well as the names of devices/IP or versions will not be included for privacy rasons.
		- Despite the in-depth recon, there wasn't much to be secured in general due to me always ensuring the security of the devices and frequent updates and some change of configurations.

**Asset Inventory** 

| Device Name      | Type               | OS         | Purpose                                     | Owner | Location |
| ---------------- | ------------------ | ---------- | ------------------------------------------- | ----- | -------- |
| Custom Build PC  | Desktop            | Arch-Linux | Work Station                                | Self  | Home     |
| Raspberry PI 5   | ARM-Based Computer | Kali-Linux | Ethical Hacking                             | Self  | Anywhere |
| Raspberry PI 4   | ARM-Based Computer | Kali-Linux | Monitoring Home Network                     | Self  | Home     |
| Dell Laptop 1    | Laptop             | Arch-Linux | Homework/Ethical Hacking                    | Self  | Anywhere |
| Dell Laptop 2    | Laptop             | Debian     | A SIEM (Wazuh) that Monitors all my devices | Self  | Home     |
| Samsung TV       | TV                 | Android    | Entertainment                               | Self  | Home     |
| Phone            | Phone              | Android    | Personal Phone                              | Self  | Anywhere |

**Risk Assessment Framework** 
- **Methodology**: Risk = Likelihood X Impact
- **Risk Rating:** High/Medium/Low


**Threat & Vulnerability Identification** 

| Device Name      | Open Ports/Services              | Detected Vulnerbilites                                                               | Severity | Exploitability | Poteninal Impact                                                   | Overall Risk |
| ---------------- | -------------------------------- | ------------------------------------------------------------------------------------ | -------- | -------------- | ------------------------------------------------------------------ | ------------ |
| Costume Build PC | None                             | None                                                                                 | Low      | Low            | None                                                               | Low          |
| Raspberry PI 5   | 22 (SSH)                         | None                                                                                 | Medium   | Low            | Port 22 may be exploited via Brute-Force                           | Low          |
| Raspberry PI 4   | 22 (SSH), 21 (FTP), 80 (Apache2) | None                                                                                 | Medium   | N/A Medium         | Port 22 & 21 may be exploited via Brute-Force                 | High         |
| Dell Laptop 1    | None                             | None                                                                                 | Low      | Low            | None                                                               | Low          |
| Dell Laptop 2    | 22 (SSH), HTTP (80)              | Susceptible to DOS attack, HTTP tampering, Vulnerable to Brute-Force for SSH & HTTP. | High     | High           | Port 80 (A login dashboard) & 21 may be exploited via Brute-Force. | High         |
| Samsung TV       | 9 costume Ports Open             | None of the ports lead to anything, they solely used for specific services.          | Low      | High           | Despite that, 9 ports increases the attack-surface.                | Medium       |
| Phone            | None                             | None                                                                                 | Low      | Low            | None                                                               | Low          |


**Existing Controls**

| Control Type   | Description                                                 | Assets Covered          | Effectivness |
| -------------- | ----------------------------------------------------------- | ----------------------- | ------------ |
| Technical      | Enable KGpg on all desktops, comes pre installed with Arch. | Desktop, Laptop         | High         |
| Administrative | Daily updates & upgrades                                    | Desktop, Laptop 1, Pi 5 | High         |
| Physical       | Device is off completely when not inside                    | Desktop, Laptop 1 & 2   | Low          |

**Risk Treatment Plan** 

| Devices          | Risk   | Mitigations                                                                                                                                                                                                                                                                                        | Responsible Party | Timeline  | Residual Risk |
| ---------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | --------- | ------------- |
| Costume Build PC | Low    | Encrypt data & files and have frequent backups, since it contains a lot of data.                                                                                                                                                                                                                   | Self              | N/A       | Low           |
| Raspberry PI 5   | Medium | Configure SSH to only allow specific IP addresses and deny everything else.                                                                                                                                                                                                                        | Self              | Medium    | Low           |
| Raspberry PI 4   | High   | Have longer password, update more frequently, disable ssh and ftp. It also has a short password as well as it doesn't have timed lock-out screen.                                                                                                                                                  | Self              | Immediate | Medium        |
| Dell Laptop 1    | Low    | Encrypt data & files and have some backups since Laptop 1 doesn't contain much data.                                                                                                                                                                                                               | Self              | N/A       |      Low       |
| Dell Laptop 2    | High   | Install tools like UFW to configure rules and deny incoming traffic expect trusted IPs. Have a strong Wazuh Dashboard password. This device stays unlocked always, have a reasonable lock-out timer. Also allow 3 to 4 password tries before getting locked out. Allow only legitimate HTTP verbs. | Self              | Immediate | High          |
| Samsung TV       | Medium | Close unneeded/unused ports                                                                                                                                                                                                                                                                        | Self              | Immediate | Medium        |
| Phone            | Low    | Encrypt data & files and have frequent backups, since it contains a lot of data.                                                                                                                                                                                                                   | Self              | N/A       | Low           |

Compliance & Policy Mapping 

**Personal Policy** 
- Regular Backups & Encrypt Drives
- Always update all systems at least once a week 
- Use Secure Protocols instead of none-secure ones, such as SFTP 

**Review & Monitoring** 
- Review monthly
- Ongoing monitoring:
	- Updates
	- Ports
	- Logs
	- Permissions
	- Alerts

Summary
- Total Devices: 7
- Critical Risks Identified: 1
- Most were low/medium risks
- Continue improvement to securing devices 
