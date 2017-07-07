---
layout: page
title: using essential tools
---

The Tape ARchiver <code>tar</code> utility is used to archive files. <br>

Creating Archives W/<code>tar</code><br>
To create an archive, you use the <code>tar -cf ArchiveName.tar /FilesToBeArchived</code> command. To see what's happening, verbose output use the <code>-v</code> option; <code>tar -cvf etc_directory.tar /etc</code>.<br>
<br>
Note:<br>
* It's good practice to create archive files with an extension such as <code>.tar</code> or <code>.tgz</code> for easy recognition. Not everyone does this... If you think a file is a tar archive, use the <code>file</code> command.<br>
<pre>
<code>
# file etc_directory.tar
etc_directory.tar: POSIX tar archive (GNU)
</code>
</pre><br>
While managing archives with tar, it is also possible to add a file to an existing archive, or to update an archive. To add files to an archive, you use the <code>-r</code> option. Use for instance <code>tar -rvf etc_directory.tar /root/System_Administration/</code> to add <code>/root/System_Administration/</code> to <code>etc_directory.tar</code>.<br>

To update a currently existing archive file, use the <code>-u</code> option. So <code>tar -uvf etc_directory.tar /root/System_Administration/</code> to write newer versions of all files in <code>/root/System_Administration/</code> to <code>etc_directory.tar</code>.<br>

Monitoring and Extracting tar Files<br>
Before extracting a file, it's good to know what might be expected. The <code>-t</code> option can be used to find out. Type for instance <code>tar -tvf etc_directory.tar | less</code> to see the contents of the <code>etc_directory.tar</code> archive.<br>

To extract the contents of an archive, use <code>tar -xvf ArchiveName.tar</code>. The archive will be extracted into the current working directory.<br>
<br>
Note:<br>
*This might not be what you want to accomplish, two solutions exist to extract the contents where you want:
<ul>

<li><code>cd</code> to the directory where you want to extract the archive</li>
<pre>
<code>
mkdir extraction_directory
cd extraction_directory/
tar -xvf ../etc_directory.tar
</code>
</pre>
<li>Use the <code>-C extraction_directory</code> option to specify the target directory, in our case <code>extraction_directory</code></li>
<code>tar -xvf etc_directory.tar -C /tmp/extraction_directory/</code>
</ul>
<br>
Apart from extracting an entire archive, it is also possible to extract one file out of the archive. Use <code>tar -xvf etc_directory.tar etc/hosts</code>.<br>
<br>
Note:<br>
*This might not be what you want to accomplish... To extract <code>etc/hosts</code> from <code>etc_directory.tar</code> to <code>/tmp</code> use:<br>
<code>tar -xvf etc_directory.tar -C /tmp etc/hosts</code>
<br>
Using Compression<br>
Originally, after creating an archive, it had to be compressed with a separate compression utility, such as <code>gzip</code> or <code>bzip2</code>. After creating <code>etc_directory.tar</code>, you can compress it with <code>gzip etc_directory.tar</code> replacing <code>etc_directory.tar</code> with <code>etc_directory.tar.gz</code> consuming significantly less space. As an alternative to using <code>gzip</code>, you can use the <code>bzip2</code> utility.<br>
<br>
To decompress files that have been compressed with <code>gzip</code> or <code>bzip2</code>, you can use the <code>gunzip</code> and <code>bunzip2</code> utilities.<br>
<br>
An alternative to using these utilities after <code>tar</code> would be to include the <code>-z</code>, gzip or <code>-j</code> bzip2 options when creating the tar archive. There is no reason to use these options when extracting. The <code>tar</code> utility will recognize the compression automatically and decompress it for you.<br>
<br>
Overview of <code>tar</code> Options
<table>
  <tr>
    <th>Option</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>c</code></td>
    <td>Creates an archive.</td>
  </tr>
  <tr>
    <td align="center"><code>v</code></td>
    <td>Shows verbose output while <code>tar</code> is working</td>
  </tr>
  <tr>
    <td align="center"><code>f</code></td>
    <td>Used to specify the name of the tar archive that is to be used.</td>
  </tr>
  <tr>
    <td align="center"><code>t</code></td>
    <td>Shows the contents of an archive.</td>
  </tr>
  <tr>
    <td align="center"><code>z</code></td>
    <td>Compresses the archive using <code>gzip</code>.</td>
  </tr>
  <tr>
    <td align="center"><code>j</code></td>
    <td>Compresses the archive using <code>bzip2</code>.</td>
  </tr>
  <tr>
    <td align="center"><code>x</code></td>
    <td>Extracts an archive.</td>
  </tr>
  <tr>
    <td align="center"><code>u</code></td>
    <td>Updates an archive, only newer files will be written to the archive.</td>
  </tr>
  <tr>
    <td align="center"><code>C</code></td>
    <td>Changes the working directory before performing the command.</td>
  </tr>
  <tr>
    <td align="center"><code>r</code></td>
    <td>Appends files to an archive.</td>
  </tr>
</table>