---
layout: page
title: shell environment
---

The environment consists of variables that define the user environment, such as <code>$PATH</code>. Variables are fixed names that can be assigned dynamic values. The advantage for scripts and programs of working with variables is that the program only has to use the name of the variable without taking interest in the specific value that is assigned to the variable. Becasue the needs for different users are different, the variables that are set in a user environment will differ. Type <code>env</code> to get an overview of the current variables defined in your shell environment.

<pre>
<code>
[root@el7_blog.local]# env
HOSTNAME=WSH-1905.local
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

To define a variable, the name of the variable is mentioned followed by an equals sign (<code>=</code>) and the value that is assigned to the specific variable.


<table>
  <tr>
    <th>vi/vim command</th>
    <th>Explanation</th>
  </tr>

  <tr>
    <td align="center"><code>Esc</code></td>
    <td align="left">Switches from input mode to command mode.</td>
  </tr>

  <tr>
    <td align="center"><code>i, a</code></td>
    <td align="left">Switches from command mode to input mode at <code>i</code> or after <code>a</code> the curent cursor position</td>
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
    <td align="left">Quits the file without applying any changes.</td>
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