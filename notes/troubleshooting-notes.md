# Troubleshooting Notes

## Issue 1

Unable to access network share.

### Resolution

Verify:

- File Sharing enabled
- Advanced Sharing enabled
- Share permissions configured

---

## Issue 2

RunMRU entry not generated.

### Resolution

Access the share using:

```
Win + R
```

instead of browsing directly.

---

## Issue 3

Recent Items empty.

### Resolution

Open files directly from the network share.

Simply browsing the folder may not generate Recent Item shortcuts.

---

## Issue 4

Quick Access not updated.

### Resolution

Open the files from the share and refresh File Explorer.

---

## Issue 5

Share inaccessible.

### Resolution

Verify:

```
\\127.0.0.1\CompanyShare
```

or

```
\\HOSTNAME\CompanyShare
```

---

## Issue 6

Registry path missing.

### Resolution

Confirm the RunMRU key exists under:

```
HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU
```

It is created after using the Run dialog.
