---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 3: Understanding Common TCP/IP Attacks"
---

<a href="#Legacy TCP/IP Vulnerabilities">3.2 Legacy TCP/IP Vulnerabilities</a><br>
<a href="#IP Vulnerabilities">3.3 IP Vulnerabilities</a><br>
<a href="#ICMP Vulnerabilities">3.4 ICMP Vulnerabilities</a><br>
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
<a name="IP Vulnerabilities"></a>
<b>IP Vulnerabilities</b><br>
The IP is a connectionless protocol that is mainly used to route information across the Internet. The role of IP is to provide best-effort services for the delivery of information to its destination. IP depends on upper-level TCP/IP suite layers to provide accountability and reliability. Layers above IP use the source address in an incoming packet to identify the sender. To communicate with the sender, the receiving station sends a reply by using the source address in the datagram. Because IP makes no effort to validate whether the source address in the packet that is generated by a node is actually the source address of the node, you can spoof the source address and the receiver will think the packet is coming from that spoofed address.<br>
<br>
Many programs for generating spoofed IP datagrams are available for free on the Internet, for example, hping lets you prepare spoofed IP datagrams with a simple one-line command, and you can send them to almost anybody in the world. You can also spoof at various other layers, for example, using ARP spoofing to link a MAC address to the IP address of a legitimate host on the network to divert the traffic that is intended for one station to someone else. The SMTP is also a target for spoofing the email source because SMTP does not verify the sender's address, so you can send any email to anybody pretending to be someone else. As a result, no packet can be trusted, and each packet must earn its trust through the network’s ability to classify and enforce policy.<br>
<br>
The following are some key IP address-based vulnerabilities that threaten network infrastructures:<br>
<br>
<ul>
<li><b>Man-in-the-middle attack:</b> An MITM attack intercepts a communication between two systems. Essentially, the attacker inserts a device into a network that grabs packets that are streaming past. Those packets are then modified and placed back on the network for forwarding to their original destination. An MITM attack can completely defeat sophisticated authentication mechanisms because the attacker waits until after a communication session is established, which means that authentication has been completed, before starting to intercept packets. An MITM attack does not directly threaten your network's stability, but it is an exploit that can target a specific destination IP address. A form of MITM is called "eavesdropping." Eavesdropping differs only in that the perpetrator just copies IP packets off the network without modifying them in any way.</li><br>
<li><b>Session hijacking:</b> Session hijacking is a twist on the MITM attack. The attacker gains physical access to the network, initiates an MITM attack and then hijacks that session. In this manner, an attacker can illicitly gain full access to a destination computer by assuming the identity of a legitimate user. The legitimate user sees the login as successful but then is cut off. Subsequent attempts to log back in might be met with an error message that indicates that the user ID is already in use.</li><br>
<li><b>IP address spoofing:</b> Attackers spoof the source IP address in an IP packet. IP spoofing can be used for several purposes. In some scenarios, an attacker might want to inspect the response from the target victim (nonblind spoofing); in other cases the attacker might not care (blind spoofing). Blind IP address spoofing is most frequently used in DoS attacks. Some reasons for nonblind spoofing include sequence-number prediction, hijacking an authorized session, and determining the state of a firewall.</li><br>
<li><b>DoS attack:</b> In a DoS attack, an attacker attempts to prevent legitimate users from accessing information or services. Since the second half of 2010, DoS has been one of the most common attacks in the United States. By targeting your computer and its network connection, or the computers and network of the sites that you are trying to use, an attacker may be able to prevent you from accessing email, websites, online accounts, or other services that rely on the affected computers. Common types of DoS attacks include packet floods and service buffer overflow attacks. Other types of DoS attacks rely on specific flaws in various applications and operating systems, such as the "teardrop" attack which can crash older operating systems. For example, in a teardrop attack, the attacker sends IP fragmented packets to a target machine. Since the machine receiving such packets cannot reassemble them due to a bug in TCP/IP fragmentation reassembly, the packets overlap one another, crashing the target network device.</li><br>
<li><b>DDoS attack:</b> A DDos attack is a DoS attack that features a simultaneous, coordinated attack from multiple source machines. The best-known example of a DDoS attack is the "smurf" attack. Attackers have been known to use four programs to launch DDoS attacks: Trinoo, TFN, TFN2K, and Stacheldraht.</li><br>
<li><b>Smurf attack:</b> A smurf attack exploits the IP broadcast addressing to create a DoS. This attack uses the ICMP. One of the utilities that are embedded in ICMP is ping which is commonly used to test the availability of certain destinations. The attacker installs smurf on a hacked computer. The hacked machine starts continuously pinging one or more networks—with all their attached hosts—using IP broadcast addresses. Every host that receives the broadcast ping message is obliged to respond with its availability. The result is that the hacked machine gets overwhelmed with inbound ping responses.</li><br>
<li><b>Resource exhaustion attacks:</b> Resource exhaustion attacks are forms of DoS attacks. These attacks cause the server’s or network's resources to be consumed to the point where the service is no longer responding, or the response is significantly reduced. By targeting IP routers, an attacker may adversely affect the integrity and availability of the network infrastructure, including end-to-end IP connectivity. Router resources that are commonly affected by packet flood attacks include the following: CPU, packet memory, route memory, network bandwidth, and vty lines.</li>
</ul>
<br>
<a name="ICMP Vulnerabilities"></a>
<b>ICMP Vulnerabilities</b><br>
ICMP is a connectionless protocol that does not use any port number and works in the network layer. ICMP was not designed to transfer data in the same way as TCP and UDP. Rather, ICMP was intended to carry diagnostic messages to ensure that links were active and to report error conditions when routes, hosts, and ports are inaccessible. ICMP datagrams are often associated with commands that are used by network administrators, such as <code>ping</code> (ICMP echo request) and <code>traceroute</code> (ICMP TTL expired in transit). Most ICMP traffic is generated by routers, firewalls, and endpoints to detect and diagnose network connection issues. ICMP is used to inform the sender that a problem has occurred while delivering the data. For example, if a host is unable to reach another host on the local network, the sender might receive an ICMP Destination Host Unreachable message. If a network link is down, a router may respond to the sender with an ICMP Destination Network Unreachable message. If traffic is blocked by a firewall, the firewall may respond with an ICMP Host Administratively Prohibited message. Every network device must implement ICMP, but some administrators block ICMP to prevent attackers from gathering information about their internal network.<br>
<br>
All types of ICMP traffic are interesting to the security analyst. Either the traffic is user-generated (as in the case of ICMP echo requests) or generated by network devices (as in the case of ICMP Destination Network Unreachable). In the first case, it is beneficial to know when someone, especially inside the network, is generating ICMP traffic to scan the network. Traffic that is generated by network devices indicates network issues and outages.<br>
<br>
The following are the security issues of ICMP messages that a security analyst needs to understand:<br>
<br>
<ul>
<li><b>Reconnaissance and scanning:</b> ICMP can be used to launch information gathering attacks. Attackers can use different methods within the ICMP to find out live host, network topology, and OS fingerprinting, and determine the state of a firewall.<br>
 - <b>ICMP unreachables:</b> ICMP unreachables are commonly used by attackers to perform network reconnaissance. In cyber security, network reconnaissance refers to the act of scanning the target network to gather information about the target. For example, during a protocol or port scan, if an ICMP Protocol Unreachable is received, the attacker will know that protocol is not in use on the target device. If an ICMP Port Unreachable is received, the attacker will know that port is not in use on the target device.<br>
 - <b>ICMP mask reply:</b> A feature that malicious insiders or outsiders can use to map your IP network. This feature allows the router to tell a requesting endpoint what the correct subnet mask is for a given network.<br>
 - <b>ICMP redirects:</b> A router sends an IP redirect to notify the sender of a better route to the destination. The intended purpose of this feature was for a router to send redirects to the hosts on its directly connected networks. However, an attacker can leverage this feature to send an ICMP redirect message to the victim's host, luring the victim's host into sending all traffic through a router that is owned by the attacker. ICMP redirect attack is an example of an MITM attack, where an attacker will act as the middle man for all communication from the source to the destination.<br>
 - <b>ICMP router discovery:</b> IRDP allows hosts to locate routers that can be used as a gateway to reach IP-based devices on other networks. Because IRDP does not have any form of authentication, it is impossible for end hosts to tell whether the information they receive is valid or not. Therefore, an attacker can perform an MITM attack using IRDP. Attackers can also spoof the IRDP messages to add bad route entries into a victim’s routing table, so that the victim’s host will forward the packets to the wrong address, and be unable to reach other networks, resulting in a form of a DoS attack.<br>
 - <b>Firewalk:</b> Firewalking is an active reconnaissance technique that employs traceroute-like techniques to analyze IP packet responses to determine the gateway ACL filters and map out the networks. The firewalking technique works by sending out TCP or UDP packets with a TTL that is one greater than the targeted gateway. If the gateway allows the traffic, it will forward the packets to the next hop where they will expire and elicit an ICMP Time Exceeded message. If the gateway host does not allow the traffic, it will likely drop the packets and the attacker will see no response.
