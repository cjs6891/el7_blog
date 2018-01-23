---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 8: Understanding Windows Operating System Basics"
---

<a href="#Windows Operating System History">8.2 Windows Operating System History</a><br>
<a href="#Windows Operating System Architecture">8.3 Windows Operating System Architecture</a><br>
<a href="#Windows Processes, Threads, and Handles">8.4 Windows Processes, Threads, and Handles</a><br>
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