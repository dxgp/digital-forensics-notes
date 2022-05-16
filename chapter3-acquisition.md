# Data Acquisition
## Image Acquisition Formats
### Raw Format
Because creating bit by bit copies is not practical for evidence presentation, OSes made it possible to write bit stream data to files (like the unix `dd`) command.

The advantages include fast transfers, ability to iggnore minor errors, wide support. Disadvantages include high storage usage, and difficult collection of data from bad hard drive sectors.

### Advanced Forensic Format (AFF)
The advantages offered by the open source AFF are:

1. Capable of producing compressed or uncompressed image files.
2. No size restriction for disk to image files.
3. Space in the image file or segmented files for metadata.
4. Simple design with extensibility.
5. Open source for multiple computing platforms and OSes.
6. Internal consistency checks for self-authentication.

## Acquisition Methods
**Static acquisitions**: Done on computers that werer seized during a police raid. 
**Live acquisitions**: The computer is powered on and logged in during live acquisitions.

In both types of acquisitions, data can be collected with three methods:
1. **Disk to image file**: Most common method and offers the most flexibility. One or more copies of the suspect drive can be made. These copies are bit for bit replications of the original drive. In addition, many commercial forensics tools can read the produced image file.
2. **Disk to disk copy**: Used when a disk-to-image file is not possible due to hardware or software restrictions. In such cases, data is copied from an older disk to a newer disk with adjustments made for the target disk's geometry so that the copied data matches the original suspect's drive. Tools like *EnCase* and *X_Ways Forensics* use this method.
3. **Logical disk to disk**: A logical acquisition captures only specific files of interest to the case or specific types. A sparse acquisition is similar but only collects fragments of deleted data. This is advisable only when the target disk is extremely large or when time constraints are in place.

Due to the nature of the work, there must be a contingency plan in place in case of hardware or software faliures. 

Also, tools vary in a variety of ways. For e.g. some tools don't copy the data in the **host protected area (HPA)** of the disk. Consider using tools such as Belkasoft, ILOokIX IXImager, Image MASSter Solo or X-Ways Replica in cases where data in the HPA is required.

## Validating Data Acquisitions
Validating data acquisitions requires using a hasing algorithm utility.

Current distributions of Linux include two hashing utilities: `md5sum` and `sha1sum`. However, Windows has no in-built hasing algorithms. However, third party hexadecimal viewing tools such as X-Ways WinHex or Breakpoint Software Hex Workshop offer these hashing utilities.

Different programs have different in-built validation facilities. For e.g. Autopsy uses MD5 for image validation (however the image must be in AFF or Expert Witness Compression format as the metadata of these files contain the original hash).

## RAID Data Acquisitions
Redundant array of independent disks (RAID) is a computer configuration involving two or more physical disks. 

There are four major configurations of RAID:

1. **RAID 0 (Striping)**: Multiple disks are viewed logically by the system as one large disk. Data storage is split equally among all RAID disks. The advantage is its increased speed and data storage capability. However, the major disadvantage is its lack of redundancy because if a disk fails, no additional copies of the list data exist.
2. **RAID 1 (Mirroring)**: Designed for data recovery in the event of a faliure. The contents of multiple disks are identical for redundancy. The major disadvantage is that the storage cost is immediately doubled.

3. **Raid 2 (Bit level striping)**: Data is written to disk at the bit level with one disk using ECC to verify if the write is successful. However, because of the bit level operations, RAID 2 is slower.

4. **Raid 5 (Block level striping with dedicated parity)**: Each disk contains parity data. If a disk has data faliure, the parity on the other disks rebuilds the corrupt data automatically when the failed drive is replaced.

Several forensics tools have support for RAID disks. This includes *Guidance Software EnCase, X-Ways Forensics, AccessData FTK, Runtime Software, R-Tools Technologies*.

## Remote Acquisition Tools
Some tools that support remote acquisition are *EnCase Enterprise, R-Tools R-Studio, WetStone US-LATT PRO, F-Response*.