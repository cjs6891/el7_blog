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
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=01;05;37;41:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.tbz=01;31:*.tbz2=01;31:*.bz=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=01;36:*.au=01;36:*.flac=01;36:*.mid=01;36:*.midi=01;36:*.mka=01;36:*.mp3=01;36:*.mpc=01;36:*.ogg=01;36:*.ra=01;36:*.wav=01;36:*.axa=01;36:*.oga=01;36:*.spx=01;36:*.xspf=01;36:
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