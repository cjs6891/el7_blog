---
layout: page
title: History
---


Bash is configured to keep the last 1,000 commands you have used. When a shell session is closed, the historyof that session is updated to the history file <code>.bash_history</code>. The file <code>.bash_history</code> is created in the home directory of the user who started a specific shell session. The <code>.bash_history</code> file is closed only when the shell session is closed; until that moment, all commands in the history are kept in memory.<br>
<br>
Working W/History:
<ul>
<li>Type <code>history</code> to show a list of all commands in the bash history.</li>
<li>Use <code>Ctrl+r</code> to open the prompt from which you can do a backward search in commands that you have previously used. Just type a part of the command you are looking for, and it will be displayed automatically. Use <code>Ctrl+r</code> to search further backward based on the same search criteria</li>
<li>Type <code>!number</code> to execute a command with a specific number from history</li>
<li>Type <code>!sometext</code> to execute the last command that starts with sometext.<br>*Notice: The command that was found is executed immediately, it may be potentially dangerous.</li>
</ul><br>
<br>
Note:<br>
*<code>history -c</code> wipes all history that is currently in memory, but it doesn't remove the <code>.bash_history</code> file from the home directory. An alternative to deleting <code>.bash_history</code> is the command <code>history -w</code> after using <code>history -c</code>.


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