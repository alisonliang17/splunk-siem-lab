# Attack Phases & Post-Access Simulation

## Phase 2: Credential Access → Legitimate Login

After a successful brute-force attack using Hydra, valid credentials are obtained.
The attacker is no longer exploiting a vulnerability — they are authenticating
legitimately using compromised credentials.

> **MITRE ATT&CK: Valid Accounts (T1078)**

---

## RDP Remote Access from Kali Linux

### Install RDP Client
```bash
sudo apt install xfreerdp
```

### Connect to Victim Machine
```bash
xfreerdp /u:Administrator /p:'Password.1!!' /v:10.0.2.6
```

---

## Attack Phase Transition

Brute Force → Credential Compromise → Legitimate Access

---

## Post-Access Techniques

| Phase | Technique | Description |
|-------|-----------|-------------|
| 1 | Privilege Escalation | Gain SYSTEM-level permissions |
| 2 | Credential Dumping | Extract credentials for lateral movement |
| 3 | Persistence | Create new admin account for long-term access |
| 4 | Data Exfiltration | Collect and transfer sensitive files |
| 5 | Malware Simulation | Execute controlled payloads to test detection |
| 6 | Password Spraying | Try one password across multiple accounts |

---

## Splunk Detection Opportunities

```spl
index="main" sourcetype="WinEventLog:Security" EventCode=4624 Logon_Type=10
```

### What to Look For
- Successful RDP login after multiple failed attempts
- Logon Type 10 (Remote Interactive)
- New or unusual source IP address
- Privileged account login activity
