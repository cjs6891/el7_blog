---
layout: page
title: analyze text with grep
---

grep, "general regular expression parser".<br>
<br>
Most useful <code>grep</code> commands
<table>
  <tr>
    <th>Option</th>
    <th>Use</th>
  </tr>
  <tr>
    <td align="center"><code>-i</code></td>
    <td>No case sensitivity, matches upper and lower case.</td>
  </tr>
  <tr>
    <td align="center"><code>-v</code></td>
    <td>Only shows lines that <i>DO NOT</i> contain the regular expression.</td>
  </tr>
  <tr>
    <td align="center"><code>-r</code></td>
    <td>Search files in the current directory and all subdirectories.</td>
  </tr>
  <tr>
    <td align="center"><code>-e</code></td>
    <td>Search for line matching more than one regular expression.</td>
  </tr>
  <tr>
    <td align="center"><code>-A <i><NUMBER></i></code></td>
    <td>Show <i><NUMBER></i> of lines after the matching regular expression.</td>
  </tr>
  <tr>
    <td align="center"><code>-B <i><NUMBER></code></td>
    <td>Show <i><NUMBER></i> of lines before the matching regular expression.</td>
  </tr>
</table>