# windows-network-share-access-investigation-dfir-lab
## Overview

This Digital Forensics and Incident Response (DFIR) lab demonstrates how Windows preserves evidence after a user accesses a shared network folder (SMB Share). Although network shares are commonly used inside organizations, they are also frequently abused by attackers for lateral movement, data staging, and internal file transfer.

The objective of this investigation is to identify forensic artifacts generated after connecting to a shared folder and opening files from it.

---

# Executive Summary

During this investigation, a local SMB network share was created and accessed from Windows Explorer.

Several forensic artifacts were generated automatically by Windows, including:

- SMB Share Configuration
- Registry RunMRU entries
- Recent Items shortcuts
- Quick Access entries

These artifacts collectively demonstrate that the user successfully accessed a remote shared folder and interacted with files stored on that share.

---

# Investigation Objectives

- Create an SMB network share
- Access the shared folder through Windows Explorer
- Open files from the share
- Examine Registry artifacts
- Investigate Recent Items
- Examine Quick Access entries
- Correlate evidence to reconstruct user activity

---

# DFIR Concepts Covered

## SMB (Server Message Block)

SMB is the Windows protocol used for file and printer sharing across systems.

Examples:

```
\\SERVER\Finance
```

or

```
\\192.168.1.20\SharedDocs
```

Attackers frequently use SMB for:

- Internal reconnaissance
- File transfer
- Data staging
- Lateral movement

Windows preserves numerous forensic artifacts after accessing these locations.

---

## Registry RunMRU

Location

```
HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU
```

Stores commands executed through the Windows Run dialog.

---

## Recent Items

Location

```
%APPDATA%\Microsoft\Windows\Recent
```

Stores shortcuts pointing to recently opened files and folders.

---

## Quick Access

Quick Access maintains references to frequently accessed folders and recently opened files, making it another valuable artifact during DFIR investigations.

---

# Tools Used

- Windows 10
- Windows Registry Editor
- Windows Explorer
- PowerShell
- SMB File Sharing
- Recent Items
- Quick Access

---

# Lab Environment

| Component | Details |
|-----------|---------|
| OS | Windows 10 x64 |
| VM Platform | VMware Workstation Player |
| Investigation Type | Host-based DFIR |
| Share Type | Local SMB Share |
| Registry Tool | Registry Editor |
| Shell | PowerShell |

---

# Skills Demonstrated

- SMB Share Investigation
- Windows Registry Analysis
- Registry RunMRU Analysis
- Windows Explorer Artifact Analysis
- Recent Items Investigation
- Quick Access Analysis
- User Activity Reconstruction
- Evidence Correlation
- DFIR Documentation
- Timeline Reconstruction

---

# MITRE ATT&CK Mapping

| Technique | ID |
|----------|----|
| Network Share Discovery | T1135 |
| Remote Services (SMB) | T1021.002 |
| Data from Network Shared Drive | T1039 |

---

# Evidence Collected

- SMB Share Configuration
- Shared Folder
- Registry RunMRU
- Recent Items
- Quick Access Entries
- File Access Evidence

---

# Evidence Correlation

The investigation correlated multiple independent Windows artifacts:

1. SMB share successfully configured.
2. User accessed the share through Windows Explorer.
3. RunMRU recorded the executed path.
4. Recent Items generated shortcuts to the opened files.
5. Quick Access displayed the shared folder and recently opened files.

Together, these artifacts provide strong evidence that the user interacted with the network share.

---

# Investigation Findings

The investigation confirmed that Windows preserves multiple independent forensic artifacts after a network share is accessed. Even if the share is no longer connected, Registry entries, Recent Items, and Quick Access can still reveal historical user activity.

---

# Key Takeaway

Network share activity leaves evidence in multiple Windows locations. Correlating Registry, Recent Items, and Quick Access artifacts allows investigators to accurately reconstruct user interaction with shared resources, making these artifacts valuable during incident response and forensic investigations.
