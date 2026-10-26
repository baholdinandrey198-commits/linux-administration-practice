# Linux Disk Management Practice

This document records disk-management concepts studied in my Ubuntu Server virtual lab.

## 1. Display Block Devices

```bash
lsblk
```

Lists block devices, including disks, partitions, and logical volumes.

```bash
lsblk -f
```

Displays filesystems, UUIDs, and mount points where available.

## 2. Check Filesystem Space

```bash
df -h
```

Displays filesystem capacity and usage in a human-readable format.

```bash
du -sh "$HOME"
```

Shows the total space used by the user's home directory.

## 3. Inspect Disk Partitions

```bash
sudo fdisk -l
```

Lists detected disks and their partition tables.

## 4. MBR and GPT

MBR and GPT are partition-table formats.

- **MBR (Master Boot Record):** an older partitioning scheme with limitations on partition layout and disk size.
- **GPT (GUID Partition Table):** a newer scheme that supports large disks and many partitions.

Partition changes should only be made to the intended disk in a test environment.

## 5. Logical Volume Manager (LVM)

LVM allows Linux storage to be managed through physical volumes, volume groups, and logical volumes.

Useful inspection commands:

```bash
sudo pvs
```

Displays physical volumes.

```bash
sudo vgs
```

Displays volume groups.

```bash
sudo lvs
```

Displays logical volumes.

## 6. Important Safety Notes

- Check the target device before modifying partitions.
- Commands that change partition tables can cause data loss.
- Do not format or repartition a disk unless you have verified that it is the intended test disk.
- Inspection commands are a safer starting point when learning disk administration.

## Key Takeaways

- `lsblk` helps inspect block devices.
- `df -h` shows filesystem space usage.
- `fdisk -l` displays partition information.
- `pvs`, `vgs`, and `lvs` inspect LVM configuration.

This document is part of my ongoing Linux administration practice.
