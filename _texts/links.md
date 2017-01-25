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