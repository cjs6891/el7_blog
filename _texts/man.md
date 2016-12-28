---
layout: page
title: /usr/bin/man
---

The historical Linux Programmer’s Manual<br>
<code># man man-pages</code><br>

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

<p><code># man passwd</code> displays <code>passwd(1)</code> by default<br>
<code># man 5 passwd</code> displays <code>passwd(5)</code>
</p>

<p><code><i>/STRING</i></code> Searches forward (down) for <i>STRING</i> in the man page<br>
When performing searches, <i>STRING</i> allows regular expression syntax.
</p>

<p>A keyword search of man pages is performed using <code># man -k <i>KEYWORD</i></code>, which displays a list of keyword-matching man page topics with section numbers.<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1482960859.png" alt="" style="">
The <code># man -K </code>option performs a full-text page search, not just titles and descriptions like the <code># man -k </code>option.
</p>