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

