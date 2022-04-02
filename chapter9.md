## Digital Forensics Analysis and Validation
### Introduction
**Scope creep**: Investigation is extended in scope due to newfound evidence. It has become more common because investigations increasingly require more detailed examinations before the trial to fend off attacks from the defence attorneys.

As a standard practice, the following steps should be followed when approaching a digital forensics investigation:

1. Use media that have been formatted  and checked for viruses. When disk to disk forensic copying is used, the original drive reformats the target drive to the same configuration. Wiping media can be done using various tools such as X-Ways Security, Digital Intelligence PDWipe etc.

2. Inventory the hardware and make notes on the condition of the system when seized i.e. document everything.

3. Remove the original drive from the computer and check the date and time values in the system's CMOS.

4. Record how the data is extracted form the suspect drive i.e. the software used to create the bit stream image and store the MD5 or SHA1 hash.

5. List all files and folders on the drive.

6. Examine the contents of all data files in all folders, starting at the root directory except for cases where the scope is defined by a warrant.

7. Use tools such as OSForensics Password Recovery for password protected files.

8. Identify the function of every executable whose hash does not match the known OS values. 

9. Document everything thoroughly as you go through.


### Validating Forensic Data

<hr>
<p align="center">Using Hexadecimal Editors</p>


**WinHex** can generate hashes of files. Take for example, a file called `test.docx`. To generate its hash:

1. Right click WinHex and select open as administrator.
2. File → Open. Select the file.
3. Tools → Compute Hash. Select `MD5(128 bit)`.
4. Copy and use the hash value as you like.
5. Autopsy can compute hashes of specific sectors of the disk. This can be used to compare the hash generated in the previous step.

**Block wise hashing**: Using hashes of secotrs from the original file to look for known file fragments. For e.g. say you're trying to recover a file from the suspect's computer but recovery shows no evidence of it. Block wise hasing can be used to match partial fragments, thus confirming that the file was stored on the suspect's computer.

<hr>
<p align="center">Using Forensics Tools</p>

Commercial digital forensics tools have built in validation features for image acquisition. For e.eg. FTK Imager gives an option for generating hashes of all files when cloning the disk (when exporting image in both `.E01` and `.S01` format).This can then be used to verify that the image file has not been corrupted when loading the image into another tool.

## Data Hiding Techniques
**Data Hiding**: Changing or manipulating a file to conceal information.

1. **Using the OS**: One common method is to change the extension of the file. However, forensics tool check the file headers and flag the file for further analysis if any discrepancy is found.
2. **Hiding partitions**: Paritions can be hidden in windows using the `diskpart remove letter=X` command and can be unhidden using the `diskpart assign letter=X`. To detect if this technique has been used, simply try to account for all the space. Any big gaps between two partitions is generally a hidden partition. While WinHex can view hidden partitions in live mode, Autopsy can only do so for disk images.
3. **Marking bad clusters**: THis technique is used in FAT file systems. Using older tools such as Norton DiskEdit, the FAT table can be edited and good clusters can be marked as bad clusters, thus allowing data hiding.
4. **Bit shifting**: Bit shifting changes data from readable code to data that looks like binary executable code. For example, taking a file and left shifting the bits by 1 and right shifting the bits when the file needs to be viewed. The counter is very simple: even after bit shifting, the hash values remain identical.

## Steganalysis Methods
The term **steganography** comes from the greek word for hidden writing. The following steganalysis methods are available:

1. Stego only attack: Used when only the stagonagrphic image is available. 
2. Known cover attack: Used when the cover media, i.e. the original file with no steganography is available.