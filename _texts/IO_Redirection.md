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
    <td align="left">STDIN</td>
    <td align="center">Keyboard</td>
    <td align="center"> < </td>
    <td align="center"> 0 </td>
  </tr>
   <tr>
    <td align="left">STDOUT</td>
    <td align="center">Monitor</td>
    <td align="center"> > </td>
    <td align="center"> 1 </td>
  </tr>
  <tr>
    <td align="left">STDERR</td>
    <td align="center">Monitor</td>
    <td align="center"> 2> </td>
    <td align="center"> 2 </td>
  </tr>
</table>

Using I/O Redirection
<table>
  <tr>
    <th>Redirector</th>
    <th>Explanation</th>
    <th>Example</th>
  </tr>
  <tr>
    <td align="center"> 1> </td>
    <td align="left">Redirect <i>STDOUT</i></td>
    <td align="left"> 1> stdout.txt </td>
  </tr>
   <tr>
    <td align="center"> 1>> </td>
    <td align="left">Redirect and append <i>STDOUT</i></td>
    <td align="left"> 1>> stdout.txt </td>
  </tr>
  <tr>
    <td align="center"> 2> </td>
    <td align="left">Redirect <i>STDERR</i></td>
    <td align="left"> 2> stderr.txt </td>
  </tr>
   <tr>
    <td align="center"> 2>> </td>
    <td align="left">Redirect and append <i>STDERR</i></td>
    <td align="left"> 2>> stderr.txt </td>
  </tr>
   <tr>
    <td align="center"> &> </td>
    <td align="left">Redirect both <i>STDOUT</i> and <i>STDERR</i></td>
    <td align="left"> &> stdout_err.txt </td>
  </tr>
   <tr>
    <td align="center"> &>> </td>
    <td align="left">Redirect and append both <i>STDOUT</i> and <i>STDERR</i></td>
    <td align="left"> &>> stdout_err.txt </td>
  </tr>
</table>

Using Pipes<br>
A pipe <code> | </code> can be used to catch the output of one command and use that as input for a second command. A pipe <code> | </code> can be useful for chaining commands, scripts, files, and programs together.

<pre>
<code>
 cat *.txt | sort | uniq > result-file
 # Sorts the output of all the .txt files and deletes duplicate lines,
 # finally saves results to "result-file".
</code>
</pre>

---

[Advanced Bash-Scripting Guide: Chapter 20. I/O Redirection](http://www.tldp.org/LDP/abs/html/io-redirection.html)