---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 10: Understanding Common Endpoint Attacks"
---

<a href="#Classify Attacks, Exploits, and Vulnerabilities">10.2 Classify Attacks, Exploits, and Vulnerabilities</a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>
<a href="#">10. </a><br>

<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>


<a name="Classify Attacks, Exploits, and Vulnerabilities"></a>
<b>Classify Attacks, Exploits, and Vulnerabilities</b><br>
A vulnerability is a flaw or weakness in a system. An exploit is a method of leveraging a vulnerability to do harm. An attack is an attempt to exploit a vulnerability. Attacks may be successful or unsuccessful. If an exploit attempt is made against a system that is not vulnerable to the exploit, then the attack is unsuccessful, but it is still considered an attack. There are many ways that attacks, vulnerabilities, and exploits can be classified using different criteria. We will examine a few.<br>
<br>
<b>Client-Side vs. Server-Side Attacks</b><br>
Both clients and servers are endpoints. That is, they are hosts that run an operating system and applications, and they connect to the network via a TCP/IP stack. Both can be targeted by attacks. But the nature of the systems leads to differences in attack strategies, attack difficulty levels and potential impacts in the case of successful attacks.<br>
<br>
Servers may be directly exposed to the Internet. This makes them easily accessible to the threat actor. But servers tend to be hardened and their applications are properly patched, making them more difficult to attack. They also tend to be actively managed and monitored, making attack attempts and results more visible.<br>
<br>
Internal clients are normally protected from the Internet, making them difficult to reach directly. But, generally, clients do not receive the same amount of attention as servers. This makes them more susceptible to attacks. Also, clients are operated by end users who tend to be more susceptible to social engineering attacks. Delivering a malicious file via email and posting malicious content on websites can be very effective client-side attack methods.<br>
<br>
While the internal client is protected from connections originating from the Internet, they are often allowed to initiate connections themselves. If a client can be compromised, the client has the ability to "phone home" connecting from the inside to the malicious command and control systems. From there the threat actor can use the compromised client as a pivot to reach other systems on the internal network.<br>
<br>
<b>Remote Exploits vs. Local Exploits</b><br>
A remote exploit is one that works over the network without any prior access to the target system. The threat actor does not need an account on the vulnerable system to exploit the vulnerability.<br>
<br>
A local exploit requires prior access to the vulnerable system. Generally, the threat actor has access to an account on the system. Using their access to that account, they implement the local exploit. Most commonly, local exploits lead to privilege escalation. Either the account is given privileges beyond the intended policy for the account, or other access methods are enabled and those methods allow privileges beyond the intended policy for the account. Note that a local exploit does not necessarily require physical access to the system. Also, an attacker may use social engineering techniques to trick an authorized user into performing the local exploit.<br>
<br>
<b>Common Vulnerability Scoring System</b><br>
With both client-side vs. server-side attacks and remote vs. local exploits, we use a single metric to divide things into two different classes. CVSS v3.0 uses multiple criterion to produce a numerical score representing the severity of a vulnerability, and provide a qualitative representation of the aspects of the vulnerability. The CVSS base score includes eight metrics. The base score can further be refined using temporal metrics and environmental metrics. Full discussion of CVSS 3.0 is well beyond the scope of this discussion. But exposure to the metrics that are used in the CVSS base score can certainly help the security analyst to qualitatively differentiate varying attacks in effective ways.<br>
<br>