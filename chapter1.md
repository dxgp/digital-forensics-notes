# Chapter 1: Understanding Digital Forensics
## Introduction
In October 2012, ISO 270037 "Information Technology -- Security Techniques -- Guidelines for identification, collection, acquisition and preservation of digital evidence" was passed.

**Federal Rules of Evidence (FRE)**: Signed into law in 1973 was created to standardise evidence procedures. 

**FBI Computer Analysis and Response Team (CART)**: Formed in 1984 to handle the increase in cases that required processing digital evidence.


### History of Digital Forensics
1. In 1980s, general purpose OSes such as DOS became available. Tools in this period were created by government agencies like the IRS and were written in C or assembly. These tools were not available to the general public.
2. In the mid 1980s, the tool *XTree Gold* became available to the genral public. Norton DiskEdit soon followed.
3. By early 1990s, *International Association of Computer Investigative Specialists (IACIS)* introduced training for digital forensics software. However, no GUI tools were available until *Expert Witness* was introduced for Macintosh.
4. Now, a lot of excellent tools such as AccessData Forensic Toolkit (FTK) are available to the general public.

**Case law**: In cases where statutes or regulation do not exist, case law allows legal counsel to apply previous similar cases to current ones in an effort to address ambiguity in laws.

## Preparing for Digital Forensics Investigations
### Public Sector Investigations
> **The Fourth Amendment**: The right of the people to be secure in their persons, houses, papers and effects, against unreasonable searches and seizures, shall not be violated, and no Warrants shall issue, but upon probable cause, supported by Oath or affirmation, and particularly describing the place to be searched, and the person or things to be seized.

A criminal case follows three stages: the complaint, the investigation and the prosecution. Once the complaint is filed, the *police blotter* is checked to find any similar crimes and discover patterns. Whether or not a police officer is capable of handling digital evidence is determined whether the offices falls into one of two categories: **Digital Evidence First Responder (DEFR)** i.e. skilled in taking precautions to preserve digital evidence or a **Digital Evidence Specialist (DES)** i.e. skilled in analyzing the acquired data.

As an examiner assigned to a case, the following steps must be followed:
1. Assess the scope of the case, which includes the devices's OS, hardware and peripheral devices.
2. Determine whether resources are available to process all the evidence. Determine whether you have the tools to analyze the evidence.
3. Once all the resources are gathered, the next task is to delegate, collect and process the information related to the complaint.
4. After collecting the evidence, the information is turned over to the prosecutor. 

### Private Sector Investigations
**Authorized requester**: A person within an organization that has the power to initiate investigations.


As a digital investigator and forensics professional, you’re expected to maintain honesty and integrity. You must conduct yourself with the highest levels of integrity in all aspects of your life. Any indiscreet actions can embarrass you and give opposing attorneys opportunities to discredit you during your testimony in court or in depositions.

When collecting evidence, follow the search and seizure procedures that government agents might have to follow as there is always a possiblity that the case might turn into a criminal investigation.

The **silver-platter doctrine** used to allow a civilian or private-sector investigative agent to deliver evidence obtained in a manner that violated the Fourth Amendment to a law enforcement agency. However, this doctrine was ruled unconstitutional in 1960.

## Approaching a Case
### Taking a Systematic Approach
The following steps must be followed when conducting a digital investigation:
1. **Initial assessment**: Make an initial assessment about the type of case you're handling.
2. **Initial design**: Determine a preliminary design or approach to the case i.e. outline the general steps you need to follow to investigate the case.
3. **Checklist**: Create a detailed checklist and refine the general outline by creating a detailed checklist that includes the steps that need to be followed along with a time estimate for each step.
4. **Required resources**: Determine the resources required i.e. list the software you plan to use.
5. **Obtain evidence**: Obtain and copy an evidence drive i.e. make a forensic copy.
6. **Risk identification**: Identify the risks i.e. list the problems you normally expect in the type of case being handled. This is known as a *standard risk assessment*.
7. **Risk mitigation**: Mitigate or minimize the risks i.e. take necessary precautions to overcome the identified risks.
8. **Testing**: Test the design by reviewing the decisions already made by you. This also includes drive verification using hashes.
9. **Analysis and recovery**: Analyze and recover the digital evidence using the software tools gathered.
10. **Investigation**: Investigate the data you have recovered including files, deleted files, emails, web history etc.
11. **Reporting**: Complete the case report by writing a detailed report that includes the stpes followed and a summary of findings.
12. **Critiquing**: Critique the case by performing a self assessment or peer review. Identify any mistakes made by you and how they can be avoided in the future.

Consider the following example:
> Manager Steve Billings has been receiving complaints from customers about the job performance of one of his sales representatives, George Montgomery. George has worked as a representative for several years. He’s been absent from work for two days but hasn’t called in sick or told anyone why he wouldn’t be at work. Another employee, Martha, is also missing and hasn’t informed anyone of the reason for her absence. Steve asks the IT Department to confiscate George’s hard drive and all storage media in his work area. He wants to know whether any information on George’s computer and storage media might offer a clue to his whereabouts and job performance concerns. After talking to George’s co- workers, Steve learned that George has been conducting a personal business on the side using company computers.

So the initial case assessment would be:
1. Situation: Employee abuse of resources
2. Nature of the case: Side business conducted on the company computer.
3. Specifics of the case: The emplyee is reportedly conducting a side business on his company computer that involves registering domain names for clients ans setting up their web sites at local ISPs. Co-workers have complained that he's been spending too much time on the side business, not paying enough attention to his assigned tasks.
4. Type of evidence: Small capacity USB drive connected to a company computer.
5. Known disk format: NTFS
6. Location of evidence: One USB drive recovered from the employee's assigned computer.

