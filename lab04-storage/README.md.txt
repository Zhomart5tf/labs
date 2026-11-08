# Lab 4 — Partition, mirror, fail, recover

## Windows
- Added a 2 GB virtual disk to the Windows 11 guest, created one NTFS volume (label Data) and assigned the letter E:.
- Partition style: GPT. Windows 11 runs in UEFI mode, and GPT supports disks over 2 TB and more than 4 partitions, which MBR does not.

## Layout before
- sda (8 GB): system disk with Ubuntu.
- sdb, sdc, sdd (2 GB each): empty, no partitions.

## Layout after
- sdb1 and sdc1 (GPT, raid flag) were joined into the RAID 1 array /dev/md0 (ext4, mounted at /mnt/raid).
- sdb1 was failed and removed, then sdd1 was added and the array rebuilt.
- Final state: /dev/md0 = sdc1 + sdd1, clean, [UU].

## What I did
1. Listed the disks (lsblk).
2. Created the RAID 1 array on sdb1 and sdc1 and checked it was healthy.
3. Wrote testfile.txt to the mirror and recorded its SHA-256 checksum.
4. Failed and removed sdb1, the array became degraded.
5. Read the file again, the checksum was identical.
6. Added sdd1 and watched the rebuild finish.

## Evidence
- evidence/lsblk-before.txt: disks before any changes
- evidence/array-healthy.txt: array healthy ([UU], clean)
- evidence/checksum-before.txt: checksum before the failure
- evidence/array-degraded.png: array degraded after failing sdb1 (screenshot)
- evidence/checksum-after-failure.png: checksum after the failure, same value (screenshot)
- evidence/array-rebuilt.png: array rebuilt with sdd1 (screenshot)

## Question: your colleague deleted the wrong file from the mirror an hour ago. Does RAID 1 help? Why?
No, RAID 1 does not help here. RAID 1 copies every write to both disks immediately, so the deletion was written to both disks at once. RAID protects against a disk failure, not against mistakes, so only a backup can bring the file back.