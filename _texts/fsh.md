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
    <td align="center">/</td>
    <td>The <code>root</code> directory. This is where the system tree starts.</td>
  </tr>
  <tr>
    <td align="center">/bin</td>
    <td>Contains executable programs that are needed to repair a system in a minimal troubleshooting mode. This directory is essential during boot.</td>
  </tr>
  <tr>
    <td align="center">/boot</td>
    <td>Contains all files and directories that are needed to boot the linux kernel.</td>
  </tr>
  <tr>
    <td align="center">/dev</td>
    <td>Device files that are used for accessing physical devices. This directory is essential during boot.</td>
  </tr>
  <tr>
    <td align="center">/etc</td>
    <td>Contains configuration files that are used by programs and services that are used on your server. This directory is essential during boot.</td>
  </tr>
  <tr>
    <td align="center">/home</td>
    <td>Used for local user home directories.</td>
  </tr>
  <tr>
    <td align="center">/lib, lib64</td>
    <td>Shared libraries that are used by programs in <code>/boot</code>, <code>/bin</code>, and <code>/sbin</code>.</td>
  </tr>
  <tr>
    <td align="center">/media, /mnt</td>
    <td>Directories that are used for mounting devies in the file system tree.</td>
  </tr>
  <tr>
    <td align="center">/opt</td>
    <td>This directory is used for optional packages that may be installed on your server.</td>
  </tr>
  <tr>
    <td align="center">/proc</td>
    <td>This directory is used by the proc file system. This is a file system structure that gives access to kernel information.</td>
  </tr>
  <tr>
    <td align="center">/root</td>
    <td>The home directory of the root user.</td>
  </tr>
  <tr>
    <td align="center">/run</td>
    <td>Contains process and user specific information that has been created since last boot.</td>
  </tr>
  <tr>
    <td align="center">/sbin</td>
    <td>Like <code>/bin</code>, but for system administration commands that are not necessarily needed by regular users.</td>
  </tr>
</table>