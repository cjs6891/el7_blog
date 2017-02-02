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
</table>
Apart from using these commands on a text file, it may also prove very useful to us a pipe <code> | </code>. <code>ps aux | less</code> sends the output of the command <code>ps aux</code> to the pager <code>less</code> allowing for easy reading.<br>
<br>
Doing More W/<code>less</code><br>
The <code>less</code> utility offers an easy way to read the contents of text files. To open the contents of a text file in less, just type <code>less</code> followed by the name of the file you want to see, as in <code>less /etc/passwd</code>. Type <code>q</code> to quit less. Use <code>/<i>string</i></code> for a forward search and <code>?<i>string</i></code> for a backward search. Repeat the last search by typing an <code>n</code>.<br>
<br>
Showing File Contents W/<code>cat</code><br>
Using <code>cat</code> is simple, just type <code>cat</code> followed by the name of the file you want to see. For instance, <code>cat /etc/passwd</code> to show the contents of <code>/etc/passwd</code> file. The <code>tac</code> utility gives the inversed results of <code>cat</code>, i.e. reverse, or last line first.<br>
<br>
First or Last Lines W/<code>head</code> and <code>tail</code><br>
Using <code>head</code> on a text file will show by default the first 10 lines of that file. Using <code>tail</code> on a text file shows the last 10 lines by default. You can adjust the number of lines that are shown by adding <code>-n</code> followed by the number you want to see. So, <code>tail -n 5 /etc/passwd</code> shows the last five lines of the <code>/etc/passwd</code> file. Another useful option for <code>tail</code> is <code>-f</code>. This option starts by showing the last 10 lines of the file you've specified but it refreshes the display as new lines are added to the file. This is convenient for monitoring log files such as <i>/var/log/messages</i>; <code>tail -f /var/log/messages</code>.<br>
<br>
When combining <code>head</code> and <code>tail</code>, you can do smart things... For instance, you want to see line number 11 of the <i>/etc/passwd</i> file. Use <code>head -n 11 /etc/passwd | tail -n 1</code>. The command before the pipe shows the first 11 lines from the file. The result is sent to the pipe, and on that result <code>tail -n 1</code> is used, which leads to only line number 11 being displayed.<br>
<br>
Filtering Columns W/<code>cut</code><br>
To filter out a specific field, the <code>cut</code> command is useful. To do this, use the <code>-d</code> option to specify the field delimiter followed by <code>-f</code> with the number of the specific filed you want to filter out. So, to filter out the first field of <i>/etc/passwd</i> use <code>cut -d : -f 1 /etc/passwd</code>.<br>
<br>
Sorting File Contents and/or Output W/<code>sort</code><br>
<code>sort</code> is a very useful command for sorting text. If you type <code>sort /etc/passwd</code>, for instance, the contents of the <i>/etc/passwd</i> file is sorted in alphabetic order. You can also use the <code>sort</code> command on output of a command, as in <code>cut -d : -f 1 /etc/passwd | sort</code>, which sorts the contents of the first column in the <i>/etc/passwd</i> file.<br>
<br>
The <code>sort</code> command sorts in alphabetic order by default. Obviously in some cases, that isn't convenient. The <code>sort</code> command offers different options to help sorting these specific types of data. For instance, <code>cut -d : -f 3 /etc/passwd | sort -n</code> to sort the third field of <i>/etc/passwd</i> in numeric order. It can also be useful to sort in reverse order <code>cut -d : -f 3 /etc/passwd | sort -rn</code>.<br>
<br>
You can also use the <code>sort</code> command and specify which column you want to sort. Use <code>sort -n -k3 -t : /etc/passwd</code>, for instance, which uses the field separator : to numericlly sort the third column of the <i>/etc/passwd</i> file.<br>
<br>
Counting Lines, Words, and Characters W/<code>wc</code><br>
The <code>wc</code> command gives three different results: the number of lines, the number of words, and the number of characters. To get the specific line count use <code>wc -l</code>.
<pre>
<code>
# wc /etc/passwd
21   40 1008 /etc/passwd
# wc -l /etc/passwd
21 /etc/passwd
</code>
</pre>