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


**WinHex** can generate 