---
layout: page
title: managing files
---

Working W/Wildcards<br>
When working with files, using wildcards can make your work a lot easier. A wildcard is a shell feature that helps you referring to multiple files in an easy way.<br>


Wildcard Overview<br>
<table>
  <tr>
    <th>Wildcard</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>*</code></td>
    <td>Refers to an unlimited number of all characters</td>
  </tr>
  <tr>
    <td align="center"><code>?</code></td>
    <td>Used to refer to one specific character that can be any character. <code>ls c?t</code> would match cat as well as cut</td>
  </tr>
  <tr>
    <td align="center"><code>[auo]</code></td>
    <td>Refers to one character that may be selected from the range that is specified between square brackets. <code>ls c[auo]t</code> would match cat, cut, and cot.</td>
  </tr>
</table><br>
<br>
Working W/Absolute and Relative Pathnames<br>
An absolute filename, or absolute path, is a complete path reference to the file or directory you want to work with. This pathname starts with the root directory, followed by all subdirectories up to the actual filename. No matter what your current directory is, absolute filenames will always work. <code>/var/log/httpd/error_log</code><br>
<br>
A relative filename is relative to the current directory as shown with the <code>pwd</code> command. It contains only the elements that are required to get from the current directory up to the item you need.<br>
<br>
Listing Files and Directories<br>
<table>
  <tr>
    <th>Command</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>ls -l</code></td>
    <td>Shows a long listing, which includes information about file properties, such as creation date and permissions.</td>
  </tr>
  <tr>
    <td align="center"><code>ls -a</code></td>
    <td>Shows all files, including hidden files.</td>
  </tr>
  <tr>
    <td align="center"><code>ls -ltra</code></td>
    <td>Shows all files, including hidded files sorted on modification date. Most recently modified files last in the list.</td>
  </tr>
  <tr>
    <td align="center"><code>ls -d</code></td>
    <td>Shows the names of directories, not the contents of all directories that match the wildcards that have been used with the <code>ls</code> command.</td>
  </tr>
  <tr>
    <td align="center"><code>ls -R</code></td>
    <td>Shows the names of directories, not the contents of all directories that match the wildcards that have been used with the <code>ls</code> command.</td>
  </tr>
</table><br>
<br>
Copying Files<br>
Copy files using the <code>cp</code> command. Just use <code>cp /path/to/file /path/to/destination</code>. To copy the file <code>/etc/hosts</code> to the <code>/tmp</code> directory for instance, use <code>cp /etc/hosts /tmp</code>.<br>
<br>
With the <code>cp</code> command, you can also copy an entire subdirectory, with its contents and everything within it. Use the <code>-R</code> option, which stands for recursive. To copy the directory <code>/etc</code> and everything in it to <code>/tmp</code>, you would, for instance, use the command <code>cp -R /etc /tmp</code>. If you want to make sure that you keep the current permissions, use the <code>-a</code> option, which has cp work in archive mode.<br>
<br>
A special case when working with <code>cp</code> are hidden files. By default, hidden files are not copied over. There are three solutions to work with hidden files:
<ul>
<li><code>cp /directory/.* /tmp</code> This copies all files that have a name string with a dot<code>.</code> to <code>/tmp</code></li>
<li><code>cp -a /directory/ .</code> This copies the entire directory <code>/directory</code>, including its contents, to the current directory.</li>
<li><code>cp -a /directory/. .</code> This copies all files, regular and hidden, to the current directory.</li>
</ul><br>
<br>
Moving Files<br>
To move files, you use the <code>mv</code> command. This command removes the file from its current location and puts it in the new location. You can also use <code>mv</code> to rename a file.<br>
<br>
<ul>
<li><code>my file1 /tmp</code> Moves file1 from the current directory to <code>/tmp</code></li>
<li><code>mkdir directory1; mv directory1 /tmp</code> Creates directory1 and moves it to <code>/tmp</code></li>
<li><code>my file1 file1-NEW</code> Renames file1 to file1-NEW</li>
</ul><br>
<br>
Deleting Files<br>
To delete files and directories, you use the <code>rm</code> command. When used on a single file, the single file is removed. You can also use it on directories that contain files, use the <code>-R</code> option, which stands for recursive.