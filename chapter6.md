# Current Digital Forensics Tools
### Types of Digital Forensics Tools
Digital forensics tools are divided into two major categories: hardware and software:

1. Hardware forensics tools: Range from single purpose tools like  Tableau T35es-R2 SATA/IDE eSATA bridge to complete systems like Digital Intelligence F.R.E.D systems.

2. Software forensics tools: Could be GUI or command line. Could be specialized or general purpose.

## Tasks Performed by Digital Forensics Tools

> **Note**: When testing new tools, follow the guidelines set up by NIST's Computer Forensics Tool Testing (CFTT) program, ASTM International's E2678 standard, the International Organization on Computer Evidence (IOCE). ISO standard 27037 states that Digital Evidence First Responders (DEFRs) should use validated tools.

The functions performed by digital forensics tools are:

1. [Acquisition](#Acquistion)
2. [Validation and Verification](#validation-and-verification)
3. [Extraction](#extraction)
4. Reconstruction
5. Reporting

### Acquistion
The first task in digital investigations. Subfunctions include tasks such as physical data copy, logical data copy, data acquistion format, command line acquisition, GUI acquisition, remote, live and memory acquistions.

While some tools are purely software, some tools like Tableau TD2 are purely hardware. These hardware have built in software for image acquistion. No other device op program is required to make a duplicate drive but additional software will be required to analyze the image.

Also, one could choose:
1. Physical copying of the drive: Making a physical copy of an encrypted drive can result in unreadable data.
2. Logical copying of a disk partition: Best option when dealing with encrypted drives. However, this method requires a live acquistion because the system must be logged into.

Acquistion formats vary from vendor proprietary to raw data. The linux command `dd` creates a bit for bit raw data copy. In larger organizations, remote acquistion is a better option due to geographical separation. AccessData and EnCase both provide support for it.

### Validation and Verification
**Validation**: Way to confirm that a tool is functioning as intended.

**Verification**: Proves that two sets of data are identical using hash values.

**Filtering**: Involves sorting and searching through investigation findings to separate good data and suspicious data.

Forensics tools can use good file hashes and compare them with the file hashes on a suspect's drive to see if they match. It can be used to filter data. Another method for finding suspicious files is by analysing the header of the files. For e.g., a standard inducator for graphics files is the hex value `FF D8`. So, if a `.docx` file has `FF D8` in the header, it could be a graphic file. (Windows 10 does this conversion automatically)

### Extraction
Most challenging of all tasks. The subfunctions used in investigations are data viewing, keyword searching, decompressing or uncompressing, carving, decrypting and bookmarking/tagging. Pre-made wordlists and filtering by extensions are some features to look for in an extraction tool.

### Reconstruction
Re-create a suspect drivr to show what happened during a crime or an incident. The subfunctions are disk to disk copy, image to disk copy, partition to partition copy, image to partition copy.