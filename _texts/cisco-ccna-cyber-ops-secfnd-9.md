---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 8: Understanding Windows Operating System Basics"
---

<a href="#History and Benefits of Linux">9.2 History and Benefits of Linux</a><br>
<a href="#Linux Architecture">9.3 Linux Architecture</a><br>
<a href="#Linux File System Overview">9.4 Linux File System Overview</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>
<a href="#">9.</a><br>

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
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>

<a name="History and Benefits of Linux"></a>
<b>History and Benefits of Linux</b><br>
Linux traces its roots back to Unix, which was developed by AT&T labs as an operating system that was meant to improve software development. It did so by addressing problems with existing operating system platforms that traditionally challenged developers, such as file management and portability. However, because Unix was owned by AT&T, using Unix meant having to pay licensing fees and users were restricted by the terms of the license. Nonetheless, it was widely used and well known to developers and computer scientists because licensing fees were made very favorable to certain institutions such as universities, and it was a highly portable and efficient platform in its day.<br>
<br>
Linux was started by Linus Torvalds as a project to create a Unix-like environment that he could run on his personal home computer because the systems at the university that he attended ran Unix. His implementation of Unix was completely re-written and he made it openly available to others with very limited restrictions under the terms of GNU public licensing or GPL guidelines. GPL allows the free distribution of software, and grants anyone the ability to modify the code if source code of the modification is made publicly available.<br>
<br>
This model helped propel Linux development because code was visible to a wide audience and improvements were made public as well. Linux quickly became a robust operating system platform with large communities of users to support others at no cost.<br>
<br>
<b>Benefits of Linux</b><br>
The open source nature of Linux makes it a highly cost-effective option. In addition to the operating system being freely available, much of the software that you can run on it is freely available. Virtually any application can be found of comparable quality to commercial counterparts.<br>
<br>
The popularity of Linux means that there are plenty of resources available to help in the form of user communities, blogs, and discussion forums. There are also many resources that can be found online, including documentation, training, and videos to further extend the support options.<br>
<br>
The Linux operating system is very stable and capable of running enterprise-scale production applications.<br>
<br>
<a name="Linux Architecture"></a>
<b>Linux Architecture</b><br>
At the core of every Linux installation is the Linux kernel, the heart of the operating system. However, beyond the kernel there are applications that interface with the kernel to get things done. Over time, packages of Linux software have evolved that are maintained by like-minded users or communities. These packages are all based on Linux, but they may favor certain types of software components, desktop environments, or services. These packages have come to be known as distributions, and there are many to choose from. Some of the more common distributions include the following:<br>
<br>
<ul>
<li>Red Hat</li><br>
<li>Debian</li><br>
<li>Mandriva</li><br>
<li>CentOS</li><br>
<li>Ubuntu</li>
</ul>
<br>
These examples are all based on Linux, but their primary difference is the software that comes packaged with each. Usually, the choice of one over another is based on preference. Some may be better suited for enterprise applications, while others create friendlier desktop environments.<br>
<br>
The Linux operating system is built on the concept of abstractions that are organized in a sequence of layers. The term "abstraction" in this context means that the details of how one layer will work are hidden from the other layers. Layers present interfaces that other layers can communicate with to perform tasks or request services. This layered architecture provides certain benefits: it simplifies software design because developers do not have to worry about how to interact with aspects already handled by other software components. The software simply requests what it needs from the other components and it is up to that component to perform the requested task and return a result to the calling component.<br>
<br>
Access to the inner workings of a layer is limited to what the layer’s interface provides for communication. A component cannot directly manipulate what is under the control of another, which prevents users or higher-level software from potentially corrupting lower-level operations. For example, users cannot directly access hardware functions. Instead, a user would execute a command from the command line interface to move or copy a file, for example. The commands take care of performing the requested operation through the lower-level structures that are in charge of communicating with the disk drive.<br>
<br>
The high-level architecture of the Linux operating system consists of three primary components or layers:<br>
<br>
<ul>
<li>user space</li><br>
<li>kernel space</li><br>
<li>hardware</li>
</ul>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517152968.png" alt="" style="">
<br>
<b>User Space</b><br>
User space describes the system memory made available to run user processes. A user process can be any of the following:<br>
<br>
<ul>
<li>an application that is initiated by a user</li><br>
<li>a background process that is initiated by a user application</li><br>
<li>services</li><br>
<li>the graphical desktop environment</li><br>
<li>commands that run from a shell</li>
</ul>
<br>
User space processes are maintained in a separate memory space to prevent user processes from interfering with kernel processes. Interaction between the kernel and user space is performed through function calls and programming interfaces rather than allowing user processes to directly control anything in the kernel. Because of this separation, user processes that misbehave will typically not impact the rest of the system as the kernel maintains control of each process to prevent corruption of critical system functions.<br>
<br>
<b>Kernel Space</b><br>
The kernel is the core of the Linux operating system. A section of the system’s main memory is reserved for the kernel to use. The kernel manages all the system resources.<br>
<br>
<ul>
<li>determines which processes can access the CPU</li><br>
<li>manages the memory allocations for each running process</li><br>
<li>is the interface between the user-space processes and the hardware.</li>
</ul>
<br>
<b>Kernel/User Relationship to the Hardware</b><br>
System hardware is insulated from direct manipulation by user processes because the kernel acts as the intermediary between the two. The kernel communicates with system hardware through device drivers. Maintaining this separation between user processes and hardware prevents user processes from potentially damaging the system in the event of a misbehaving process. However, users with sufficient privileges on the system can still cause damage by erasing critical files, for example.<br>
<br>
The kernel is also responsible for managing multitasking by deciding which processes can access the CPU, a function that is called scheduling. When a user process is given time on the CPU, the kernel is responsible for mapping the virtual address space of the process to the physical address space of the main memory.<br>
<br>
In addition, the kernel must load and unload special memory, which are called registers, within the CPU. These registers are used for extremely fast computation and storage. However, since each user process must be kept separate by the kernel, a function that is called context switching is implemented to temporarily unload the registers until the next time that process needs the CPU.<br>
<br>
<a name="Linux File System Overview"></a>
<b>Linux File System Overview</b><br>
Linux maintains a fairly standard file system structure, making navigation around different hosts easier even if they are running different Linux distributions. There are some minor differences between distributions, but navigating around the differences can be easily overcome once you familiarize yourself with the basic structure, as shown in the figure below.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517153807.png" alt="" style="">
<br>
In Linux, the file system structure begins with the root directory, which is expressed with a single forward slash (/) character. Everything else in the file system, including other drives or peripheral devices, will reside somewhere below the root.<br>
<br>
Different Linux distributions may reserve subdirectories for you to mount drives or other storage media. For example, if you mount a CD-ROM drive in an Ubuntu installation, it will be mounted in a directory that is called /media by default. Other distributions may include a directory that is called /mnt for mounting storage media. You can also mount storage media anywhere that you want as long as your user account has permission to write to the directory where you want to mount it. The location used to mount storage media is known as the “mount point.”<br>
<br>
Different Linux distributions may have slightly different file system structures, but the core structure is common to all distributions. These directory locations are used to store specific types of data as follows:<br>
<br>
<ul>
<li>/tmp: Stores temporary files. It is often used as a workspace by applications. Users should not use this directory to store anything of any importance because many Linux distributions wipe this directory on boot, and in a default installation, any user is able to read and write to this directory. Attackers may use this folder to store malware, often as the first stage of an attack, because it is a consistent and permissive directory across Linux installations.</li><br>
<li>/home: Location where the personal directories for users are stored. These directories should be secured because they often contain private and sensitive information (like configuration files with password, SSH private identity keys, and user files).</li><br>
<li>/usr: Used to store user-space programs and data. The reason for the /usr directory is mostly historical, but in modern Linux installations it contains several subdirectories:<br>
<br>
 - /usr/local: A location set aside for administrators to install software.<br>
 - /usr/share: Originally, this directory was used to share files between hosts that could be used on different Linux/Unix platforms. It was designed as a workaround when disk space was at a premium. Today's systems have no such constraints, so it is no longer used in that capacity.<br>
 - /usr/lib: Stores library files that executable programs need to access at run time<br>
 - /usr/bin and /usr/sbin: These directories are used to store binary (compiled) executable files. These files make up the bulk of the Linux operating system. The /usr/sbin was traditionally reserved for files that can only be used by root, but that distinction no longer applies.<br>
 - /usr/man: This directory is used to store the manual pages, AKA “man pages,” that contain the documentation for important files in the operating system and installed applications.
