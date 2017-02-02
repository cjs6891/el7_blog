---
layout: page
title: regular expression primer
---

A regular expression is a search pattern that allows you to look for specific text in an advanced and flexible way.<br>
<br>
Using Line Anchors<br>
The type of regular expression that specifies where in a line of output the result is expected is known as a line anchor. To show lines that start with text you are looking for, you can use the regular expression <code>^</code>. For instance, <code>grep ^root /etc/passwd</code> indicates you are looking only for lines that have <i>root</i> at the beginning.
<pre>
<code>
grep '^root' /etc/passwd
root:x:0:0:root:/root:/bin/bash
</code>
</pre>
Another regular expression that relates to the position of the specific text in a specific line is <code>$</code>, which states the lines end with some text. For instance, <code>grep 'halt$' /etc/passwd</code> indicates you are looking only for lines that have <i>halt</i> at the end.
<pre>
<code>
grep 'halt$' /etc/passwd
halt:x:7:0:halt:/sbin:/sbin/halt
</code>
</pre>