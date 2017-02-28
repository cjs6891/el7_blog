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
Fields of <code>/etc/passwd</code>:
<ul>
<li><b>USERNAME</b>: Unique name for the user. User names are important to match a user to his password, which is stored separately in <code>/etc/shadow</code>. On Linux, there can be no spaces in the username.</li>
<li><b>Password</b>: In the old days, the second field of <code>/etc/passwd</code> was used to store the hashes password of the user. <code>/etc/passwd</code> is readable by all users, and poses a security risk. Current Linux systems store the hashes password in <code>/etc/shadow</code>.</li>
<li><b>UID</b>: Each user has a unique user ID (UID). It is the UID that really determines what a user can do. UID 0 is reserved for root. The lowerd UIDs (<i>typically up to 999</i>) are used for system accounts, and the higher UIDs (<i>from 1,000 on by default</i>), are reserved for people that need to connect directly to the server. The range of UIDs that are used to create regular user accounts is set in <code>/etc/login.defs</code>.</li>
<li><b>GID</b>: Each user is a member of at least one group, referred to as the <i>primary group</i>. The primary group plays a central role in permissions management.</li>
<li><b>Comment Field</b>: Self explanatory.</li>
<li><b>Directory</b>: The <i>home directory</i>, the initial directory where the user is placed after logging in, and storing personal files, programs, etc.</li>
<li><b>Shell</b>: The program that is started after the user has successfully connected to the server, for most users it will be <code>/bin/bash</code>. For system accounts it will typically be <code>/sbin/nologin</code>. The <code>/sbin/nologin</code> command is a specific command that denies access.</li>
</ul>
<br>
Fields of <code>/etc/shadow</code>:
<ul>
<li><b>Login Name</b>: Notice <code>/etc/shadow</code> does not contain any UIDs, but user names only.</li>
<li><b>Encrypted Password</b>: Self explanatory.</li>
<li><b>Days since January 1, 1970, that the password was last changed</b>: aka <i>epoch</i>, considered the beginning of days on Linux</li>
<li><b>Days before a password may be changed</b>: Allows for a more strict password policy, where it's not possible to change back to the original password immediately.</li>
<li><b>Days after which a password must be changed</b>: Contains the maximum validity period of passwords. Notice default is 99,999</li>
<li><b>Days before password is to expire that user is warned</b>: Used to warn a user when a forced password change is upcoming, default is 7.</li>
<li><b>Days after password expires that account is disabled</b>: Used to enforce a password change. After password expiry, users can't log in.</li>
<li><b>Days since January 1, 1970, that account is disabled</b>: Can set this field to disable an account.</li>
<li><b>Reserved field</b>: Self explanatory.</li>
</ul>
<br>
*** Most of the password properties can be managed with <code>passwd</code> or <code>chage</code>.<br>
<br>
Creating Users<br>
You can edit <code>/etc/passwd</code> and <code>/etc/shadow</code> files directly or use <code>useradd</code>. To remove users, you can use <code>userdel</code>. Use <code>userdel -r</code> to remove a user, including the complete user environment.<br>
<br>
Modifying Configuration Files<br>
To add accounts, it suffices that one line is added to <code>/etc/passwd</code> and another line is added to <code>/etc/shadow</code>, in which the user account and all of its properties are defined. It's not recommended, though. By making an error, you might mess up the consistency of the file and make logging in completely impossible to anyone.<br>
<br>
useradd<br>
The <code>useradd</code> utility is probably the most common tool on Linux for managing users.
<pre>
useradd - create a new user or update default new user information
  -m, --create-home
    Create the user's home directory if it does not exist
  -M, --no-create-home
    Do not create the user's home directory, even if the system wide setting from /etc/login.defs (CREATE_HOME) is set to yes.
  -g, --gid GROUP
    The group name or number of the user's initial login group
  -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace
  -u, --uid UID
    The numerical value of the user's ID

userdel - delete a user account and related files
  -r, --remove
    Files in the user's home directory will be removed along with the home directory itself and the user's mail spool.
</pre>
<br>
usermod<br>
The ultimate command-line utility for modifying user properties is <code>usermod</code>. It can be used to set all properties of users as stored in <code>/etc/passwd</code> and <code>/etc/shadow</code>, plus some additional tasks, such as managing group membership.<br>
<br>
User Management Default Configuration Files<br>
<code>/etc/login.defs</code> and <code>/etc/default/useradd</code>.<br>
<br>
<code>/etc/default/useradd</code> contains some default values that are applied when using useradd.<br>
<br>
<code>/etc/login.defs</code> login related variables are set. A list of the most significant properties that can be set:<br>
<ul>
<li><code>MOTD_FILE</code>: Message of the Day File.</li>
<li><code>ENV_PATH</code>: Defines $PATH variable, a list of directories that should be searched for executable files after logging in.</li>
<li><code>PASS_MAX_DAYS, PASS_MIN_DAYS</code> and <code>PASS_WARN_AGE</code>: Define the default password expiration properties when creating new users.</li>
<li><code>UID_MIN</code>: The first UID to use when creating new users.</li>
<li><code>CREATE_HOME</code>: Indicates whether or not to create a home directory for new users.</li>
<li><code>USERGROUPS_ENAB</code>: Set to yes to create a private group for all new users. That means a new user has a group with the same name as the user as its default group. If set to no, all users are made a member of the group users.</li>
</ul>
<br>
<code>passwd</code> - update user's authentication tokens<br>
<code>chage</code> - change user password expiry information<br>
<br>
Managing Password Properties<br>
Password properties are set in <code>/etc/shadow</code>. You can use <code>chage</code> and <code>passwd</code> to change these properties. To see current password settings use <code>chage -l <i>USERNAME</i></code>.<br> 
<br>
Creating a User Environment<br>
When a user logs in, an environment is created. To construct the user environment, a few files play a role:
<ul>
<li><code>/etc/profile</code>: Used for default settings for all users when starting a login shell</li>
<li><code>/etc/bashrc</code>: Used to define defaults for all users when starting a subshell</li>
<li><code>~/.bash_profile</code>: Specific settings for one user applied when starting a login shell</li>
<li><code>~/.bashrc</code>: Specific settings for one user applied when starting a subshell</li>
</ul>
When logging in, the files are read in this order, and variables and other settings that are defined in these files are applied. If a variable or setting occurs in more than one file, the last one wins.