---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 3: Understanding Common TCP/IP Attacks"
---

<a href="#Legacy TCP/IP Vulnerabilities">3.2 Legacy TCP/IP Vulnerabilities</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>
<a href="#">3.</a><br>


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
<a name=""></a>

<a name="Legacy TCP/IP Vulnerabilities"></a>
<b>Legacy TCP/IP Vulnerabilities</b><br>
The TCP/IP protocol suite (RFC 793), developed under the sponsorship of the U.S. Department of Defense, was designed to work in a trusted environment. The model was developed as a flexible, fault-tolerant set of protocols that were robust enough to avoid failure if one or more nodes went down. The focus was on solving the technical challenges of moving information quickly and reliably, not to secure it.<br>
<br>
The designers of this original network never envisioned the Internet as it exists today. The problem is that weakness is inherent in the design itself and eradicating them is difficult. Many early TCP/IP protocols are now considered insecure and vulnerable to various attacks, ranging from password sniffing to denial of service. As an example, TCP/IP is shipped with Berkley r-utilities. It is a set of tools featuring remote login (rlogin), remote copying (rcp), and remote command execution (rsh). These commands were developed for password-free access to UNIX machines only. Although the r-utilities tools have some advantages, they should be avoided because they can make access extremely insecure. Also, being inherent in the design means that universal cross-platform vulnerabilities are present in the very infrastructure of the Internet and most other networks, like LANs. The fact that TCP over IP is a low-level protocol means that all the higher-level protocols (for example, HTTP, Telnet, and SMTP) are vulnerable by inheritance (for example, hijacking a Telnet connection).<br>
<br>
The 1988 attack by the “Morris worm” was a wake-up call for the Internet’s architects, who had done their original work in an era before smart phones, before cyber cafes, before even the widespread adoption of the personal computer. The Morris worm attack was one of the first computer worms that were distributed via the Internet and it was a precursor to other well-known worm attacks including 1999's Melissa, 2001's Code Red, 2003's Slammer, and the SQL Sapphire/Slammer worm in January 2003. According to its creator, the Morris worm was not written to cause damage, but to gauge the size of the ARPANET. It worked by exploiting known vulnerabilities in common utilities including sendmail, which is email routing software, and finger, a tool that showed which users were logged on to the network. However, consequence of the code caused it to be more damaging: a computer could be infected multiple times and each additional process would slow the machine down, eventually to the point of being unusable. The Morris worm opened up computer security as a legitimate topic.<br>
<br>
Due to reliance on rsh (normally disabled on untrusted networks), fixes to sendmail, finger, the widespread use of network filtering, and improved awareness of the dangers of weak passwords, the Morris Worm type attacks should not succeed on a properly configured system today. But these virus and worm outbreaks have demonstrated that networked computers continue to be vulnerable to new attacks, despite the widespread deployment of antivirus software and firewalls.<br>
<br>
The TCP/IP suite has been modified and enhanced over the years. The protocol suite, consisting of four main protocols (IP, TCP, UDP, and ICMP), describes the ways in which devices communicate on TCP/IP networks, ranging from the way individual chunks of data, which are known as packets, are formatted, to the details of how those packets are routed through various networks to their final destinations. As a security analyst, you need an essential understanding of the protocol structures and their vulnerabilities. The following discussion will include the protocol relationships, and packet and datagram structures, providing details of the protocol vulnerabilities that are relevant to packet analysis.<br>
<br>

