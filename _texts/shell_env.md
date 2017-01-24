---
layout: page
title: shell environment
---

The environment consists of variables that define the user environment, such as <code>$PATH</code>. Variables are fixed names that can be assigned dynamic values. The advantage for scripts and programs of working with variables is that the program only has to use the name of the variable without taking interest in the specific value that is assigned to the variable. Becasue the needs for different users are different, the variables that are set in a user environment will differ. Type <code>env</code> to get an overview of the current variables defined in your shell environment.

<pre>
<code>
[root@el7_blog.local]# env
HOSTNAME=el7_blog.local.local
TERM=xterm
SHELL=/bin/bash
HISTSIZE=1000
SSH_CLIENT=192.168.<i>X</i>.<i>X</i> 8367 22
QTDIR=/usr/lib64/qt-3.3
OLDPWD=/root
QTINC=/usr/lib64/qt-3.3/include
SSH_TTY=/dev/pts/0
USER=root
LIBGL_DRIVERS_PATH=/usr/lib/dri:/usr/lib64/dri
MAIL=/var/spool/mail/root
PATH=/usr/lib64/qt-3.3/bin:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin
PWD=/root
LANG=en_US.UTF-8
SSH_ASKPASS=/usr/libexec/openssh/gnome-ssh-askpass
HISTCONTROL=ignoredups
SHLVL=1
HOME=/root
LOGNAME=root
QTLIB=/usr/lib64/qt-3.3/lib
CVS_RSH=ssh
SSH_CONNECTION=192.168.<i>X</i>.<i>X</i> 8367 192.168.<i>X</i>.<i>X</i> 22
LESSOPEN=||/usr/bin/lesspipe.sh %s
G_BROKEN_FILENAMES=1
_=/bin/env
</code>
</pre>

To define a variable, the name of the variable is mentioned followed by an equals sign (<code>=</code>) and the value that is assigned to the specific variable.<br>

Environment Configuration Files<br>
<ul>
<li><code>/etc/profile</code>: This is the generic file that is processes by all users upon login.</li>
<li><code>/etc/bashrc</code>: This file is processed when subshells are started.</li>
<li><code>~/.bash_profile</code>: In this file, user-specific login shell variables can be defined.</li>
<li><code>~/.bashrc</code>: In this user-specific file, subshell variables can be defined.</li>
</ul><br>

re-load <code>~/.bash_profile</code> -or- <code>~/.bashrc</code> on the fly, i.e.without having to log out and in:<br>
<table>
<tr><td><code>source ~/.bash_profile</code></td></tr>
<tr><td><code>source ~/.bashrc</code></td></tr>
<tr><td><code>. ~/.bash_profile</code></td></tr>
<tr><td><code>. ~/.bashrc</code></td></tr>
</table><br>

<code>/etc/motd</code> and <code>/etc/issue</code><br>
Bash offers an option to include messages in the <code>/etc/motd</code> and <code>/etc/issue</code> files. Messages in <code>/etc/motd</code> display after a user has successfully logged into a shell. Another way to send information to users is by using <code>/etc/issue</code>. The contents of this file display before the user logs in.