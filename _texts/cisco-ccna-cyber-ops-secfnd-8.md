---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 8: Understanding Windows Operating System Basics"
---

<a href="#Windows Operating System History">8.2 Windows Operating System History</a><br>
<a href="#Windows Operating System Architecture">8.3 Windows Operating System Architecture</a><br>
<a href="#Windows Processes, Threads, and Handles">8.4 Windows Processes, Threads, and Handles</a><br>
<a href="#Windows Virtual Memory Address Space">8.5 Windows Virtual Memory Address Space</a><br>
<a href="#Windows Services">8.6 Windows Services</a><br>
<a href="#Windows File System Overview">8.7 Windows File System Overview</a><br>
<a href="#Windows File System Structure">8.8 Windows File System Structure</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>
<a href="#">8.</a><br>

<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>

<a name="Windows Operating System History"></a>
<b>Windows Operating System History</b><br>
Microsoft Windows has been a family of operating systems for personal computers since 1985. In addition to Windows OS for personal computers, Microsoft offers operating systems for servers and personal mobile devices. Originally developed by Microsoft for IBM, MS-DOS was the standard operating system for IBM-compatible personal computers. The latest Windows OS is Windows 10 (the successor to Windows 8), which debuted on July 29, 2015.<br>
<br>
It is interesting to note that although Microsoft operating systems have several vulnerabilities, they are not in the top three, as reported in the 2014 NIST National Vulnerability Database, as shown below.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516661893.png" alt="" style="">
<br>
<pre>
<code>
Note:
Go to https://nvd.nist.gov/ to view the National Vulnerability Database on NIST's web site.
</code>
</pre>
<br>
<a name="Windows Operating System Architecture"></a>
<b>Windows Operating System Architecture</b><br>
The Windows OS has evolved into a robust enterprise computing platform that ranges in use from everyday end user desktop environments to data center-scale server platforms. Its architecture has matured to include features that provide system stability and security. Although Windows is used most often as a desktop computing platform, its server platforms are used extensively in corporate data centers by IT professionals. The operating system’s architecture is common across all its offerings and consists of two major components:<br>
<br>
<ul>
<li><b>User mode:</b> This component manages processes on behalf of system users. It runs with lower privilege so users can’t directly interfere with system level processes. It also provides communication pathways that are known as APIs so that user processes can request access to system level resources.</li><br>
<li><b>Kernel mode:</b> This is where the core processes of the operating system run. Its processes run with the highest level of privilege so it can manage system CPU and memory resources.</li>
</ul>
<br>
The figure illustrates the various architectural components of the Windows OS, and outlines major processes that each component handles.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516668628.png" alt="" style="">
<br>
This is not an exhaustive list of all the elements for each component, but it does outline the major processes and which mode is responsible for each. One of the concepts of the Windows architecture is how processes are treated relative to the mode in which they reside. For example, the user processes appear to occupy their own distinct spaces, which roughly equate to the memory resources the operating system dedicates to each. By design, this prevents a user mode process from accessing the memory space of another process. This mechanism enhances the security and stability of the system.<br>
<br>
Kernel mode processes also operate within the same memory space. However, kernel mode processes are higher privileged functions that cannot be directly accessed by lower privileged user mode processes. Executing processes in the same memory space increases the overall efficiency of the system.<br>
<br>
User mode and kernel mode processes are the Windows subsystems that form the core of the operating system. They are started at system initialization by the Session Manager (Smss.exe). The following registry key will identify the system’s operating mode HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\SubSystems.<br>
<br>
<b>User Mode</b><br>
User mode processes are specific processes initiated or owned by Windows users. These processes operate within the confines of their own memory space or spaces. This prevents one user’s process from accessing another user’s process space or resources. The system does provide mechanisms for one user process to request resources from another. This is handled through specific API calls that are tightly controlled by the system, which prevents a process from arbitrarily impinging on another user’s process space while reducing the potential of system corruption. Remember, user mode processes operate at lower system privileges than kernel mode processes to maintain the separation between the user and kernel mode spaces.<br>
<br>
The types of processes that run in user mode can fall into one of four general categories:<br>
<br>
<ul>
<li><b>Non-service processes:</b> These are fixed processes that support user access to system resources such as logon services and Session Manager. These are not services in a strict sense because they are initiated by user activity and not started by the service control manager.</li><br>
<li><b>Service processes:</b> These are services that run in support of user system requirements; they are not system services that run independent of users, and are generally initiated by the system through the service control manager. Some examples include the Task Scheduler and Print Spooler.</li><br>
<li><b>User applications:</b> As the name implies, these are the processes that are needed to run applications that are initiated by users.</li><br>
<li><b>OS environment support:</b> Windows NT originally shipped with support for Windows, OS/2, and POSIX subsystems to support a Windows design goal of code portability. Recent versions of Windows have dropped support for OS/2 and POSIX in favor of an enhanced version of POSIX that is called Subsystem for UNIX-based Applications (SUA). The OS environment support subsystem manages the subsystem components to use based on what is required by running applications.</li>
</ul>
<br>
User mode applications and services often need to utilize resources that are managed by kernel mode processes. For example, a user mode process may need to write to a file or initiate a network connection. To support user application requirements, Windows can allow a process to switch contexts from user to kernel mode. When the operation requiring the system level resource completes, the system will switch the context back to user mode. This function is handled by a kernel interface layer that manages context switches and will prevent user mode processes direct access to system level resources.<br>
<br>
<b>Kernel Mode</b><br>
A large portion of the Windows OS runs as kernel mode processes. Unlike user mode processes, where each process runs in its own protected memory space, kernel mode processes share the same memory space. This provides speed and efficiency, along with the opportunity for a misbehaving process to potentially impact the entire system. To mitigate this possibility, Windows enforces kernel mode code signing, which means that drivers and critical system files must be signed by a cryptographic key from a public certification authority.<br>
<br>
Major processes that run in kernel mode include the following:<br>
<br>
<ul>
<li>Kernel executive: Performs base operating system services such as I/O, networking, and memory management</li><br>
<li>Kernel: Responsible for managing low level system operations such as thread scheduling and managing system interrupts</li><br>
<li>Device drivers: Handles the requests for I/O to and from connected hardware devices</li><br>
<li>Hardware abstraction layer: HAL is a layer of OS code that handles interaction between the kernel and hardware to account for differences between platforms such as motherboards. This allows the OS to be insulated from the hardware so that the OS itself does not need to adapt to hardware differences. Rather, the HAL handles low level hardware contingencies by translating them to standard OS functions.</li><br>
<li>Window management and graphics subsystem: Implements the GUI and manages graphic functions for Window management and interface controls</li><br>
<li>Ntoskrnl.exe: Windows executive and kernel</li><br>
<li>Hal.dll: HAL module</li><br>
<li>Win32k.sys: Kernel-mode device driver for managing Windows displays and screen output. Also collects input from devices such as the keyboard and mouse</li><br>
<li>Ntdll.dll: System service dispatcher to executive</li><br>
<li>Kernel32.dll: Kernel interface core Windows subsystem</li><br>
<li>Advapi32.dll: Core Windows subsystem</li><br>
<li>User32.dll: User-mode management subsystem</li><br>
<li>Gdi32.dll: Graphical user interface management subsystem</li><br>
</ul>
<br>
<a name="Windows Processes, Threads, and Handles"></a>
<b>Windows Processes, Threads, and Handles</b><br>
A Windows application consists of one or more processes. In the simplest terms, a "process" is an instance of an executing program.<br>
<br>
One or more threads run in the context of the process. A thread is the basic unit the operating system allocates processor time to. A thread can execute any part of the process code, including parts currently being executed by another thread. Each process provides the resources to execute a program and contains the following characteristics:<br>
<br>
<ul>
<li>Runs in virtual address space</li><br>
<li>Consists of executable code</li><br>
<li>Opens handles to system objects</li><br>
<li>A security context</li><br>
<li>A unique process identifier</li><br>
<li>Environment variables</li><br>
<li>A priority class</li><br>
<li>Minimum and maximum working set sizes</li><br>
<li>At least one thread of execution</li>
</ul>
<br>
Each process is started with a single thread that is often referred to as the primary thread. However, the process can create additional threads from any of its existing threads.<br>
<br>
A thread is the entity within a process that can be scheduled for execution. All threads of a process share its virtual address space and system resources. In addition, each thread maintains exception handlers, a scheduling priority, thread local storage, a unique thread identifier, and a set of structures the system will use to save the thread context until it is scheduled. The thread context includes the thread's set of machine registers, the kernel stack, a thread environment block, and a user stack in the address space of the thread's process. Threads can also have their own security contexts, which can be used for impersonating clients. All threads within a process can access its virtual address space. In general, threads cannot access the memory space that belongs to another process. This protects the process from being corrupted by another process.<br>
<br>
Microsoft Windows supports preemptive multitasking, which creates the effect of simultaneous execution of multiple threads from multiple processes. On a multiprocessor computer, the system can simultaneously execute as many threads as there are processors on the computer.<br>
<br>
An object is a data structure that represents a system resource, such as a file, thread, or graphic image. An application cannot directly access object data or the system resource that an object represents. Instead, an application must obtain an object handle, which it can use to examine or modify the system resource. Each handle has an entry in an internally maintained table. These entries contain the addresses of the resources and the means to identify the resource type.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516670055.png" alt="" style="">
<br>
The Windows Task Manager can be used to view the running applications and processes. Here are two ways to start the Windows Task Manager:<br>
<br>
<ul>
<li>Right-click the taskbar and choose the Start Task Manager option.</li><br>
<li>Run the taskmgr command from the Windows command line.</li>
</ul>
<br>
<a name="Windows Virtual Memory Address Space"></a>
<b>Windows Virtual Memory Address Space</b><br>
In modern computing systems, temporary data instructions that are processed by the CPU are stored in the computer’s RAM. Virtual memory is a memory management technique that helps the system execute programs when the environment is running low on RAM memory. Virtual memory temporarily transfers content directly from RAM into the disk storage system. This process helps to compensate for a shortage of RAM.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516801621.png" alt="" style="">
<br>
A process is allocated specific memory addresses from the available virtual address space. The address space for each process is private and cannot be accessed by other processes unless it has permission to open the process for read or write access. All Windows applications and processes have to be granted specific access to various kernel system resources or objects, such as TCP ports and Windows sockets. By design, processes are not allowed direct access to kernel level functions. A process “handle” provides the process with access to a specific kernel level resource. Typically, the process has to release the “handle” in order for other processes to be able to access the same kernel level resource. However, if the process has kernel level access to a function and the handle has granted PROCESS_VM_READ (function) access, other processes can be granted read access to the same kernel level function’s memory space via the ReadProcessMemory function. In addition, if the process has kernel level access to a function and the handle has granted PROCESS_VM_WRITE (function) access, other processes can write to the same kernel level function’s memory space via the WriteProcessMemory function. It should be noted that processes need SeDebugPrivilege in order to open such handles. This potential violation of the process's memory privacy is very common when dealing with malware, and is a technique that is used to insert malicious code with the intent of gaining access to a system.<br>
<br>
A virtual address space does not represent the actual physical location of an object in memory; instead, the system maintains a page table for each process. The page table is an internal data structure used to translate virtual addresses into corresponding physical addresses. Each time a thread references an address, the system translates the virtual address to a physical address.<br>
<br>
Each process on 32-bit Microsoft Windows supports a virtual address space that enables addressing up to 4 gigabytes of memory. Each process on 64-bit Windows supports a virtual address space of 8 terabytes.<br>
<br>
<a name="Windows Services"></a>
<b>Windows Services</b><br>
Microsoft Windows services (formerly known as NT services) will create long-running executable applications that run in their own Windows sessions. These services can be automatically started when the computer boots. These services can be paused and restarted, and do not show any user interface. These features make services ideal for use on a server or whenever you need long-running functionality that does not interfere with other users who are working on the same computer.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516835526.png" alt="" style="">
<br>
Services Control Manager is used to start, stop, pause, resume, and configure the services.<br>
<br>
To start Services Control Manager using the Windows interface, complete these steps:<br>
<br>
<ol>
<li>Click the <b>Start button</b></li><br>
<li>Click <b>Control Panel</b></li><br>
<li>Click <b>Administrative Tools</b></li><br>
<li>Double-click <b>Services</b></li>
</ol>
<br>
To start the Services Control Manager by using a command line, open a Windows command prompt and enter the services.msc command.<br>
<br>
<a name="Windows File System Overview"></a>
<b>Windows File System Overview</b><br>
The NTFS file system is predominantly utilized in most Windows installations today. A file system is a mechanism for organizing files on storage media. The type of media may influence which file system is appropriate to use. For example, optical media typically uses ISO 9660 or UDF. The focus of this section is on disk storage since the operating system and user data are typically stored on hard disk media.<br>
<br>
The following file system options are supported in Windows installations:<br>
<br>
<ul>
<li>File allocation table: FAT is a general-purpose file system that is supported by Windows and other operating systems such as Mac OS X and Linux. Because of its simplicity and portability, it remains a popular file system. It is mostly used as the default format for USB-based storage media such as flash drives. However, it does have some limitations in terms of the file sizes it supports and the maximum partition size, so it is not widely used for hard drives. There are varieties of FAT known as FAT16 and FAT 32. The FAT32 variant is the most commonly used because it is the least restrictive of the variants, less than FAT16.</li><br>
<li>exFAT: The extended version of the FAT file system removes some of the file and partition size limitations of FAT, but is not widely supported on OSs other than Windows and later versions of Mac OS X.</li><br>
<li>Hierarchical file system plus: HFS+ is the file system that is used on Mac OS X-based systems. HFS+ permits file names up to 255 characters in length and supports larger file sizes and drive partitions than the original HFS. It is not supported on Windows platforms without the aid of additional software. However, a Windows system can read data from an HFS-formatted drive.</li><br>
<li>Extended file system: EXT is the default file system on Linux-based installations. Its most current version is EXT4, which has the benefit of maintaining backward compatibility with the previous versions 2 and 3. It is not natively supported on Windows platforms, but a Windows system can read data from EXT-formatted drives with additional software.</li><br>
<li>New technology file system: NTFS is the most commonly used file system in Windows installations. It is natively supported across all versions of Windows operating systems. Mac OS X-based systems can read NTFS partitions but can only write to them by installing additional driver software.</li>
</ul>
<br>
<b>NTFS Basics</b><br>
The NTFS file system provides many features that make it a good choice for both enterprise-scale systems and desktop systems. Some key features are:<br>
<br>
<ul>
<li>Performance and reliability</li><br>
<li>Compatibility</li><br>
<li>Large file and partition size</li><br>
<li>Disk quotas</li><br>
<li>Recovery features</li><br>
<li>Security</li>
</ul>
<br>
It also supports file system encryption to further secure data at rest on the storage media. NTFS supports data access control through security descriptors that include file ownership and permission characteristics for each file. This capability is one reason that NTFS is used so extensively throughout Windows deployments.<br>
<br>
<b>NTFS Volume Structure</b><br>
Formatting a drive with the NTFS file system creates several system files, and the basic structures for reading and writing files and recording their locations.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516836390.png" alt="" style="">
<br>
The partition boot sector occupies the first 16 sectors of the drive. It contains information that points to the system bootstrap instructions and the location of the Master File Table (MFT), which contains an index of all the files on the partition. The last of the 16 sectors is a copy of the boot sector, which can be referenced if the primary is corrupted.<br>
<br>
The MFT contains a file that maps the location of all the files and directories on the partition. NTFS also maintains a mirror or copy of the MFT that can be used if the primary is corrupted. In addition to file location, the MFT stores file attributes such as file name, security descriptor, and time stamps.<br>
<br>
The system files are created when the NTFS volume is first initialized. These files are hidden and are used to store metadata about files, NTFS volumes, logs, and file attribute definitions.<br>
<br>
The file area is where the files and directories are stored.<br>
<br>
<b>NTFS Alternate Data Streams</b><br>
An interesting feature of the NTFS file system is ADS (Alternate Data Streams) technique. Files in NTFS are stored as a series of attributes such as the file name and date stamp. One attribute is called $DATA, which represents the actual file data, and is known as a "data stream." However, NTFS allows you to attach ADSs to a file that provides for various interesting cases. ADSs are primarily used by applications to store additional information about a file.<br>
<br>
ADS data is not readily visible and can be difficult to detect. In fact, recent versions of Windows just started providing tools for identifying files with ADS. A file with ADS can be referenced with the following format:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516836614.png" alt="" style="">
<br>
In the example below, the base file name is myFile.txt. The colon character (:) separates the base file name from the name of the ADS, which is ADStest. To test this feature, you can easily create a file with an ADS as follows:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516836699.png" alt="" style="">
<br>
This command sends the text that is specified in the echo command to an ADS that is associated with a file called myFile.txt. List the files in the directory with the dir command to confirm that the file was created.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516836763.png" alt="" style="">
<br>
Note that the myFile.txt file exists, but the size of the file is 0 bytes. The reason for this is that the data that we entered into the file did not go to the primary data stream which is what the dir command is reporting. It went to an alternate data stream that we called ADStest.<br>
<br>
To see the data that you put into the alternate stream, do the following:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516836830.png" alt="" style="">
<br>
This illustrates an important ADS issue: it is easy to hide things in an ADS. This technique has been leveraged for malicious purposes, so it is important to be aware of it. Recent versions of Windows have added tools to help administrators identify the presence of ADS. For example, the dir command now includes support for the /r parameter, which lists the ADSs that are associated with a file. Consider the following example:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516836893.png" alt="" style="">
<br>
Note that the dir command with the /r parameter is now reporting the presence of the ADS attached to the file. Also note that the byte size of the ADS is also being reported and that the byte size of the file remains 0.<br>
<br>
<a name="Windows File System Structure"></a>
<b>Windows File System Structure</b><br>
In a Windows-based system, every storage device that is connected to a host contains its own file system. The Windows OS can be installed on virtually any drive that is connected to the host. However, it is most often installed on the first physical hard drive that is connected to the host. Hard drives, or any storage media for that matter, are identified with letters.<br>
<br>
The first hard drive is given the letter C, followed by a colon (:). The Windows file system is not case-sensitive by default (although Windows can be configured to support case-sensitivity). Consequently, accessing the C: and c: drives will reference the same device. Additional storage media is given the next sequential letter designation.<br>
<br>
The hard drive on which the Windows OS is installed is typically organized in the following manner:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516838980.png" alt="" style="">
<br>
This is not an exhaustive list of the full Windows file system, but it does include the major directories.<br>
<br>
<ul>
<li><b>Boot:</b> A hidden directory that contains system boot files.</li><br>
<li><b>Logs:</b> As of Windows 10, the directory where event logs are stored.</li><br>
<li><b>PerfLogs:</b> Stores performance logs if this feature is enabled in the operating system.</li><br>
<li><b>Program files:</b> In 64-bit Windows installations, stores 64-bit applications.</li><br>
<li><b>Program files (x86):</b> In 64-bit Windows installations, stores 32-bit applications.</li><br>
<li><b>ProgramData:</b> Directory used to store application-need data. Applications are not able to write directly to this directory, but they can create subdirectories used for their own purposes.</li><br>
<li><b>Users:</b> Directory where users store their data. Each user with an account on the system has a folder that is dedicated to them. Users with standard account privileges are only able to access the data in their assigned directory.<br>
<br>
 - <b>Public:</b> This subdirectory of the Users directory can be shared among all the users of a system. Normally, Windows access controls do not allow users to access data in other users’ directories. However, the public directory allows anyone on the system to store data, making it ideal for sharing data among users.<br>
 <br>
  - <b><i>username</i>:</b> All users with accounts on a Windows host are given areas for their use. The area for each user resides under the Users directory and bears the name of an individual user’s account. This area allows users to privately store their documents and other data since other users are permitted access to their own directory only. Each user’s directory includes a subdirectory that is called AppData. This location is used by applications that need to store things specific to a user, for example a user’s browsing history.
