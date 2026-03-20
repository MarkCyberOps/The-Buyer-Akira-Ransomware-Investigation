# The Buyer – Akira Ransomware Investigation (DFIR Lab)

## Overview
This project documents a full-scale ransomware investigation conducted in a simulated SOC environment. The scenario follows a threat actor who re-entered a network using pre-staged access and deployed Akira ransomware.

The objective was to investigate the attack end-to-end, identify attacker techniques, and determine the full scope of compromise using Microsoft Defender for Endpoint (MDE) and KQL.

---

## Objectives
- Identify initial access vector
- Track attacker activity across hosts
- Detect credential theft and lateral movement
- Analyze command & control (C2) activity
- Investigate data exfiltration
- Identify ransomware deployment and impact
- Determine scope of compromised systems

---

## Key Findings

### 🖥️ Compromised Hosts
- `as-pc2` (Initial access & staging)
- `as-srv` (Lateral movement & ransomware execution)

---

## Attack Chain Summary

```text
Initial Access → AnyDesk (as-pc2)
Execution → wsync.exe (C2 beacon)
Recon → scan.exe (network discovery)
Credential Access → LSASS dump
Lateral Movement → as.srv.administrator → as-srv
Tool Transfer → bitsadmin → Invoke-WebRequest
Exfiltration → st.exe → exfil_data.zip
Recovery Prevention → wmic shadowcopy delete
Ransomware → updater.exe
Impact → akira_readme.txt
Anti-Forensics → clean.bat
