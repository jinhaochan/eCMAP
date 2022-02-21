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



