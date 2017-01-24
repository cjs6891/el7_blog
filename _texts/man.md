---
layout: page
title: /usr/bin/man
---

Using <code>--help</code><br>
The quickest way to get an overview of how to use a command is by running the command with the <code>--help</code> option.<br>
<pre>
<code>
[root@el7_blog.local]# man --help
man, version 1.6f

usage: man [-adfhktwW] [section] [-M path] [-P pager] [-S list]
        [-m system] [-p string] name ...

  a : find all matching entries
  c : do not use cat file
  d : print gobs of debugging information
  D : as for -d, but also display the pages
  f : same as whatis(1)
  h : print this help message
  k : same as apropos(1)
  K : search for a string in all pages
  t : use troff to format pages for printing
  w : print location of man page(s) that would be displayed
      (if no name given: print directories that would be searched)
  W : as for -w, but display filenames only

  C file   : use `file' as configuration file
  M path   : set search path for manual pages to `path'
  P pager  : use program `pager' to display pages
  S list   : colon separated section list
  m system : search for alternate system's man pages
  p string : string tells which preprocessors to run
               e - [n]eqn(1)   p - pic(1)    t - tbl(1)
               g - grap(1)     r - refer(1)  v - vgrind(1)

</code>
</pre>

The historical Linux Programmer’s Manual<br>
<code>man man-pages</code><br>

<table>
  <tr>
    <th>Section</th>
    <th>Content Type</th>
  </tr>
  <tr>
    <td>1</td>
    <td>User Commands</td>
  </tr>
  <tr>
    <td>2</td>
    <td>System Calls</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Library Functions</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Special Files</td>
  </tr>
  <tr>
    <td>5</td>
    <td>File Formats</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Games</td>
  </tr>

  <tr>
    <td>7</td>
    <td>Conventions, Standards, and Miscellaneous</td>
  </tr>
  <tr>
    <td>8</td>
    <td>System Administration and Privileged Commands</td>
  </tr>
  <tr>
    <td>9</td>
    <td>Linux Kernel API</td>
  </tr>
</table>

<p>To distinguish identical topic names in different sections, man page references include the section number in parentheses after the topic. <code>passwd(1)</code> describes the command to change passwords, while <code>passwd(5)</code> explains the <code>/etc/passwd</code> file format for storing local user accounts. </p>

<p><code>man passwd</code> displays <code>passwd(1)</code> by default<br>
<code>man 5 passwd</code> displays <code>passwd(5)</code>
</p>

<p><code><i>/STRING</i></code> Searches forward (down) for <i>STRING</i> in the man page<br>
When performing searches, <i>STRING</i> allows regular expression syntax.
</p>

<p>A keyword search of man pages is performed using <code># man -k <i>KEYWORD</i></code>, which displays a list of keyword-matching man page topics with section numbers.<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1482960859.png" alt="" style="">
The <code>man -K </code>option performs a full-text page search, not just titles and descriptions like the <code># man -k </code>option.
</p>