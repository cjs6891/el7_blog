---
layout: page
title: r4nd0m c0mm4nd5/n0735...
--- 

<pre>
who - show who is logged on

w - Show who is logged on and what they are doing.

Alt+F1 - Alt+F6, switch terminal windows at the console. # chvt can be used as a convienient alternative to using Alt+F1 - Alt+F6.

chvt - change foreground virtual terminal

In a graphical environment Ctrl+Alt+F1 - F6 may also be used.

halt, poweroff, reboot - Halt, power-off or reboot the machine

# systemctl reboot
# reboot
# systemctl halt
# halt
# systemctl poweroff
# poweroff

To Force a Machine Restart:
# /bin/echo b > /proc/sysrq-trigger

# ssh USERNAME@REMOTE_HOST
 - or -
# ssh REMOTE_HOST -l USERNAME

SSH Public Fingerprint:
~/.ssh/known_hosts

Common SSH Options
-v     Verbose, shows in detail what is happening while establishing the connection
-X     Enables support for graphical applications
-p PORT     Used to connect to an SSH service not listing on the default port 22

X Forwarding, SSH:
/etc/ssh/ssh_config
  ForwardX11 yes

scp — secure copy (remote file copy program)

Copy To Host
/usr/bin/scp /tmp/output.txt USERNAME@REMOTE_HOST:/tmp/output.txt

Copy From Host
/usr/bin/scp USERNAME@REMOTE_HOST:/tmp/output.txt /tmp/output.txt

scp can copy an entire subdirectory structure using the -r option
Copy To Host
/usr/bin/scp -r /tmp/output_dir USERNAME@REMOTE_HOST:/tmp/output_dir

Copy From Host
/usr/bin/scp -r USERNAME@REMOTE_HOST:/tmp/output_dir /tmp/output_dir


rsync - a fast, versatile, remote (and local) file-copying tool

SSH Key-Based Authentication
1. ssh-keygen — authentication key generation, management and conversion
2. ssh-copy-id — use locally available keys to authorize logins on a 
remote machine

# ssh-keygen
# ssh-copy-id USERNAME@REMOTE_HOST

Private Key:
~/.ssh/id_rsa

Public Key:
~/.ssh/id_rsa.pub

screen - screen manager with VT100/ANSI terminal emulation

screen allows you to run multiple terminal sessions attaching and detaching as necessary. 

List detached screen session(s)
# screen -list
There is a screen on:
        2877.pts-0.el7_blog    (Detached)

Attach to screen session(s)
# screen -r 2877

whoami - print effective userid

id - print real and effective user and group IDs

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

usermod - modify a user account
	-a, --append
		Add the user to the supplementary group(s). Use only with the -G option.
	-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
		A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no  intervening whitespace. The groups are subject to the same restrictions as the group given with the -g option.

		If the user is currently a member of a group which is not listed, the user will be removed from the group. This behavior can be changed via the -a option, which appends the user to the current supplementary group list. 

</pre>