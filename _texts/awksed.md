---
layout: page
title: awk sed micro-primer
---

<code>awk</code>: a field-oriented pattern processing language<br>
<br>
Awk breaks each line of input passed to it into fields. By default, a field is a string of consecutive characters delimited by whitespace, though there are options for changing this. Awk parses and operates on each separate field. This makes it ideal for handling structured text files, especially tables, or data organized into consistent chunks, such as rows and columns.
<pre>
# /bin/echo one two | /bin/awk '{print $1}'
one

# /bin/echo one two | /bin/awk '{print $2}'
two

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

<code>sed</code>: a non-interactive text file editor<br>