Next, the following general steps must be followed:
1. Acquire the USB drive from the IT department, which initially acquired the evidence.
2. Complete an evidence form and establish a chain of custody.
3. Transport the evidence to your digital forensics lab.
4. Place the evidence in an approved secure container i.e. a safe with access limited to authorized personnel.
5. Prepare your forensic workstation.
6. Retrieve the evidence from the secure container. 
7. Make a forensic copy of the evidence drive.
8. Return the evidence to the secure container.
9. Process the copied evidence drive with your digital forensics tools.

An **evidence custody form**, also called a chain-of-evidence form, that helps us document what has and has not been done with the original evidence and forensic copies of the evidence. An evidence custody form must contain the following information:

1. Case number
2. Investigating organization
3. Investigator
4. Nature of case
5. Location evidence was obtained
6. Description of evidence
7. Vendor name
8. Model number or serial number
9. Evidence recovered by
10. Date and time
11. Item #/Evidence processed by/Disposition of evidence/Date/Time
12. Page

To store the evidence, the following points must be kept in mind:
1. When gathering products to secure the computer evidence, make sure they can be safely used to store computer components.
2. Be cautious when handling any computer component to avoid damaging the component or coming into contact with static electricity, which can destroy digital evidence.
3. Consider using an antistatic pad with an antistatic wrist strap.
4. The evidence must be placed in a well padded container as it prevents damage to the evidence while being transported to the secure locker.
5. Save discarded har drive boxes, antistatic bags and packing material for computer hardware when you or others acquire computer devices.
6. Use evidence tape with your name to seal all components to prove that the chain of custody is not violated.
7. If an entire computer is to be transported, place new disks in disk drives to reduce possible drive damage while you're moving it.

## Employee Termination Cases
### Internet Abuse Investigations
The following are the requirements for investigating internet abuse investigations:
1. The organization's Internet proxy server logs.
2. Suspect computer's IP address obtained from the organization's network administrator.
3. Suspect computer's disk drive.
4. Preferred digital forensics analysis tool.

The following steps should be followed:
1. **Drive examination**: Use standard digital forensics techniques and procedures to perform the disk drive examination.
2. **Web history**: Search for and extract all web page URLs and other associated information.
3. **Server logs**: Contact the network firewall administrator and request a proxy server log of the suspect computer's network IP address for the dates of interest. 
4. **Comparison**: Compare the data obtained from the server logs with the forensically obtained data to confirm that they match. If they don't, the allegations must be dismissed.
5. **Collection**: Continue the forensic analysis to extract all remaining data.


### E-mail Abuse Investigation
E-mail investigations typically include spam, inappropriate and offensive message content, and harassment or threats. 

The following are the requirements for an email abuse investigation:
1. An electronic copy of the offending email that contains the message header data.
2. If available, email server log records.
3. For e-mail systems that store users' messages on a central server, access to the central server is required.
4. For email systems that store users' messages on a computer as an Outllok `.pst` or `.ost` file, access to the computer is required.

The following steps must be followed:
1. Use standard forensic analysis techniques and procedures on the Outlook `.pst` or `.ost` files.
2. For server based email data files, contact the email server admin and obtain an electronic copy of the suspect's and victim's email folder or data.
3. For web based email, investigations, search for internet keywords to extract all related email address information.
4. Examine the header data of all messages of interest to the investigation.

### Attorney Client Privilege Investigations
The following basic steps must be followed in an ACP case:
1. **Initiation memo**: Request a memo from the attorney directing you to start the investigation. The memo must state that the investigation is privileged communication and list your name and other associates' names assigned to the case.
2. **Keywords**: Request a list of keywords of interest to the investigation.
3. **Beginning investigation**: After receiving the memorandum, initiate the investigation and analysis. Any findings before the memo are subject to discovery by the opposing attorney.
4. **Bit-stream copies**: For drive examinations, make two bit stream images, using a different tool for each image. This is advisable because every tool has its strengths and weaknesses. If large enough drives are available, make *uncompressed* bit stream images.
5. **Hash values**: Verify the hash values on all files on the original and re-created disks or its image file.
6. **Drive examination**: Methodically examine every portion of the drive i.e. both allocated and unallocated disk areas and extract all data.
7. **Keyword searches**: Run keyword searches on allocated and unallocated disk space followed by verification that the disk contains information related to the case.
8. **Data formats**: For Windows OSes, use speciality tools to analyze and extract dataform the Registry. For e.g. AccessData Registry Viewer. For binary and CAD files, find the correct program and if possible, take printouts of the binary data.
9. **Unallocated data**: For unallocated data recovery, use a tool that removes or replaces non-printable data.
10. **Consolidate**: Consolidate all recovered data from the evidence bit-stream image into well organized folders and subfolders. Storre the recovered data output using a logical and easy to follow storage method for the attorney or paralegal.

**Note**: All written communication with the attorney must be minimized and telephone must be used whenever possible. Any documentation written to the attorney must contain a header stating that it's *"Privileged Legal Communication -- Confidential Work Product"*. Also, providing assistance to the attorney or paralegal in analyzing the data is necessary.

### Industrial Espionage Investigations
All suspected industrial espionage investigations must be treated as criminal investigations. When planning an industrial espionage investigation, the following staff is required:

1. The digital investigator responsible for forensics examinations.
2. The technology specialist who is knowledgeable about the suspected compromised technical data.
3. The network specialist who can perform log analysis and set up the network monitors to trap network communication of possible suspects.
4. The threat assessment specialist who's familiar with federal and state laws and regulations related to International Traffic in Arms Regulations (ITAR) or Export Administration Regulations (EAR) and industrial espionage.

Remember the following guidelines when initiating an industrial espionage investigation:

1. Determine whether this investigation involves a possible industrial espionage incident 


