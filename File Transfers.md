## Windows File Transfer Methods

The term `fileless` suggests that a threat doesn't come in a file, they use legitimate tools built into a system to execute an attack. This doesn't mean that there's not a file transfer operation. As discussed later in this section, the file is not "present" on the system but runs in memory.

> A .lnk file is a Windows shortcut, a small file that acts as a pointer or link to another file, folder, application, or network location, allowing quick access without navigating to the original item.


The `Astaroth attack` generally followed these steps: 
1. A malicious link in a spear-phishing email led to an LNK file. 
2. When double-clicked, the LNK file caused the execution of the [WMIC tool](https://docs.microsoft.com/en-us/windows/win32/wmisdk/wmic) with the "/Format" parameter, which allowed the download and execution of malicious JavaScript code. 

>(The WMI command-line (WMIC) utility provides a command-line interface for Windows Management Instrumentation (WMI). WMIC is compatible with existing shells and utility commands.)

3. The JavaScript code, in turn, downloads payloads by abusing the [Bitsadmin tool](https://docs.microsoft.com/en-us/windows/win32/bits/bitsadmin-tool).

>[Dynamic Link Libraries (DLLs)](https://www.lenovo.com/in/en/glossary/dynamic-link-library/) are shared files in Windows and OS/2 containing code, data, or resources that multiple applications can use simultaneously

![[Pasted image 20260126000424.png]]

