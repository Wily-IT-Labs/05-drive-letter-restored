# TechNova IT Support Lab — Ticket #1045
## Windows 11 Disk Management Troubleshooting

### Overview

This hands-on IT support lab simulates a storage-related incident at TechNova, a fictional company. The objective was to configure a new virtual disk, troubleshoot a missing drive letter, and restore access to the storage volume using Windows Disk Management.

### Lab Environment

- **Operating System:** Windows 11 Pro
- **Virtualization:** VMware Workstation
- **Workstation:** PC01
- **Additional Virtual Disk:** 5 GB NVMe
- **File System:** NTFS
- **Troubleshooting Tool:** Disk Management (`diskmgmt.msc`)

### Incident Description

**Ticket ID:** #1045  
**Category:** Storage / Disk Management  
**Priority:** Medium  
**Status:** Resolved

A user reported that a secondary storage drive was no longer visible in File Explorer.

The IT technician was assigned to investigate the missing drive, identify the cause, and restore access without unnecessarily formatting or deleting the existing volume.

### Troubleshooting Procedure

**Step 1 — Initialize the new disk**

A new 5 GB virtual disk was attached to the Windows 11 virtual machine through VMware Workstation.

Disk Management detected the disk as unknown and not initialized.

The disk was initialized using the GPT partition style.

![Disk initialization](Disk%20Management/01-disk-not-initialized.png)

**Step 2 — Configure and verify the storage volume**

A new simple volume was created, formatted with NTFS, assigned drive letter E:, and labeled `technova-data`.

Disk Management confirmed that the volume was online and healthy.

![Healthy NTFS volume](Disk%20Management/02-disk-initialized-healthy.png)

**Step 3 — Simulate a missing drive letter**

The E: drive letter was removed to reproduce a common support incident in which a healthy storage volume is no longer accessible through its previous drive letter.

The partition remained present and healthy in Disk Management.

![Missing drive letter](Disk%20Management/03-drive-letter-missing.png)

**Step 4 — Diagnose the issue**

The technician opened Disk Management using `diskmgmt.msc`, located the secondary disk, and verified that the NTFS volume still existed.

The **Change Drive Letter and Paths** option was used to address the missing drive letter.

![Drive letter troubleshooting](Disk%20Management/04-drive-letter-troubleshooting.png)

**Step 5 — Restore and verify access**

Drive letter E: was reassigned to the existing NTFS volume.

The final verification confirmed that the volume was online, healthy, and accessible again without recreating or formatting the partition.

![Restored E drive](Disk%20Management/05-drive-letter-restored.png)

### Root Cause

The storage volume had lost its assigned drive letter. Although the partition remained healthy, Windows could not access it through its previous E: path.

### Resolution

The original drive letter was restored using Disk Management. No repartitioning or reformatting was necessary during recovery
