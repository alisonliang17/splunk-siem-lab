# 🔐 Splunk SIEM Security Lab

## 📌 Project Overview
A hands-on cybersecurity lab that simulates real-world RDP brute force attacks and detects them in real-time using Splunk SIEM. This project demonstrates both offensive (Red Team) and defensive (Blue Team) security techniques.

## 🛠️ Tools & Technologies
- Splunk Enterprise 9.4.3
- Splunk Universal Forwarder 9.4.0
- Kali Linux
- Windows Server 2022
- Hydra
- xfreerdp
- Metasploit Framework

## ⚔️ Attacks Simulated

### 1. RDP Brute Force (Hydra)
Simulated brute force attack against Windows Server RDP using a custom password list.
- Detection: EventCode 4625 Failed Login

### 2. Remote Desktop Takeover (xfreerdp)
Gained full remote desktop access after cracking the password.
- Detection: EventCode 4624 Successful Login

### 3. Metasploit Exploitation
Further exploitation after initial access.

## 📊 Splunk Detection Queries
index="main" sourcetype="WinEventLog:Security" EventCode=4625
index="main" sourcetype="WinEventLog:Security" EventCode=4624

## 🔵 Blue Team Defense
- Block attacking IP via Windows Firewall
- Enable account lockout after 5 failed attempts
- Real-time monitoring and automated alerts

## 🎯 Key Learnings
- Built full SIEM environment from scratch
- Simulated real-world attacks
- Created real-time dashboards and alerts
- Practiced Red Team and Blue Team techniques

## ⚠️ Disclaimer
Educational purposes only. All attacks performed in isolated virtual machine environment.
