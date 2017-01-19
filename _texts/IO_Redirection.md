---
layout: page
title: I/O Redirection
---

There are always three default files open, <i>STDIN</i>, <i>STDOUT</i>, and <i>STDERR</i>. These, and any other open files, can be redirected. Redirection simply means capturing output from a file, command, program, script, or even code block within a script and sending it as input to another file, command, program, or script.

<table>
  <tr>
    <th>Name</th>
    <th>Default Destination</th>
    <th>Redirection Use</th>
    <th>File Descriptor Number</th>
  </tr>
  <tr>
    <td align="center">STDIN</td>
    <td align="center">Keyboard</td>
    <td align="center"> < </td>
    <td align="center"> 0 </td>
  </tr>
   <tr>
    <td align="center">STDOUT</td>
    <td align="center">Monitor</td>
    <td align="center"> > </td>
    <td align="center"> 1 </td>
  </tr>
  <tr>
    <td align="center">STDERR</td>
    <td align="center">Monitor</td>
    <td align="center"> 2> </td>
    <td align="center"> 2 </td>
  </tr>
</table>