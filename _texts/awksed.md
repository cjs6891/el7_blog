---
layout: page
title: awk sed micro-primer
---

<code>awk</code>: a field-oriented pattern processing language<br>
<br>
Awk breaks each line of input passed to it into fields. By default, a field is a string of consecutive characters delimited by whitespace, though there are options for changing this. Awk parses and operates on each separate field. This makes it ideal for handling structured text files, especially tables, or data organized into consistent chunks, such as rows and columns.
<pre>
# print first field $1
# /bin/echo one two | /bin/awk '{print $1}'
one

# print second field $2
# /bin/echo one two | /bin/awk '{print $2}'
two

# print all fields $0
# /bin/echo one two | /bin/awk '{print $0}'
one two

 - - - - - - - - - - 

# /bin/echo one two > /tmp/output.txt

# /bin/echo three four >> /tmp/output.txt

# /bin/awk '{print $1}' /tmp/output.txt
one
three

# /bin/awk '{print $2}' /tmp/output.txt
two
four

# /bin/awk '{print $0}' /tmp/output.txt
one two
three four
</pre>

Input Field Separator Variable<br>
Awk reads and parses each line from input based on the whitespace character by default and sets the variables $1,$2 and etc. Awk FS variable is used to set the field separator for each record. Awk FS can be set to any single character or regular expression. You can use input field separator using one of the following two options:<br>

<code>awk -F 'FS' 'commands' inputfilename</code><br>
<code>awk 'BEGIN{FS="FS";}'</code><br>

<pre>
# /bin/cat /etc/passwd
root:x:0:0:root:/root:/bin/bash

 - - - 

,# /bin/awk -F ':' '{print $1", "$6", "$7}' /etc/passwd
root, /root, /bin/bash

 -or-

# /bin/awk 'BEGIN{FS=":";} {print $1", "$6", "$7}' /etc/passwd
root, /root, /bin/bash
</pre>

<code>sed</code>: a non-interactive text file editor<br>
sed stands for stream editor. It is a very essential tool for text processing. It is a marvelous utility that can play around regular expressions. A well-known usage of the sed command is for text replacement.<br>
<br>
Replace Occurrences of a String With Another String<br>
<pre>
# sed 's/pattern/replace_string/' file

 -or-

# cat file | sed 's/pattern/replace_string/' file
</pre>
The default sed behavior is to write to STDOUT, use the <code>-i</code> option to save the changes along with the substitutions to the same file. Make sure you know what you're doing before using <code>-i</code>, it might be difficult to revert file modifications that are applied; redirection is common for most users.
<pre>
# sed -i 's/text/replace/' file

# sed 's/text/replace/' file > newfile
</pre>

The previous sed command <code>sed 's/text/replace/' file</code> will replace the first occurrence of the pattern in each line. In order to replace every or all occurrences, add the <code>g</code> parameter at the end <code>sed 's/pattern/replace_string/g' file</code>.

[USEFUL ONE-LINE SCRIPTS FOR SED](http://www.pement.org/sed/sed1line.txt){:target="_blank"}