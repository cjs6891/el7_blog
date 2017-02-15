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
2. Use <code>visudo</code> to verify <pre>%wheel  ALL=(ALL)       ALL</pre> is included<br>
<pre>
## Same thing without a password
# %wheel        ALL=(ALL)       NOPASSWD: ALL
</pre>

A few useful user commands:<br>
<pre>
whoami - print effective userid

id - print real and effective user and group IDs
</pre>