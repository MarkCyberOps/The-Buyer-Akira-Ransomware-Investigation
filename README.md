# The Buyer – Akira Ransomware Investigation

## Overview

This repository documents a full digital forensics and incident response (DFIR) investigation involving a ransomware attack attributed to an Akira affiliate.

The attacker re-entered the environment using pre-staged access and executed a multi-stage intrusion involving credential theft, lateral movement, data exfiltration, and ransomware deployment.

---

## Scenario Overview

<img width="500" height="700" alt="thebuyer" src="https://github.com/user-attachments/assets/3c2d8033-2ba1-4ea3-8688-18a54b1d2c11" />


---

## Ransom Note Evidence

<img width="705" height="726" alt="ransom note" src="https://github.com/user-attachments/assets/45209df5-08c9-4ea5-b8bf-58de53141072" />


---

## Encrypted Environment

<img width="713" height="617" alt="Ransom Impact File server Encrypted" src="https://github.com/user-attachments/assets/b0c74c8e-a94d-4260-bf9d-1591d696838e" />


---

## Objectives

- Identify initial access vector
- Track attacker activity across endpoints
- Detect credential access and lateral movement
- Analyze command and control behavior
- Investigate data exfiltration
- Identify ransomware execution
- Determine scope of compromise

---

## Environment

- Platform: Microsoft Defender for Endpoint (MDE)
- Query Language: KQL
- Hosts:
  - as-pc2
  - as-srv

---

## Compromised Hosts
  - as-pc2
  - as-srv

---

## Attack Chain Summary
  - Initial Access → AnyDesk (as-pc2)
  - Execution → wsync.exe
  - Credential Access → LSASS dump
  - Lateral Movement → as.srv.administrator → as-srv
  - Reconnaissance → scan.exe
  - Tool Transfer → bitsadmin → Invoke-WebRequest
  - Exfiltration → st.exe → exfil_data.zip
  - Recovery Prevention → wmic shadowcopy delete
  - Ransomware Deployment → updater.exe
  - Impact → akira_readme.txt
  - Anti-Forensics → clean.bat

---

## Key Findings

### Initial Access
- Remote access established via AnyDesk
- Persistence from previous compromise reused

### Credential Access
- LSASS memory accessed
- Process discovery used to locate target

### Lateral Movement
- Administrator account leveraged:
  - as.srv.administrator

### Exfiltration
- Data compressed using:
  - st.exe
- Archive created:
  - exfil_data.zip

### Ransomware Deployment
- Payload disguised as:
  - updater.exe
- SHA256:
  - e609d070ee9f76934d73353be4ef7ff34b3ecc3a2d1e5d052140ed4cb9e4752b

### Anti-Forensics
- Cleanup script:
  - clean.bat
- Payload removed post-execution

---

## Indicators of Compromise

### Domains
- sync.cloud-endpoint.net
- cdn.cloud-endpoint.net

### IP Addresses
- 104.21.30.237
- 172.67.174.46
- 88.97.164.155

### Hashes

Ransomware: e609d070ee9f76934d73353be4ef7ff34b3ecc3a2d1e5d052140ed4cb9e4752b

Staging Tool: 512a1f4ed9f512572608c729a2b89f44ea66a40433073aedcd914bd2d33b7015
