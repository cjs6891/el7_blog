---
layout: page
title: Red Hat Certified System Administrator
---

[Download CentOS Linux ISO images](https://wiki.centos.org/Download){:target="_blank"}

<b>Executing Commands</b><br>
The purpose of the Linux shell is that it provides an environment in which commands can be executed. The shell takes care of interpreting the command that a user has entered correctly. To do this, the shell makes a difference between three kinds of commands:<br>
<br>
<ul>
<li>Aliases</li>
<li>Internal Commands</li>
<li>External Commands</li>
</ul>
<br>
An alias is a command that a user can define as needed. Some aliases are provided by default; type <code>alias</code> on the command line to get an overview. To define an alias, use <code>alias newcommand='oldcommand'</code>, as in the default alias ll=’ls -l --color=auto’. Aliases are executed before anything else.<br>
<br>
<code>
<pre>
# alias
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
</pre>
</code>
