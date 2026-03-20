# Detailed Analysis

## Initial Access

The attacker re-entered the environment using AnyDesk, indicating persistence from a prior compromise.

## Execution

A malicious binary (wsync.exe) was downloaded and executed using PowerShell.

## Credential Access

The attacker performed process enumeration and accessed LSASS memory to extract credentials.

## Lateral Movement

Using stolen credentials, the attacker authenticated to as-srv with administrative privileges.

## Reconnaissance

Network scanning was performed using scan.exe (Advanced IP Scanner).

## Tool Transfer

Initial download via bitsadmin failed. The attacker switched to PowerShell Invoke-WebRequest.

## Exfiltration

Data was compressed using st.exe and stored as exfil_data.zip.

## Defense Evasion

Microsoft Defender was disabled via registry modification and PowerShell.

## Impact

Ransomware (updater.exe) executed and encrypted files. The ransom note akira_readme.txt was dropped.

## Anti-Forensics

A cleanup script (clean.bat) deleted the ransomware binary post-execution.
