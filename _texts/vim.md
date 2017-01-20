---
layout: page
title: vi/vim
---

The only text editor that is always available is <code>vi</code>. An important concept when working with <code>vi/vim</code> is that it uses different modes. These modes often cause confusion because in command mode you can just enter a command and you cannot change the contents of a text file. To change the contents of a text file, you need to get to input mode. 

<table>
  <tr>
    <th><code>vi/vim</code> command</th>
    <th>Explanation</th>
  </tr>
  <tr>
    <td align="center"><code>Esc</code></td>
    <td align="left">Switches from input mode to command mode.</td>
  </tr>
  <tr>
    <td align="center"><code>i, a</code></td>
    <td align="left">Switches from command mode to input mode at <code>i</code> or after <code>a</code> the curent cursor position</td>
  </tr>
  <tr>
    <td align="center"><code>o</code></td>
    <td align="left">Opens a new line below the current cursor position and goes to input mode.</td>
  </tr>
  <tr>
    <td align="center"><code>:wq</code></td>
    <td align="left">Writes the current file and quits.</td>
  </tr>
  <tr>
    <td align="center"><code>:q!</code></td>
    <td align="left">Quits the file without applying any changes.</td>
  </tr>
  <tr>
    <td align="center"><code>:w <i>filename</i></code></td>
    <td align="left">Writes the current file with a new <i>filename</i></td>
  </tr>
  <tr>
    <td align="center"><code>dd</code></td>
    <td align="left">Deletes the current line.</td>
  </tr>
  <tr>
    <td align="center"><code>yy</code></td>
    <td align="left">Copies the current line.</td>
  </tr>
  <tr>
    <td align="center"><code>P</code></td>
    <td align="left">Pastes the current selection.</td>
  </tr>
  <tr>
    <td align="center"><code>v</code></td>
    <td align="left">Enters visual mode, allowing you to select a block of text using the arrow keys. Use <code>d</code> to cut, or <code>y</code> to copy the selection.</td>
  </tr>
  <tr>
    <td align="center"><code>u</code></td>
    <td align="left">Undoes the last command, repeat as needed.</td>
  </tr>
  <tr>
    <td align="center"><code>Ctrl+r</code></td>
    <td align="left">Redoes the last undo.</td>
  </tr>
  <tr>
    <td align="center"><code>gg</code></td>
    <td align="left">Goes to the first line in the document.</td>
  </tr>
  <tr>
  <tr>
    <td align="center"><code>G</code></td>
    <td align="left">Goes to the last line in the document.</td>
  </tr>
  <tr>
    <td align="center"><code>/<i>string</i></code></td>
    <td align="left">Searches for <i>string</i> from the current cursor position forward.</td>
  </tr>
  <tr>
    <td align="center"><code>?<i>string</i></code></td>
    <td align="left">Searches for <i>string</i> from the current cursor position backward.</td>
  </tr>
  <tr>
    <td align="center"><code>^</code></td>
    <td align="left">Goes to the first position in the current line.</td>
  </tr>
  <tr>
    <td align="center"><code>$</code></td>
    <td align="left">Goes to the last position in the current line.</td>
  </tr>
  <tr>
    <td align="center"><code>!ls</code></td>
    <td align="left">Adds the output of <code>ls</code> (<i>or any other command</i>) in the current file'</td>
  </tr>
  <tr>
    <td align="center"><code>:%s/old/new/g</code></td>
    <td align="left">Replaces <i>ALL</i> occurrences of <i>old</i> with <i>new</i>.</td>
  </tr>
</table>