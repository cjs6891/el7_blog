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
Escaping W/Regular Expressions<br>
When using regular expressions it's a good idea to use escaping to prevent shell interpretation. To prevent shell interpretation from ever happening, put the regular expression between quotes. For example, <code>grep '^root' /etc/passwd</code> instead of <code>grep ^root /etc/passwd</code>.<br>
<br>
Wildcards and Multipliers<br>
To start with there is a <code> . </code> regular expression. This is used as a wildcard character to look for one specific character. So, the regular expression <code>r.t</code> would match the strings <i>rat</i>, <i>rot</i>, and <i>rut</i>.<br>
<br>
In some cases, you might want to be more specific about the characters you are looking for. For instance, the regular expression <code>r[aou]t</code> matches the strings <i>rat</i>, <i>rot</i>, and <i>rut</i> as well.<br>
<br>
Another useful regular expression is the multiplier <code> * </code>. This matches zero or more of the previous character.<br>
<br>
If you know exactly how many of the previous character you are looking for, you can specify a number also, as in <code>re\{2\}d</code>, which would match <i>red</i> as well as <i>reed</i>. The last regular expression that is useful to know about is <code> ? </code>, which matches zero or one of the previous character.<br>
<br>
Significant Regular Expressions
<table>
  <tr>
    <th>Regular Expression</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>^text</code></td>
    <td>Line starts with text.</td>
  </tr>
  <tr>
    <td align="center"><code>text$</code></td>
    <td>Line ends with text.</td>
  </tr>
  <tr>
    <td align="center"><code> . </code></td>
    <td>Wildcard, matches any single character.</td>
  </tr>
  <tr>
    <td align="center"><code>[abc]</code></td>
    <td>Matches <i>a</i>, <i>b</i>, or <i>c</i>.</td>
  </tr>
  <tr>
    <td align="center"><code> * </code></td>
    <td>Matches 0 to an infinite number of the previous character.</td>
  </tr>
  <tr>
    <td align="center"><code>\{2\}</code></td>
    <td>Matches exactly 2 of the previous character.</td>
  </tr>
  <tr>
    <td align="center"><code>\{1,3\}</code></td>
    <td>Matches a minimum of 1 and a maximum of 3 of the previous character.</td>
  </tr>
  <tr>
    <td align="center"><code>colou?r</code></td>
    <td>Match 0 or 1 of the previous character. This makes the previous character optional, which in this example would match both <i>color</i> and <i>colour</i></td>
  </tr>
</table>