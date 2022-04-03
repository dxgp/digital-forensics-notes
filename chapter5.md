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

When room runs out in an allocated cluster, the OS allocates another cluster for the file, which adds more slack space on the disk. As files grow, more clusters are chained together and this chain need not be continuous.