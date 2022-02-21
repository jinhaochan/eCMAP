# eCMAP
Personal notes on eCMAP

## 1. Intro

Goals of Malware Analysis:
1. How does it work (Behaviors)
2. How to detect it (Signatures)
3. How to defeat it and eliminate the threats it creates (Indicators)

Some tools for MA:
1. File Format Analyzers
2. System and Network Monitoring tools
3. Debuggers and Disassemblers
4. Small Gadget tools (Data converters, Decryptors)
5. Virtualization tools
6. IDE

Types of Analysis
1. Static
2. Dynamic

***Important Note: You don't have to understand every single instruction of the malware, but only to meet the 3 questions of the Goals.***

Acquisition Tools:
1. Disk Imaging
    - Belkasoft Acquisition
    - Magnet ACQUIRE
    - FTK Imager
3. Memory Acquisition
    - DumpIt
    - Memdump
    - Belkasoft RAM Capturer
    - Magnet RAM Capturer
5. Others
    - Kroll Artifact Parser and Extractor (KAPE)
    - Rawcopy


### KAPE stuff

Use the KAPE gui

`--tsource`: Source of the drive

`--target`: The targets determine files and directories that will be collected by KAPE, in other words they define the evidence you want to collect.

`--tdest`: Destination folder to store the information collected

e.g:
- `kape.exe --tsource C: --target RegistryHives --tdest Z:\Case1\RegFiles`
    - Gets all registry hives from C drive, and stores them in Z:\Case1\RegFiles
- `kape.exe --tsource C: --tdest Z:\Case2\ --tflush --target EvidenceOfExecution --vss --vhdx CASE2`
    - `tflush` to ensure `tdest` is empty.
    - `vss` to process Volume Shadow Copies
    - `vhdx` to create a VHDX file named CASE2
    - Gets all EvidenceOfExecution
- `kape.exe --tsource C: --tdest Z:\Case3\ --tflush --target FileSystem,EventLogs --vss --vhdx CASE3`
    - Same as above, but collecting FileSystem and EventLogs


## 2. Static Analysis

Two types of Static Analysis
- Basic Analysis
    - File Metadata
    - Strings and other information embedded in it
- Advanced Analysis
    - Source code examination
    - Disassembly

### File Identification and Classification

Identifying file type and obtaining a unique signature of the sample

File can be identified via:
1. File types (Extensions)
2. File Hashes (MD5, Fuzzy Hash, ImpHash)
3. Strings embedded in the file

All files on a computer are either
1. ASCII files (plain text, HTML, XML)
2. Binary files (Structured files)
    - May contain header and footer bytes

![image](https://user-images.githubusercontent.com/7328587/154879915-9af7fbbe-12fc-4afc-98d4-a7ac8e28e5f7.png)

Linux `file` command can identify file types

![image](https://user-images.githubusercontent.com/7328587/154880013-47aec8be-d76f-4931-b479-b1dc4bc6f679.png)

We cannot rely on extensions, as that can be changed without affecting the underlying structure.

The presence of `PE` and `.text` within a file can indicate that it is an executable

### Hashes

![image](https://user-images.githubusercontent.com/7328587/154880154-84f38947-981c-450c-8a5c-312b3553e259.png)

Other hashing functions:
1. FuzzyHash
2. Import Hash
3. Section Hash

We can deal with polymorphic code that changes across systems by using Fuzzy Hashing. Even if a small amount of code has been changed, the similarity will be very high

Fuzzy Hashing segments a file and generates hashes on those segments. Similarity is compared using those hashed segments.

Fuzzy Hashing provides File Similarity.

### Strings

Strings end with a `\0` or `00` or `NUL` or escape sequence character

Strings can be in ASCII or Unicode
- ASCII = 7bit or 128 characters
- Extended ASCII = 8 bits or 256 characters
- Unicode UTF-16 = 16 bits = 2 bytes

Unicode:

![image](https://user-images.githubusercontent.com/7328587/154900509-d780dbfc-5791-40b8-bd3a-d7d5481926c6.png)

When extracting strings, we need to extract both ASCII and Unicode so we don't miss any strings

ASCII strings are either printable or non-printable as output unless inspected in their hex forms
- e.g. newline = '\n' = '\x0A'
- non-printable characters are represented by a `.` dot






## 2. Assembly stuff



## 2. Dynamic Analysis



## 2. Debugging/Disassembly



## 2. Obfuscation techniques



## 2. Static Analysis
