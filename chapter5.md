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

Files larger than 512 bytes are stored outside the MFT. Each MFT record starts with a header identifying it as a resident or non-resident attribute.

### Data Streams
Data can be appended to existing files using data streams. This can obscure valuable evidentiary data. A data stream becomes an additional file attribure and allows the file to be associated with different applications.

### Compression
Provides compression similar to FAT DriveSpace 3. Under NTFS, files, folders or entire volumes can be compressed. Most forensics tool have support for decompression.

### Encryption
Encrypting File System (EFS) was introduced with Windows 2000 and implements a public and private key method of encrypting files, folders or disk volumes. When EFS is used in newer version, a **recovery certificate** is generated and sent to the local windows administrator account. 

*Recovery Key Agent* implements the recovery certificate. Windows admins can recover a key in two ways: through Windows or from `cmd`.

### Deletion
NTFS files deleted at a command prompt function much like FAT files. (The following steps also apply when a user empties the Recycle Bin.) The OS performs the following tasks:
1. The associated clusters are designated as free—that is, marked as available for new data.
2. The `$Bitmap` file attribute in the MFT is updated to reflect the file’s deletion, showing that this space is available.
3. The file’s record in the MFT is marked as being available.
4. VCN/LCN cluster locations linked to deleted nonresident files are then removed from the original MFT record.
5. A run list is maintained in the MFT of all cluster locations on the disk for nonresident files. When the list of links is deleted, any reference to the links is lost.

## Whole Disk Encrytion
Loss of **Personal Identity Information (PII)** from theft is now a major convern. To prevent this loss, whole disk encryption is now provided. These provide features such as preboot authentication, full or pation disk encryption, key management, TPM microchip to generate encryption keys and authenticate logins.

In whole disk encryption, each sector of the drive is encrypted separately. The boot sector is also encrypted. Microsoft BitLocker provides whole disk encryption in Microsoft platforms.

## Windows Registry
**Registry**: A databse that stores hardware and software configuration information, network connections, user preferences and setup information.

The Registry can contain valuable evidence in forensic investigations. `regedit` can be used to edit the Registry.

Some Registry related terminology:

- Registry editor: A Windows utility for viewing and modifying data in the registry.
- HKEY: The Registry is split into categories with the prefix `HKEY_`.
- Key: Each HKEY contains folder referred to as keys. Keys can contain other folders or values.
- Subkey: A key displayed under another key is a subkey, imilar to a subfolder in Windows or File Explorer.
- Branch: A key and its contents, including subkeys, make up a branch in the Registry.
- Value: A name and value in a key.
- Default value: All keys have a default value that may or may not contain data.
- Hives: Specific branches in `HKEY_USER` and `HKEY_LOCAL_MACHINE`. For e.g. hive branches in `HKEY_LOCAL_MACHINE\Software` are `SAM`, `Security`, `Components` and `System`. For `HKEY_USER`, each user account has its own hive link to `Ntuser.dat`.

The registry file locations and purpose is given below:
1. `Ntuser.dat`: User protected storage area. Contains the list of most recently used files and desktop configuration settings.
2. `Default.dat`: Contains the computer's system settings.
3. `SAM.dat`: Contains user account management and security settings.
4. `Security.dat`: Contains the computer's security settings.
5. `Software.dat`: Contains installed programs' settings and associated usernames and passwords.
6. `System.dat`: Contains additional computer system settings.

