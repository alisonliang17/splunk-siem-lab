1

2

After a successful brute-force attack using Hydra, valid credentials (username and password)
are obtained.
At this stage, the attacker is no longer exploiting access—they are authenticating legitimately
using compromised credentials.
Remote Desktop Login (RDP)
From Kali Linux
- Install RDP client:
sudo apt install xfreerdp
- Connect to the victim machine:
xfreerdp /u:Administrator /p:'Password.1!!' /v:10.0.2.6
Key Concept
● Attack Phase Transition:
○ Brute Force Credential Compromise Legitimate Access➜ ➜
● This technique maps to:
○ Valid Accounts (MITRE ATT&CK T1078)
Post-Access Attack Simulation
Once access is gained, attackers typically perform the following actions:
1. Privilege Escalation
● Gain higher-level permissions (e.g., SYSTEM access)
2. Credential Dumping & Lateral Movement
● Extract credentials and access other systems
3. Persistence
● Maintain long-term access (e.g., create new admin user)
4. Data Exfiltration
● Collect and transfer sensitive files
5. Malware Simulation
● Execute controlled payloads for testing detection
6. Password Spraying
● Attempt one password across multiple accounts
Detection Opportunities (Splunk)
● Successful RDP login after multiple failed attempts
● Logon Type 10 (Remote Interactive)
● New or unusual source IP address
● Privileged account login activity
