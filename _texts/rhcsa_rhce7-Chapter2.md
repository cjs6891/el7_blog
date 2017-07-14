---
layout: page
title: RHCSA - Using Essential Tools
---

<b>Basic Shell Skills</b><br>
Executing Commands<br>
The purpose of the Linux shell is that it provides an environment in which commands can be executed. The shell takes care of interpreting the commands that a user has entered. The shell make a difference between three kinds of commands:<br>
<ul>
<li>Aliases</li>
<li>Internal Commands</li>
<li>External Commands</li>
</ul>
An alias is a command that a user can define as needed. Type the <code>alias</code> command to get an overview.
<pre><code>[root@el7_blog.local ~]# alias
alias cp='cp -i'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
</code></pre>
To define an alias, use <code>alias <i>NEWCOMMAND</i>='<i>OLDCOMMAND</i>'</code>, as in <code>alias ll='ls -l --color=auto'</code><br>
<br>
An internal command is a command that is a part of the shell itself. It is available when the shell is loaded and can be executed from memory without any lookup from disk.<br>
<br>
An external command is a command that exists as an executable file on disk; because is has to be read from disk, it's a bit slower.<br>
<br>
To find out whether a command is a bash internal, or an executable file on disk, use the <code>type</code> command.
<pre><code>[root@el7_blog.local ~]# type time
time is a shell keyword

[root@el7_blog.local ~]# which time
/usr/bin/time

[root@el7_blog.local ~]# type /usr/bin/time
/usr/bin/time is /usr/bin/time
</code></pre>
To look up external commands, the <code>$PATH</code> variable is used. This variable defines a list of directories that is searched for a matching filename when a users enters a command. You can use the <code>which</code> command to find the exact command the shell will be using. For security reasons the current directory is not in the <code>$PATH</code> variable, and Linux does not look in the current directory to see whether a specific command is available from that directory. That is why you need to start a command that is in the current directory but nowhere in the <code>$PATH</code> by including a <b><i>./</i></b> in front of it. The dot stands for the current directory, and by running it as <b><i>./</i></b>, you'll tell bash to look for the command in the current directory.<br>
<br>
I/O Redirection<br>
There are always three default files open, <i>STDIN</i>, <i>STDOUT</i>, and <i>STDERR</i>. These, and any other open files, can be redirected. Redirection simply means capturing output from a file, command, program, script, or even code block within a script and sending it as input to another file, command, program, or script.<br>
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
In I/O redirection, files can be used to replace the default STDIN, STDOUT, and STDERR. You can also redirect to <i>device files</i>. A device file on Linux is a file that is used to access specific hardware. The hard disk for instance can be referred to as <i>/dev/sda</i>, the console as <i>/dev/console</i> or <i>/dev/tty</i>, and if you want to discard a commands output, you can redirect to <i>/dev/null</i>.<br>
<table>
  <tr>
    <th>Redirector</th>
    <th>Explanation</th>
    <th>Example</th>
  </tr>
  <tr>
    <td align="center"> > -or- 1> </td>
    <td align="left">Redirect <i>STDOUT</i></td>
    <td align="left"> > stdout.txt </td>
  </tr>
   <tr>
    <td align="center"> >> -or- 1>> </td>
    <td align="left">Redirect and append <i>STDOUT</i></td>
    <td align="left"> >> stdout.txt </td>
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
<br>
Using Pipes<br>
A pipe <code> | </code> can be used to catch the output of one command and use that as input for a second command. A pipe <code> | </code> can be useful for chaining commands, scripts, files, and programs together.

<pre>
<code>
 cat *.txt | sort | uniq > result-file
 # Sorts the output of all the .txt files and deletes duplicate lines, saving results to "result-file".
</code>
</pre>
<br>
History<br>
Bash is configured to keep the last 1,000 commands you have used. When a shell session is closed, the history of that session is updated to the history file <code>.bash_history</code>. The <code>.bash_history</code> file is created in the home directory of the user who started a specific shell session. The history file is closed only when the shell session is closed; until that moment, all commands in the history are kept in memory.<br>
<br>
The history feature makes it easy to repeat complex commands. There are several ways of working history:<br>
<ul>
<li>Type <code>history</code> to show a list of all commands in the bash history</li>
<li>Use <code>Ctrl+r</code> to open the prompt from which you can do backward searches in the commands that you have previously used. Use <code>Ctrl+r</code> again to search further backward based on the same search criteria.</li>
<li>Type <code>!<i>number</i></code> to execute a command with a specific number from history.</li>
<li>Type <code>!<i>sometext</i></code> to execute the last command that starts with <i>sometext</i>. <i><b>Notice: </b><code>!<i>sometext</i></code> is potentially dangerous because the command that was found is executed immediately!</i></li>
</ul>
<b><i>Note:</i></b> The <code>history -c</code> command wipes all history that is currently in memory, but it doesn't remove the <code>.bash_history</code> file from the home directory.<br>
<b><i>&nbsp;*&nbsp;</i></b> The <code>history -w</code> command writes the current history to the history file, overwriting the history file's contents.<br>
<b><i>&nbsp;*&nbsp;</i></b>Use <code>rm -fr ~/.bash_history</code> to delete the history file. As an alternative to deleting the history file, you can use <code>history -w</code> after using <code>history -c</code>, i.e.<code>history -c && history -w</code>.<br>
<br>
Bash Completion<br>
Another useful feature of the bash shell is automatic completion. This feature helps you in finding the commands you need, and it also works on variables and filenames.<br>
<br>
Just type the beginning of a command and press the <code>Tab</code> key on you keyboard. If there is only one option for completion, bash will complete the command automatically for you. If there are several options, you need to press the <code>Tab</code> key once more to get an overview of all available options.<br>

