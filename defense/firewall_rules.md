# Windows Firewall – Block Attacker IP (Incident Response)

## Description

After detecting suspicious activity in Splunk (multiple failed RDP login attempts – EventCode 4625), the attacker IP address was blocked using Windows Defender Firewall.

This demonstrates the **Response / Containment** phase of the Cyber Kill Chain.

The attacker system (Kali Linux) was prevented from continuing brute-force attempts against the Windows Server.

---

## Create Firewall Rule to Block Attacker

Open **Windows Defender Firewall with Advanced Security**

### Step 1 – Navigate to Inbound Rules

Left panel:

```
Inbound Rules
```

Right panel:

```
New Rule...
```

---

### Step 2 – Rule Configuration

Rule Type:

```
Custom
```

Program:

```
All programs
```

Protocol and Ports:

```
Any
```

Scope:

Under remote IP addresses:

```
These IP addresses → Add → 10.0.2.5
```

Action:

```
Block the connection
```

Profile:

```
Domain
Private
Public
```

---

### Step 3 – Name the Rule

Example:

```
Name:
Block Attacker - Kali Linux (10.0.2.5)

Description:
Incident Response - Block brute-force attacker from Kali after detection in Splunk
```

Click Finish.

---

## Expected Result

The Kali Linux attacker machine can no longer connect to the Windows Server via RDP.

Further brute-force attempts will fail due to firewall restrictions.

---

## Detection Evidence in Splunk

Example search:

```spl
index="main" sourcetype="WinEventLog:Security" EventCode=4625
```

Indicators of attack:

* High volume failed logons
* Repeated attempts from single IP address
* Target account: Administrator
* Protocol: RDP (3389)

---

## Cyber Kill Chain Mapping

| Phase | Tool |
|------|------|
| Reconnaissance | netdiscover |
| Scanning | nmap |
| Exploitation | hydra |
| Access | xfreerdp |
| Detection | Splunk SIEM |
| Response | Windows Firewall block rule |

---

## Security Insight

Blocking malicious IP addresses is a common containment step during incident response.

Firewall rules help:

* stop brute-force attacks
* prevent lateral movement
* reduce attacker persistence
* protect exposed services

This demonstrates how SIEM detection integrates with defensive controls.
