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
</table>