<b>Editing Files w/vi and/or vim</b><br>
The only text editor that is always available is <code>vi</code>. An important concept when working with <code>vi/vim</code> is that it uses different modes. Two of them are particularly important: command mode and input mode. These modes often cause confusion because in command mode you can just enter a command and you cannot change the contents of a text file. To change the contents of a text file, you need to get to input mode.<br>

<table>
  <tr>
    <th>vi/vim command</th>
    <th>Explanation</th>
  </tr>

  <tr>
    <td align="center"><code>Esc</code></td>
    <td align="left">Switches from input mode to command mode. Use this before typing any command.</td>
  </tr>

  <tr>
    <td align="center"><code>i, a</code></td>
    <td align="left">Switches from command mode to input mode at (<code>i</code>) or after (<code>a</code>) the current cursor position</td>
  </tr>

  <tr>
    <td align="center"><code>o</code></td>
    <td align="left">Opens a new line below the current cursor position and goes to input mode.</td>
  </tr>

  <tr>
    <td align="center"><code>:wq</code></td>
    <td align="left">Writes the current file and quits.</td>
  </tr>

  <tr>
    <td align="center"><code>:q!</code></td>
    <td align="left">Quits the file without applying any changes. The <code>!</code> forces the command to do its work.</td>
  </tr>

  <tr>
    <td align="center"><code>:w <i>filename</i></code></td>
    <td align="left">Writes the current file with a new <i>filename</i></td>
  </tr>

  <tr>
    <td align="center"><code>dd</code></td>
    <td align="left">Deletes the current line.</td>
  </tr>

  <tr>
    <td align="center"><code>yy</code></td>
    <td align="left">Copies the current line.</td>
  </tr>

  <tr>
    <td align="center"><code>P</code></td>
    <td align="left">Pastes the current selection.</td>
  </tr>

  <tr>
    <td align="center"><code>v</code></td>
    <td align="left">Enters visual mode, allowing you to select a block of text using the arrow keys. Use <code>d</code> to cut, or <code>y</code> to copy the selection.</td>
  </tr>

  <tr>
    <td align="center"><code>u</code></td>
    <td align="left">Undoes the last command, repeat as needed.</td>
  </tr>

  <tr>
    <td align="center"><code>Ctrl+r</code></td>
    <td align="left">Redoes the last undo.</td>
  </tr>

  <tr>
    <td align="center"><code>gg</code></td>
    <td align="left">Goes to the first line in the document.</td>
  </tr>

  <tr>
    <td align="center"><code>G</code></td>
    <td align="left">Goes to the last line in the document.</td>
  </tr>

  <tr>
    <td align="center"><code>/<i>string</i></code></td>
    <td align="left">Searches for <i>string</i> from the current cursor position forward.</td>
  </tr>

  <tr>
    <td align="center"><code>?<i>string</i></code></td>
    <td align="left">Searches for <i>string</i> from the current cursor position backward.</td>
  </tr>

  <tr>
    <td align="center"><code>^</code></td>
    <td align="left">Goes to the first position in the current line.</td>
  </tr>

  <tr>
    <td align="center"><code>$</code></td>
    <td align="left">Goes to the last position in the current line.</td>
  </tr>

  <tr>
    <td align="center"><code>!ls</code></td>
    <td align="left">Adds the output of <code>ls</code> (<i>or any other command</i>) in the current file.</td>
  </tr>

  <tr>
    <td align="center"><code>:%s/old/new/g</code></td>
    <td align="left">Replaces <i>ALL</i> occurrences of <i>old</i> with <i>new</i>.</td>
  </tr>

  <tr>
    <td align="center"><code>:9</code></td>
    <td align="left">Goes to line number 9.</td>
  </tr>
</table>
<br>
<b>Understanding the Shell Environment</b><br>
Understanding Variables<br>
Variables are fixed names that can be assigned dynamic values. The advantage for scripts and programs of working with variables is that the program only has to use the name of the variable without taking interest in the specified value that is assigned the the variable. Because the needs for different users are different, the variables that are set in a user environment will differ. The <code>env</code> command will give you an overview of the current variables defined in your shell.<br>
<br>
Environment Configuration Files<br>
When a user logs in, an environment is created for that user automatically. This happens on four different files where some script code can be specified and where variables can be defined for use by one specific user:
<ul>
<li><code>/etc/profile</code> This is the generic file that is processed by all users upon login.</li>
<li><code>/etc/bashrc</code> This file is processed when subshells are started.</li>
<li><code>~/.bash_profile</code> In this file, user-specific login shell variables can be defined.</li>
<li><code>~/.bashrc</code> In this file, subshell variables can be defined.</li>
</ul>
In these files a difference is made between a login shell and a subshell. A login shell is the first shell that is opened for a user after the user has logged in. From the login shell, a user may run scripts, which will start a subshell of that login shell. Bash allows for the creation of a different environment in the login shell and in the subshell but to make sure the same settings are used in all shells, it's a good idea to include subshell settings in the login shell as well.<br>
<br>
Using <code>/etc/motd</code><code>/etc/issue</code>