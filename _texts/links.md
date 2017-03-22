---
layout: page
title: links, hard and symbolic
---

Understanding Hard links<br>
Linux stores administrative data about files in inodes. Every file on linux has an inode, and in the inode, important information about the file is stored:<br>
<ul>
<li>The data block where the file contents are stored</li>
<li>The creation, access, and modification date</li>
<li>Permissions</li>
<li>File owners</li>
</ul>
Just one important piece of information is not stored in the inode: the name. Names are stored in the directory, and each filename knows which inode it has to address to access further file information.<br>
<br>
When you create a file, you give it a name. Basically, this name is a hard link. On a linux file system, multiple hard links can be created to a file. This can be useful, because it enables you to access the file from multiple different locations. Some restrictions apply to hard links:
<ul>
<li>Hard links must exist all on the save device</li>
<li>You can't create hard links to directories</li>
<li>The number of aliases the original file has. When the last name is removed, the contents are also removed.</li>
</ul>
Understanding Symbolic Links<br>
A symbolic link does not link directly to the inode but to the name of the file. This makes symbolic links much more flexible, but it also has some disadvantages. The advantages of symbolic links is that they can link to files on other devices, as well as on directories. The major disadvantage is that when the original file is removed, the symbolic link becomes invalid and does not work any longer.<br>
<br>
Creating Links<br>
Use the <code>ln</code> command to create links. It uses the same order as <code>cp</code> and <code>mv</code>; first you mention the source name, followed by the destination name. If you want to create a symbolic link, you use the option <code>-s</code>, and then you specify the source and target file or directory. One important restriction applies, however; to be able to create hard links, you must be the owner of the item that you want to link to. This is a new security restriction that has been introduced in EL7.

<table>
  <col width="35%">
  <col width="65%">
  <tr>
    <th>Command</th>
    <th>Explanation</th>
  </tr>
  <tr>
    <td align="center"><code>ln /etc/hosts .</code></td>
    <td>Creates a link to the file <code>/etc/hosts</code> in the current directory</td>
  </tr>
  <tr>
    <td align="center"><code>ln -s /etc/hosts .</code></td>
    <td>Creates a symbolic link to the file <code>/etc/hosts</code> in the current directory</td>
  </tr>
  <tr>
    <td align="center"><code>ln -s /home /tmp</code></td>
    <td>Creates a symbolic link to the directory <code>/home</code> in the directory <code>/tmp</code></td>
  </tr>
</table><br>

The <code>ls</code> command will reveal whether a file is a link:
<ul>
<li>In the output of the <code>ls -l</code> command, the first character is an <code>l</code> if the file is a symbolic link.</li>
<li>If a file is a symbolic link, the output of <code>ls -l</code> shows the name of the item it links to after the filename</li>
<li>If a file is a hard link, <code>ls -l</code> shows the hard link counter</li>
</ul>
<pre>
<code>
[root@el7_blog.local]# pwd
/tmp
[root@el7_blog.local]# ls -l
-rw-r--r--.  2 root root     0 Apr 18  2016 HTTPD_ERRORS
lrwxrwxrwx.  1 jobs users    5 Jan 25 16:03 home -> /home
drwxrwxrwt.  7 root root  4.0K Jan 25 16:05 .
</code>
</pre>
Removing Links<br>
Removing links can be dangerous. DO NOT USE <code>-r</code> or <code>-f</code> to remove links, even if they are subdirectories.<br>
<br>
Change Ownership of Links<br>
<code>chown -h<i> symbolic link</i></code> -h, --no-dereference, affect each symbolic link instead of any referenced file (useful only on systems that can change the ownership of a symlink)<br>