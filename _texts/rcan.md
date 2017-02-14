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

# ssh USERNAME@HOST
 - or -
# ssh HOST -l USERNAME

SSH Public Fingerprint:
~/.ssh/known_hosts

Common SSH Options
-v     Verbose, shows in detail what is happening while establishing the connection
-X     Enables support for graphical applications
-p <PORT>     Used to connect to an SSH service not listing on the default port 22


</pre>