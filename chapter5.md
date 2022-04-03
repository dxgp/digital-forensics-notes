# File Systems
## Boot Sequence
Terminology:
- **CMOS**: Complementary Metal Oxide Semiconductor stores the BIOS
- **EFI**: Extensible Firmware Interface defines the interface between the firmware and the OS
- **UEFI**: Newer version of EFI.
- **MBR**: Master Boot Record is the information in the first sector of the disk that identifies how and where the OS is located so that it can be loaded into the main memory
- **GPT**: GUID Partition Table does the same thing as MBR but is a newer standard that supports more partitions.

During the booting sequence, the bootstrap process contained in the ROM is first started (the dell loading screen). The CMOS setup can then be accessed using the set of keys specified by the system manufacturer.

## Disk Drives

## Microsoft File Structures
**Clusters**: In Microsoft file strutures, sectors are grouped to form clusters. Clusters are typically 512, 1024, 2048, 4096 bytes each. Combining sectors minimizes the overhead of r/w files to a disk and are numbered sequentially starting at 2 (first sector contains the boot record). 

These cluster numbers are called _logical addresses_ while sector numbers are called physical addresses.

**Disk partition**: A partition is a logical drive. FAT16 does not recognize disks larger than 2MB. Partitions can be hidden between partitions on a disk. 

## FAT Disks
### Basics
FAT stands for File Allocation Table. The FAT file structure was originally designed for floppy disks. The FAT databse is typically written to a disk's outermost track and contains filenames, directory names, date and timestamps, starting cluster number and file attributes.

Files are allocated space by clusters. This can result in drive slack where unused space in a cluster between the end of an active file and the end of the cluster. Drive slack includes RAM slack and file slack.

When room runs out in an allocated cluster, the OS allocates another cluster for the file, which adds more slack space on the disk. As files grow, more clusters are chained together and this chain need not be continuous. When the OS stores data in a FAT file system, it assigns a starting cluster position to a file. Data for the file is written to the first sector of the first assigned cluster. 

When this assigned cluster is filled and runs out of room, FAT assigns the next available cluster to the file. If the next available cluster isn't contiguous, the file becomes fragmented.

### Deletion
When a file is deleted in FAT, the directory entry is marked as deleted and the HEX `E5` character replaces the first letter of the filename. Then, the FAT chain for that file is set to 0. 

This means that the deleted data remains in the disk and this area where the files reside becomes unallocated disk space.

## NTFS Disks
New Technology File System (NTFS) was introduced in Windows NT. This was the primary file system for Vista. It provided improvement over the FAT file system by providing more information about a file and giving more control over files and folders. Unlike FAT, this is a journaling file system.

In NTFS, everything written to the disk is considered a file. The first data set is the **Partition Boot Sector** followed by the **Master File Table (MFT)**. It results in much less file slack space and clusters are smaller for smaller disk drives. It also uses *unicode*.

### Master File Table (MFT)
Contains information about all files on the disk, including the system files the OS uses. The first 15 records in the MFT are reserved for system files. Records in MFT are referred to as **metadata**.

All files and filders are stored in separate records of 1024 bytes each. Each record contains file or folder information which is divided into _record fields_ containing metadata. A record field is referred to as an **attribute ID**. 