</li><br>
<li>/dev: Contains device files. Hardware and virtual devices, such as terminals, appear as files to the operating system. When Linux needs to access a device, it often does so by interacting through device files. Unlike other directories here, this folder is "special" in that the files and folders inside are representations of hardware and objects in the kernel. For example, although it appears to be a file, /dev/sda may point to your first hard disk drive, and /dev/urandom is a secure random number generator.</li><br>
<li>/etc: Stores system configuration files for the operating system and services. For example, SSL keys for web servers, private keys for SSH servers, and user accounts and passwords are kept here. This directory must be kept secure to keep the system secure.</li><br>
<li>/var: This directory is used by the operating system and applications to store runtime data and log files. There are several subdirectories that are located here, two of which are common to all Linux distributions:<br>
<br>
 - /var/log: Used by the operating system and applications to store log files. At a minimum, non-privileged users must be prevented from writing to this folder. Otherwise, the integrity of the log files would be compromised after an attack.<br>
 - /var/tmp: This directory is used as a workspace to store temporary runtime data for the operating system and running applications.
</li><br>
<li>/bin and /sbin: These directories are used to store system binary files. Traditionally, the files stored here were files that were required to boot the operating system. All other system files were stored in the /usr/bin and /usr/sbin directories, which is no longer true as many files found in /usr/bin and /usr/sbin are required at boot time.</li><br>
<li>/lib: Stores library files that must be available to executable files at run time.</li>
</ul>
<br>
<b>Special File System Structures</b><br>
When you navigate the file system from the command line, you are likely to encounter entries in directory listings in the form of a dot (.) or two dots (..). These structures represent important constructs in the file system. First, the single dot (.), is a reference to the current directory. The significance of this is that if, for example, you want to execute a file in the current directory, you may be surprised to find that the system will not find the file even if you are in the directory the file resides in. The reason for this is that Linux searches specific directories when you execute something.<br>
<br>
<pre>
<code>
Note:
The set of directories that Linux searches for command execution is stored in an environment variable that is called $PATH. The path is assigned to you at login. You can modify the path that is assigned to you by editing your user profile. If you wish to see the path for your environment, execute the following command: echo $PATH The output will show a colon-separated list of the directories in your path.
</code>
</pre>
<br>
Therefore, to execute a file that is not in the path, you would start with the reference to the current directory, the dot (.) followed by a forward slash (/), and the file name. For example, you want to compile a tool that you downloaded to your home directory, called new-app. You created a subdirectory in your home directory to store the components that are needed to compile the application. When ready, enter the directory that was created and compile the application, which will produce an executable file that is called new-app in that directory. To execute the application, enter the following in the command prompt:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154419.png" alt="" style="">
<br>
The double dot (..) refers to the parent directory of the current directory. For example, user Joe has a home directory of /home/joe. Joe creates a subdirectory to download a tool that is called newapp20. The full path to this directory is /home/joe/newapp20. While inside that directory, Joe decides to navigate back up to his home directory. To do so, he can use the double dot reference:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154475.png" alt="" style="">
<br>
Joe is now working in the /home/joe directory. The command that he used is the same as the following:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154525.png" alt="" style="">
<br>
One last structure that you may encounter in documentation or reference material is the tilde (~). The tilde is a shortcut that represents the current user’s home directory. Returning to the example of the user Joe, who wanted to navigate to his home directory, another alternative is to use the tilde,as follows:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154580.png" alt="" style="">
<br>
This command puts him back in his home directory: /home/joe<br>
<br>
<b>Fully Qualified vs. Relative File References</b><br>
You have two options for navigating the Linux file system. You can use a fully qualified reference to your destination or you can use a relative reference. The fully qualified reference means that you explicitly state the location beginning with the root of the file system.<br>
<br>
Fully qualified references always start with a forward slash (/), which represents the root. For example, the fully qualified reference to Joe’s home directory is /home/joe, which is workable as long as the file system locations are not too lengthy. Consider copying a file from one location to another using fully qualified path names:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154696.png" alt="" style="">
<br>
The benefit of this method is that copying this file to the specified location will work from anywhere in the file system. However, due to the length of the file location references, it is cumbersome to type, especially if a command can be repeated.<br>
<br>
An alternative is to use relative references. A relative reference lets you specify a location relative to some starting point other than root. For example, if a file that you wish to copy is in the directory that you are currently working in, you can omit the path and specify the file name and the destination. In this scenario, Joe is in his Downloads directory and he just downloaded a .pcap file. He uses the following command to copy the file to a directory called caps, under his home directory where he stores his .pcap files:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154769.png" alt="" style="">
<br>
In this example, Joe knows that his Downloads directory is in his home directory: /home/joe. The caps directory is also there. Since Joe is currently in the Downloads directory, he uses the double dots (..) to go up to the parent directory, and from there he moves down to the caps directory.<br>
<br>
Unlike fully qualified directory references, relative references have no leading forward slash. One last note on relative references is that you can also leverage the tilde (~), which points to your home directory. In the previous example, where Joe wants to copy a .pcap file from his Downloads directory to the caps directory, he could have used the following command instead:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154849.png" alt="" style="">
<br>
<b>How Devices Are Represented as Files in the Linux File System</b><br>
Devices in the Linux file system are represented as files. You will find them in the /dev directory. Usually, users don’t interact with device files directly. Device files are most often accessed by applications that require the services of a device. However, users that write scripts or code applications may need to access devices, so it is important to understand the concept of devices being represented as files.<br>
<br>
One example of a device that is used frequently in scripting is /dev/null, which is a device that represents nothing, so sending data to it is, in effect, discarding the data. Consider the following example:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517154954.png" alt="" style="">
<br>
Without the reference to /dev/null, the echo command would send the string test data to the terminal window where you entered the command. However, directing the output to /dev/null discards the data, so the echo command would not display the string in the terminal window as it normally would.<br>
<br>
Devices can be classified in one of the following categories:<br>
<br>
<ul>
<li>Block: Devices that process data in fixed chunks, for example, disk drives or other forms of storage devices.</li><br>
<li>Character: Devices that work with data streams. One such device is /dev/null. Directly connected printers are another example.</li><br>
<li>Pipe: Sometimes referred to as “named pipes.” These devices operate in a manner similar to character devices. However, the data stream is directed to another process rather than a device file or driver.</li><br>
<li>Sockets: These devices are unique in that they are not usually found in the /dev directory. They are used for interprocess communication such as network communication.</li>
</ul>
<br>
You will be able to tell a device’s type by listing the files in the /dev directory with file details. The following command lists files in a directory with the file details:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517155111.png" alt="" style="">
<br>
The l parameter lists the details, and the a parameter lists all files, including filenames that start with a dot (.). Here are some examples of device file entries:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517155163.png" alt="" style="">
<br>
The first character of the entry specifies the type. For example, the c represents a character type of device, and the b represents a block type of device.<br>
<br>
Some device types that you should be familiar with include disk devices. In some commands or configuration files, you will need to specify a disk drive reference. Complete by entering the file name of the device to reference.<br>
<br>
In Linux, disks are often identified by the letters sd, followed by a third letter. For example, the first disk drive would be referred to as sda. The next would be sdb. The three-letter code refers to the entire disk drive. However, disks are often divided into discreet partitions, so a number that follows the three-letter code of the disk indicates the sequence of partitions. For example:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517155263.png" alt="" style="">
<br>
Here, you see an entry for a disk drive that is called “sda,” which contains two partitions: sda1 and sda2. There are many types of devices and each has its unique identification code.<br>
<br>