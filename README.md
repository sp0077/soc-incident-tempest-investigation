# TEMPEST Incident Investigation

SOC investigation of a compromised Windows workstation from the TryHackMe TEMPEST challenge.

This project reconstructs the attacker kill chain using network traffic and endpoint telemetry.

---

## Attack Overview

The attack exploited the **Follina vulnerability (CVE-2022-30190)** through a malicious Word document.

The attacker performed the following actions:

1. Delivered malicious document
2. Executed MSDT exploit
3. Downloaded payloads
4. Established command and control communication
5. Escalated privileges
6. Created persistence

---

## Tools Used

- Wireshark
- Sysmon
- Timeline Explorer
- CyberChef

---

## Repository Structure

| Folder | Description |
|------|------|
screenshots | Investigation evidence |
iocs | Indicators of compromise |
detection_rules | Detection engineering |
diagrams | Attack diagrams |

---

## Investigation Report

See full analysis in:

investigation_report.md
