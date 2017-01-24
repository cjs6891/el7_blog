---
layout: page
title: file system hierarchy
---

The file system on most linux systems is organized in a similar way. The layout of the linux file system is defined in the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/), and this file system hierarchy is described in <code>man 7 hier</code>.<br>

FSH Overview
<table>
  <tr>
    <th>Directory</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>/</code></td>
    <td>The <code>root</code> directory. This is where the system tree starts.</td>
  </tr>
  <tr>
    <td align="center"><code>/bin</code></td>
    <td>Contains executable programs that are needed to repair a system in a minimal troubleshooting mode. This directory is essential during boot.</td>
  </tr>
  <tr>
    <td align="center"><code>/boot</code></td>
    <td>Contains all files and directories that are needed to boot the linux kernel.</td>
  </tr>
  <tr>
    <td align="center"><code>/dev</code></td>
    <td>Device files that are used for accessing physical devices. This directory is essential during boot.</td>
  </tr>
  <tr>
    <td align="center"><code>/etc</code></td>
    <td>Contains configuration files that are used by programs and services that are used on your server. This directory is essential during boot.</td>
  </tr>
  <tr>
    <td align="center"><code>/home</code></td>
    <td>Used for local user home directories.</td>
  </tr>
  <tr>
    <td align="center"><code>/lib, lib64</code></td>
    <td>Shared libraries that are used by programs in <code>/boot</code>, <code>/bin</code>, and <code>/sbin</code>.</td>
  </tr>
  <tr>
    <td align="center"><code>/media, /mnt</code></td>
    <td>Directories that are used for mounting devies in the file system tree.</td>
  </tr>
  <tr>
    <td align="center"><code>/opt</code></td>
    <td>This directory is used for optional packages that may be installed on your server.</td>
  </tr>
  <tr>
    <td align="center"><code>/proc</code></td>
    <td>This directory is used by the proc file system. This is a file system structure that gives access to kernel information.</td>
  </tr>
  <tr>
    <td align="center"><code>/root</code></td>
    <td>The home directory of the root user.</td>
  </tr>
  <tr>
    <td align="center"><code>/run</code></td>
    <td>Contains process and user specific information that has been created since last boot.</td>
  </tr>
  <tr>
    <td align="center"><code>/sbin</code></td>
    <td>Like <code>/bin</code>, but for system administration commands that are not necessarily needed by regular users.</td>
  </tr>
  <tr>
    <td align="center"><code>/srv</code></td>
    <td>Directory that may be used for data that is used by services like NFS, FTP, and HTTP.</td>
  </tr>
  <tr>
    <td align="center"><code>/sys</code></td>
    <td>Used as an interface to different hardware devices that is managed by the linux kernel and associated processes.</td>
  </tr>
  <tr>
    <td align="center"><code>/tmp</code></td>
    <td>Contains temporary files that may be deleted without any warning during boot.</td>
  </tr>
  <tr>
    <td align="center"><code>/usr</code></td>
    <td>Directory that contains subdirectories with program files, libraries for these program files and documentation about them. Typically, many subdirectories exist in this directory that mimic the contents of the <code>/</code> directory. The contents of <code>/usr</code> are not required during boot.</td>
  </tr>
  <tr>
    <td align="center"><code>/var</code></td>
    <td>Directory that contains files which may change in size dynamically, such as log files, mail boxes, and spool files.</td>
  </tr>
</table>