</li><br>
<li><b>ICMP tunneling:</b> An ICMP tunnel, also known as ICMPTX, establishes a covert connection between two remote computers, using ICMP echo requests and reply packets. ICMP tunneling can be used to bypass firewalls rules through obfuscation of the actual traffic inside the ICMP packets. Without proper deep packet inspection or log review, network administrators will not be able to detect this type of tunneling traffic through their network. A common ICMP tunneling program is LOKI that uses ICMP as a tunneling protocol for a covert channel. By using LOKI, an attacker can transmit data secretly by hiding their malicious traffic inside ICMP so that the networking devices cannot detect the transmission.</li><br>
<li><b>ICMP-based OS fingerprinting:</b> OS fingerprinting is the process of learning which operating system is running on a device. ICMP can be used to perform an active OS fingerprint scan. For example, if the ICMP reply contains a TTL value of 128, it is probably a Windows machine, and if the ICMP reply contains a TTL value of 64, it is probably a Linux-based machine.</li><br>
<li><b>Denial of service attacks:</b> DoS attacks that use ICMP include the following:<br>
<br>
 - <b>ICMP flood attack:</b> The attacker overwhelms the targeted resource with ICMP echo request (ping) packets, large ICMP packets, and other ICMP types to significantly saturate and slow down the victim's network infrastructure. The following figure is an example of the ICMP Flood.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515111722.png" alt="" style="">
<br>
 - <b>Smurf attack:</b> In a smurf attack, an attacker broadcasts many ICMP echo request packets using a spoofed source IP address (which is the victim's IP address) to a network using an IP broadcast address. If networking devices do not filter this traffic, then they will be broadcasted to all computers in the network. The victim’s network will get congested with all the ICMP echo replies traffic, which will bring down the productivity of the entire victim's network. This exchange is illustrated in the following figure.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515111886.png" alt="" style="">
<br>
</li><br>
</ul>