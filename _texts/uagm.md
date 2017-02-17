---
layout: page
title: user and group management
---

Users on Linux<br>
To get information about a user account, use the <code>id</code> command.
<pre>
$ id
uid=1000(toor) gid=100(users) groups=100(users)
</pre>

root<br>
On all linux systems, by default there is the user root, also known as the super-user. root is used for managing Linux... Generally speaking, all tasks that involve direct access to devices need root permissions.<br>
<br>
Making a habit of logging in as root is an unnecessary security risk, try using one of the following alternative methods.<br>
<br>
Run Tasks W/Elevated Permissions
<table>
  <tr>
    <th>Command</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>su</code></td>
    <td>Opens a subshell as a different user, with the advantage that only in the subshell commands are executed as root; environmental variables are NOT set.</td>
  </tr>
  <tr>
    <td align="center"><code>su -</code></td>
    <td>Opens a subshell as a different user, with the advantage that only in the subshell commands are executed as root; environmental variables ARE set.</td>
  </tr>
  <tr>
    <td align="center"><code>sudo</code></td>
    <td>Allows you to set up an environment where specific tasks are executed with administrative privileges.</td>
  </tr>
  <tr>
    <td align="center"><code>PolicyKit</code></td>
    <td>Allows you to set up graphical utilities to run with administrative privileges.</td>
  </tr>
</table>

*** Using <code>su -</code> is better than using <code>su</code>. When <code>-</code> is used, a login shell is started, without the <code>-</code>, some variables may not be set correctly.<br>
<br>
sudo<br>
Instead of using the root user account, unprivileged users can be configured for using administrator permissions on specific tasks by using sudo. This is more secure because you will only be able to act as if you have administrator permissions while running this specific command.<br>
1. Add <i>USER</i> account to the wheel group, <code>usermod -aG wheel <i>USER</i></code><br>
2. Use <code>visudo</code> to verify <code>%wheel  ALL=(ALL)       ALL</code> is included<br>
<pre>
## Same thing without a password
# %wheel        ALL=(ALL)       NOPASSWD: ALL
</pre>

A few useful user commands:<br>
<pre>
whoami - print effective userid

id - print real and effective user and group IDs
</pre>
Managing Accounts<br>
<code>/etc/passwd</code><br>
<pre>
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
avahi-autoipd:x:170:170:Avahi IPv4LL Stack:/var/lib/avahi-autoipd:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
tss:x:59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
ntp:x:38:38::/etc/ntp:/sbin/nologin
</pre>
Fields of <code>/etc/passwd</code>
<ul>
<li><b>USERNAME</b>: Unique name for the user. User names are important to match a user to his password, which is stored separately in <code>/etc/shadow</code>. On Linux, there can be no spaces in the username.</li>
<li><b>Password</b>: In the old days, the second field of <code>/etc/passwd</code> was used to store the hashes password of the user. <code>/etc/passwd</code> is readable by all users, and poses a security risk. Current Linux systems store the hashes password in <code>/etc/shadow</code></li>
<li><b>UID</b>: Each user has a unique user ID (UID). It is the UID that really determines what a user can do. UID 0 is reserved for root. The lowerd UIDs (typically up to 999) are used for system accounts, and the higher UIDs (from 1,000 on by default), are reserved for people that need to connect directly to the server. The range of UIDs that are used to create regular user accounts is set in <code>/etc/login.defs</code>.</li>
<li><b>GID</b>: Each user is a member of at least one group, referred to as the <i>primary group</i>.</li>
<li><b>Comment Field</b>: Comment field... used for commenting user accounts</li>
<li><b>Directory</b>: The <i>home directory</i>, the initial directory where the user is placed after logging in and would store personal files, programs, etc.</li>
<li><b>Shell</b>: The program that is started after the user has successfully connected to the server, for most users it will be <code>/bin/bash</code>. For system accounts it will typically be <code>/sbin/nologin</code>. The <code>/sbin/nologin</code> command is a specific command that denies access to users.</li>
</ul>