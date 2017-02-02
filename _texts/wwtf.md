---
layout: page
title: working with text files
---

Common Text File-Related Tools
<table>
  <tr>
    <th>Command</th>
    <th>Explanation</th>
  </tr>
  <tr>
    <td align="center"><code>less</code></td>
    <td>Opens the text file in a pager, which allows for easy reading of the text file</td>
  </tr>
  <tr>
    <td align="center"><code>cat</code></td>
    <td>Dumps the contents of the text file to the screen</td>
  </tr>
  <tr>
    <td align="center"><code>head</code></td>
    <td>Shows first 10 lines of the file</td>
  </tr>
  <tr>
    <td align="center"><code>tail</code></td>
    <td>Shows last 10 lines of the file</td>
  </tr>
  <tr>
    <td align="center"><code>cut</code></td>
    <td>Used to filter specific columns or characters from a text file</td>
  </tr>
  <tr>
    <td align="center"><code>sort</code></td>
    <td>Sorts contents of a text file</td>
  </tr>
  <tr>
    <td align="center"><code>wc</code></td>
    <td>Counts the number of lines, words, and characters in a file</td>
  </tr>
</table><br>
<br>
Apart from using these commands on a text file, they may also prove very useful when used in pipes <code> | </code>. <code>ps aux | less</code> sends the output of the command <code>ps aux</code> to the pager <code>less</code> to allow for easy reading.<br>
<br>
Doing More W/<code>less</code><br>
The <code>less</code> utility offers an easy way to read the contents of text files. To open the contents of a text file in less, just type <code>less</code> followed by the name of the file you want to see, as in <code>less /etc/passwd</code>. Type <code>q</code> to quit less. Use <code>/<i>string</i></code> for a forward search and <code>?<i>string</i></code> for a backward search. Repeat the last search by using <code>n</code>.<br>
<br>
Showing File Contents W/<code>cat</code><br>
Using <code>cat</code> is simple, just type <code>cat</code> followed by the name of the file you want to see. For instance, <code>cat /etc/passwd</code> to show the contents of <code>/etc/passwd</code> file. The <code>tac</code> utility gives the inversed results of <code>cat</code>, i.e. reverse, or last line first.<br>
<br>
First of Last Lines W/<code>head</code> and <code>tail</code><br>
Using <code>head</code> on a text file will show by default the first 10 lines of that file. Using <code>tail</code> on a text file shows the last 10 lines by default. You can adjust the number of lines that are shown by adding <code>-n</code> followed by the number you want to see. So, <code>tail -n 5 /etc/passwd</code> shows the last five lines of the <code>/etc/passwd</code> file. Another useful option for <code>tail</code> is <code>-f</code>. This option starts by showing the last 10 lines of the file you've specifiedm but it refreshes the display as new lines are added to the file. This is convenient for monitoring log files such as <i>/var/log/messages</i>; <code>tail -f /var/log/messages</code>.