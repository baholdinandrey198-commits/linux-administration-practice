# Linux Storage Administration Lab

## Objective

Practice inspecting disks, partitions, filesystems, LVM, and software RAID on Ubuntu Server 24.04.5 LTS running in Oracle VirtualBox.

## Environment

- OS: Ubuntu Server 24.04.5 LTS
- Kernel: Linux 6.8.0-142-generic
- Virtualization: Oracle VirtualBox

## Tools Used

- `lsblk` — inspect block devices and storage layout
- `lsblk -f` — inspect filesystem types and UUIDs
- `df -h` — inspect filesystem capacity and usage
- `findmnt` — inspect mounted filesystems
- `pvs` — inspect LVM physical volumes
- `cat /proc/mdstat` — inspect software RAID status
- `mdadm --detail` — inspect RAID array details
- `mdadm --examine` — inspect RAID member metadata
- `blkid` — identify filesystem and device signatures
- `wipefs` — inspect known signatures when run without destructive options

## Findings

### System Disk and LVM

- System disk: `/dev/sda`, approximately 30 GB
- Boot partition: `/dev/sda2`, mounted at `/boot`
- LVM physical volume: `/dev/sda3`
- Volume group: `ubuntu-vg`
- Root logical volume: `ubuntu--vg-ubuntu--lv`
- Root filesystem: `ext4`, mounted at `/`

The `pvs` output showed `/dev/sda3` as the physical volume in `ubuntu-vg`. No free physical extents were reported in that volume group.

### Software RAID 1

- RAID device: `/dev/md0`
- RAID level: RAID 1
- Members: `/dev/sdb1` and `/dev/sdc1`
- Array state: `clean`
- Active devices: 2
- Failed devices: 0

The `/proc/mdstat` and `mdadm --detail` outputs showed both RAID members active. The `mdadm --examine` outputs showed matching array UUIDs and valid metadata checksums on both members.

### Additional XFS Partition

The `/dev/sdd1` partition was identified as XFS by `lsblk -f` and `blkid`. It was not shown as mounted in the `findmnt` output.

### RAID Filesystem Investigation

The `blkid` and `wipefs` commands did not report a recognized filesystem signature on `/dev/md0`.

This does not prove that the array contains no data. Its purpose and any previous use remain undetermined.

## Safety Practices

- Inspect storage devices before making changes.
- Verify device names before partitioning or formatting.
- Do not format or remove RAID members without confirming their purpose and checking for important data.
- RAID redundancy is not a substitute for backups.

## Skills Practiced

- Linux storage inspection
- Filesystem identification
- LVM inspection
- Software RAID status checks
- Reading command output
- Safe troubleshooting without modifying storage

## Status

Initial storage inspection completed. Further investigation is required to determine the intended use of the unmounted RAID array and XFS partition.
