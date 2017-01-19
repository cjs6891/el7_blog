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
    <td>STDIN</td>
    <td>Keyboard</td>
    <td>" < "</td>
    <td>" 0 "</td>
  </tr>
   <tr>
    <td>STDOUT</td>
    <td>Monitor</td>
    <td>" > "</td>
    <td>" 1 "</td>
  </tr>
  <tr>
    <td>STDERR</td>
    <td>Monitor</td>
    <td>" 2> "</td>
    <td>" 2 "</td>
  </tr>
</table>