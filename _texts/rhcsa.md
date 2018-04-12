---
layout: page
title: Red Hat Certified System Administrator
---

[Download CentOS Linux ISO images](https://wiki.centos.org/Download){:target="_blank"}

<b>Executing Commands</b><br>
The purpose of the Linux shell is that it provides an environment in which commands can be executed. The shell takes care of interpreting the command that a user has entered correctly. To do this, the shell makes a difference between three kinds of commands:<br>
<br>
<ul>
<li>Aliases</li>
<li>Internal Commands</li>
<li>External Commands</li>
</ul>
<br>
An alias is a command that a user can define as needed. Some aliases are provided by default; type <code>alias</code> on the command line to get an overview. To define an alias, use <code>alias newcommand='oldcommand'</code>, as in the default alias <code>alias ll='ls -l --color=auto'</code>. Aliases are executed before anything else.<br>
<br>
<pre>
<code>
# alias
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
</code>
</pre>
<br>
An internal command is a command that is a part of the shell itself. It is available when the shell is loaded and can be executed from memory without any lookup from disk. An external command is a command that exists as an executable file on disk of the computer. Because it has to be read from disk, it is a bit slower. When a user executes a command, the shell first looks to determine whether it is an internal command; if it is not, it looks for an executable file with a name that matches the command on disk. To find out whether a command is a bash internal, or an executable file on disk, you can use the <code>type <i>command</i></code>.<br>
<br>
To look up external commands, the <code>$PATH</code> variable is used. This variable defines a list of directories that is searched for a matching filename when a user enters a command. To find out which exact command the shell will be using, you can use the <code>which</code> command. For instance, type <code>which ls</code> to find out where the shell will get the <code>ls</code> command from.<br>
<br>
<b>Internal Command</b> - A command that is a part of the shell and does not exist as a file on disk.<br>
<br>
<b>External Command</b> - A command that exists as a file on disk.<br>
<br>
You should notice that for security reasons that the current directory is not in the <code>$PATH</code> variable and that Linux does not look in the current directory to see whether a specific command is available from that directory. That is why you need to start a command that is in the current directory but nowhere in the $PATH by including <code>./</code> in front of it. The dot stands for the current directory, and by running it as </code>./<code>, you're telling bash to look for the command in the current directory.<br>
<br>