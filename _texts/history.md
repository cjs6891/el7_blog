---
layout: page
title: History
---


Bash is configured to keep the last 1,000 commands you have used. When a shell session is closed, the historyof that session is updated to the history file <code>.bash_history</code>. The file <code>.bash_history</code> is created in the home directory of the user who started a specific shell session. The <code>.bash_history</code> file is closed only when the shell session is closed; until that moment, all commands in the history are kept in memory.<br>
<br>
Working W/History:
<ul>
<li>Type <code>history</code> to show a list of all commands in the bash history.</li>
<li>Type <code>Ctrl+r</code> to open the prompt from which you can do a backward search in commands that you have previously used. Just type a part of the command you are looking for, and it will be displayed automatically. Type <code>Ctrl+r</code> again to search further backward based on the same search criteria.</li>
<li>Type <code>!<i>number</i></code> to execute a command with a specific <i>number</i> from history.</li>
<li>Type <code>!<i>sometext</i></code> to execute the last command that starts with <i>sometext</i>.<br>* Notice: W/<i>sometext</i> the command that was found is executed immediately, executing it may be potentially dangerous.</li>
</ul><br>
<br>
Note:<br>
*<code>history -c</code> wipes all history that is currently in memory, but it doesn't remove the <code>.bash_history</code> file from the home directory.<br>An alternative to deleting <code>.bash_history</code> is the command <code>history -w</code> after using <code>history -c</code>.