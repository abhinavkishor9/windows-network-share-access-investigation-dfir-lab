# Investigation Notes

## Lab Summary

Objective:

Investigate forensic artifacts generated after accessing an SMB network share.

---

# Analyst Methodology

The investigation followed a structured DFIR workflow:

1. Create a local SMB network share.
2. Populate the share with sample documents.
3. Access the share using Windows Explorer.
4. Open multiple files from the shared location.
5. Examine Registry artifacts.
6. Inspect Recent Items.
7. Review Quick Access.
8. Correlate all artifacts.
9. Produce a forensic timeline.

---

# Investigation Steps

## Step 1

Created folder:

```
C:\NetworkShareLab
```

---

## Step 2

Created sample files:

- Confidential.docx
- EmployeeData.xlsx
- Payroll.txt

---

## Step 3

Enabled Advanced Sharing.

Share Name:

```
CompanyShare
```

---

## Step 4

Verified hostname.

Example:

```
DESKTOP-SCIQBLO
```

---

## Step 5

Accessed:

```
\\127.0.0.1\CompanyShare
```

Opened all three documents.

---

## Step 6

Investigated Registry:

```
HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU
```

Observed the executed share path.

---

## Step 7

Investigated:

```
%APPDATA%\Microsoft\Windows\Recent
```

Observed shortcut files for:

- Confidential.docx
- EmployeeData.xlsx
- Payroll.txt
- CompanyShare

---

## Step 8

Reviewed Quick Access.

Observed:

- CompanyShare
- Confidential.docx
- EmployeeData.xlsx
- Payroll.txt

---

# Evidence Collected

- Shared folder configuration
- Registry RunMRU
- Recent Items shortcuts
- Quick Access references

---

# Analyst Observations

Windows generated multiple independent artifacts after the network share was accessed.

Each artifact independently confirmed:

- The share was opened.
- Files were accessed.
- Windows recorded user activity in several locations.

The combination of Registry and Explorer artifacts provides reliable evidence for reconstructing SMB access during DFIR investigations.

---

# Conclusion

The investigation successfully demonstrated how Windows records network share access through Registry and Explorer artifacts, enabling investigators to reconstruct user interaction with shared resources.