</li><br>
<li><b>Windows:</b> The directory that stores the operating system and its various subsystems.<br>
<br>
 - <b>System:</b> This directory is used to store 16-bit system DLL (dynamic link library) files. In 64-bit Windows installations, this directory is normally empty.<br>
<br>
 - <b>System32:</b> This directory is used to store 64-bit system DLL files in 64-bit Windows installations.<br>
<br>
 - <b>SysWOW64:</b> 64-bit Windows is backward compatible with 32-bit applications. This directory stores 32-bit system DLL files.<br>
<br>
 - <b>WinSxS:</b> This directory stores copies of system DLL files. Often, these files represent older versions of the DLL files that may be required by older applications. The folder name stands for Windows side-by-side because it allows older applications to co-exist with newer ones that require the most current DLL files.
</li>
</ul>
<br>
<b>File System Paths</b><br>
The Windows file system is a hierarchical system in which the root of a disk drive represents the top of hierarchy with multiple levels of directories that can store files or other directories. The term “path” refers to the location of an object, such as a file, which includes the drive and hierarchy of directories that uniquely identify the location of the object. For example, if you use your browser to download a PDF document, the system will store the document in the downloads directory of your user directory, which resides on the disk drive on which the operating system is installed—usually the C: drive.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516840060.png" alt="" style="">
<br>
Each element of the path is separated by a backslash (\) character. Note that the path starts with a reference to the disk drive, followed by the series of directories that you must traverse to get to the file, and lastly, the file name. This is known as a “fully qualified” path because it includes all the information that is needed to identify the specific location of the file.<br>
<br>
Windows also supports relative paths to identify the location of an object. For example, when you open the command line window, the system puts you in your user directory. The command prompt itself specifies the directory that you are in. To locate the PDF file that you downloaded with your browser, you only need to specify the location of the file relative to your current location. In the example that follows, the user wishes to copy the PDF file from the downloads directory to the documents directory:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516840154.png" alt="" style="">
<br>
Note that with the relative notation, the leading backslash is omitted since that would represent the root of the drive. Because the user was already in their user directory, and both the downloads and documents directories reside in the user directory, only those directories that need to be referenced in the command, along with the file to be copied.<br>
<br>
<b>File Naming Conventions</b><br>
File names in the Windows file system consist of two components:<br>
<br>
<ul>
<li>Base file name</li><br>
<li>File extension</li>
</ul>
<br>
The maximum number of characters that can be used to express a file path is 256 characters. Four additional characters are included in fully qualified names (bringing the total maximum number of characters that is supported to 260), which includes the drive letter, the colon that follows it, the backslash that represents the root of the drive and a null character at the end of the file name to terminate the file name.<br>
<br>
However, it should be noted that Microsoft provides the ability to increase the MAX-PATH length within Windows 10.<br>
<br>
The unicode version of Windows file IO functions allow for longer paths, approximately 32,767 characters. By utilizing the extended paths, files and directories can be hidden in such a way that some tools are unable to find them. The Windows cmd shell only supports ANSI file paths. Any tool that uses ANSI file IO functions or fails to support \\?\C:\ paths cannot access the directories and files that exist after the first 260 path characters.<br>
<br>
In a Windows file name, a period or dot character (.) is used to separate the base file name from the extension. However, most other punctuation characters cannot be used in a file name because they have special meanings to the Windows command interpreter.<br>
<br>
In Windows, the file extension is used to identify an association between a file and the application that is needed to open or execute the file. The list below contains examples of common file extensions and the applications with which they are typically associated:<br>
<br>
<ul>
<li><b>.exe:</b> Executable file</li><br>
<li><b>.txt:</b> Text file</li><br>
<li><b>.rtf:</b> Rich text file</li><br>
<li><b>.pdf:</b> Portable document format</li><br>
<li><b>.bmp:</b> Bitmap graphic image</li>
</ul>
<br>
The list is just a small sample of file extensions. You will mostly see them expressed with three characters but that is not a requirement. File extensions are mapped in the operating system to specific applications. Often, a file format that is used by an application is assigned a unique icon by the application when the application is installed. It registers the extension association so that when a user double-clicks the icon that represents the file, the operating system will know which application to launch. Users can change these mappings but it is not done frequently.<br>
<br>
<b>File Properties, Attributes, and Permissions</b><br>
File properties are essentially details about a file, including the file’s modification and creation date, file size, and other meta information about the file. Specific information that is stored as a property of a file can differ by file type. For example, an audio file will allow you to add a rating, but that same attribute is not supported for text files. Some properties can be modified depending upon the type of file and its ownership permissions.<br>
<br>
Another aspect of a file’s properties is file ownership, which allows Windows to enforce a degree of access control so that only the user that creates a file and the administrator initially have permission to access the file. File owners and administrators can grant permission to others. Note that to implement Windows file permissions, you must be using the NTFS file system.<br>
<br>
To view or modify the ownership and permission properties of a file, right-click the file, choose Properties, and then select the Security tab.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516840948.png" alt="" style="">
<br>
Currently, the administrator account (represented by the single person icon) and the members of the administrators group (represented by the two-person icon) can access the file. The system user that is listed is a special account that is used by the operating system. By default, the system user is granted full control to every file. You can add users to the list to give others access to the file by clicking the Edit button under the Group or user names box.<br>
<br>
In the figure below, the user has added the Users group to the file properties.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516841097.png" alt="" style="">
<br>
Once you have decided which users should have access to the file, you can specify the permissions to grant each user or user group. The permissions are defined below:<br>
<br>
<ul>
<li><b>Read:</b> Allows users to view and list files and subdirectories.</li><br>
<li><b>Write:</b> Allows users to write to files or add files and subdirectories to folders.</li><br>
<li><b>Read and execute:</b> Allows users to view the contents of files, list files and subdirectories, and execute files if they are of an executable type. The read and execute permission does not grant permission to write to the file.</li><br>
<li><b>Modify:</b> Permits users to read and write to files and subdirectories and grants permission to delete files and directories.</li><br>
<li><b>Full control:</b> Permits reading, writing, modifying, and deleting files and subdirectories.</li>
</ul>
<br>
You have the ability to explicitly allow or deny file/directory permissions by checking the boxes in the appropriate column. If a specific permission level is not set, the deny permission will take precedence.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516841308.png" alt="" style="">
<br>
Another aspect of Windows file properties is file attributes, which is metadata associated with every file. File attributes are used to define how the system, applications, or users can interact with a file. You can view many of the attributes that are associated with a file by right-clicking the file and selecting Properties from the context menu.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516841423.png" alt="" style="">
<br>
Note the attributes section that is near the bottom of the window. Click the Advanced button to expose more attributes.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516841473.png" alt="" style="">
<br>
The following is a complete list of available file attributes:<br>
<br>
<ul>
<li><b>Archive:</b> Used to mark files for backup</li><br>
<li><b>Compressed:</b> Indicates that the data in a file is compressed</li><br>
<li><b>Device:</b> Reserved for system use</li><br>
<li><b>Directory:</b> Marks the object as a directory rather than a file</li><br>
<li><b>Encrypted:</b> Indicates that the file or directory is encrypted</li><br>
<li><b>Hidden:</b> Hides the file or directory from standard directory listings</li><br>
<li><b>Normal:</b> Identifies files that have no other attributes set. It is only valid when used alone</li><br>
<li><b>Not Indexed:</b> The file or directory is not indexed by the content indexing service.</li><br>
<li><b>Offline:</b> File data is not available because it has been physically moved to offline storage; used by remote storage applications.</li><br>
<li><b>Readonly:</b> Applications can read the file data but cannot write or delete it.</li><br>
<li><b>Reparse Point:</b> A file that is a symbolic link</li><br>
<li><b>System:</b> A directory that is reserved for use by the operating system</li><br>
<li><b>Temporary:</b> Indicates that the file is used for temporary storage. Typically, the application using the file deletes it when the file handle is closed.</li><br>
<li><b>Virtual:</b> Reserved for system use.</li>
</ul>
<br>
There are several mechanisms for setting or viewing file attributes. For example, from the file properties box, you can view or modify several, but not all, file attributes. You can also view and modify file attributes from the command line with the attrib command. The help text from the command line example that follows shows the various options that you can use with the attrib command:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516842078.png" alt="" style="">
<br>
Not all the attributes are available for viewing or change with this command because some attributes are only modified by applications or the system. In the example that follows, the attrib command is used to set the read only attribute on a file:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516842157.png" alt="" style="">
<br>