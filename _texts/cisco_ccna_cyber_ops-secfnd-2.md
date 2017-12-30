---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 2: Understanding the Network Infrastructure"
---

<a href="#Analyzing DHCP Operations">2.2 Analyzing DHCP Operations</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>
<a href="#">2.</a><br>


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

<a name="Analyzing DHCP Operations"></a>
<b>Analyzing DHCP Operations</b><br>
Various attacks are emerging that target the Dynamic Host Configuration Protocol or DHCP. In any organization with multiple DHCP clients, DHCP server availability is critical. It is important for security analysts to understand the DHCP messages that are exchanged between the DHCP server and the DHCP client, in order to effectively monitor, troubleshoot, and mitigate DHCP-based attacks. Moreover, when analyzing logs, identifying or correlating attack-related issues is easier for the security analyst who has a solid understanding of DHCP and how it functions.<br>
<br>
In large environments, manual address assignment can become an excessive administrative problem, especially for mobile devices that roam from one network to another many times each day. DHCP is a standardized network protocol for dynamically distributing IP addresses automatically, and setting other network configuration parameters, such as the subnet mask, default router, and DNS servers. With DHCP, computers request IP addresses and networking parameters automatically from a DHCP server, reducing the need for network administrators or users to manually configure these settings.<br>
<br>
In an enterprise environment, a DHCP server is usually a dedicated device; in smaller deployments or some branch offices, it can be configured on DHCP-capable switches or routers.<br>
<br>
DHCP employs a connectionless service model using UDP, and is implemented using the same two UDP port numbers as BOOTP (Bootstrap Protocol). In fact, DHCP is implemented as an option of BOOTP and uses BOOTP as its transport protocol. UDP port number 67 is the destination port of a DHCP server, and UDP port number 68 is used by the DHCP client.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514583034.png" alt="" style="">
<br>
Some of the most common messages that are exchanged between the DHCP server and the client are as follows:<br>
<br>
<ul>
<li>DHCPDISCOVER</li><br>
<li>DHCPOFFER</li><br>
<li>DHCPREQUEST</li><br>
<li>DHCPACK</li>
</ul>
<br>
When a computer or other networked device connects to a network, the DHCP client software sends out a DHCPDISCOVER message on its local physical subnet over UDP port 67, which is a broadcast message to locate available servers.<br>
<br>
When a DHCP server receives a DHCPDISCOVER message from a client, which is an IP address lease request, the server reserves an IP address for the client and makes a lease offer by sending a DHCPOFFER message to the client on UDP port 68. This message contains the client's MAC address, the IP address that the server is offering, the subnet mask, the lease duration, and the IP address of the DHCP server that is making the offer. The offer from the DHCP server is not a guarantee that the IP address will be allocated to the client; however, the server usually reserves the address until the client has had a chance to formally request the address.<br>
<br>
After the client receives a DHCPOFFER, it responds with a DHCPREQUEST message, indicating its intent to accept the parameters in the DHCPOFFER. A client can receive DHCP offers from multiple servers, but it will accept only one DHCP offer.<br>
<br>
When the DHCP server receives the DHCPREQUEST message from the client, the configuration process enters its final phase. The acknowledgement phase involves sending a DHCPACK packet to the client. This packet includes the lease duration and any other configuration information that the client might have requested. At this point, the IP configuration process is completed.<br>
<br>
<pre>
<code>
Note:
As indicated in the figure above, DHCPOFFER and DHCPACK messages are sometimes sent as broadcasts instead of unicasts. For details, refer to [RFC 2131](http://www.rfc-editor.org/rfc/rfc2131.txt){:target="_blank"}, Dynamic Host Configuration Protocol.
</code>
</pre>
<br>
The lease mechanism ensures that hosts that have been moved or are switched off for extended periods do not keep addresses that they do not use. The addresses are returned to the address pool by the DHCP server, to be reallocated as necessary.<br>
<br>
In addition to the four most common DHCP messages, you might also see other DHCP messages in packet captures as follows:<br>
<br>
<ul>
<li><b>DHCPNAK:</b>b> A DHCPNAK is a negative acknowledgment from the DHCP server. For example, the server sends DHCPNAK if the client requests an address that is already in use by another client.</li><br>
<li><b>DHCPDECLINE:</b>b> If the DHCP client determines the offered configuration parameters are invalid, it sends a DHCPDECLINE packet to the server, and the client must begin the lease process again.</li><br>
<li><b>DHCPRELEASE:</b>b> After the client is ready to give up the DHCP IP address, it sends a DHCPRELEASE message.</li><br>
<li><b>DHCPINFORM:</b>b> A DHCP client that already has an IP address can use DHCPINFORM message to request more information from the server. For example, browsers use DHCP Inform to obtain web proxy settings.</li>
</ul>
<br>
<b>DHCP Relay Agent</b><br>
The DHCP server does not have to reside directly on the same subnet where the DHCP client resides. Moreover, it’s impractical to have a DHCP server on every subnet. Most enterprise networks will have a few centralized DHCP servers. The DHCP relay agent acts as an intermediary and ensures that local DHCP client requests are passed onto centralized DHCP servers. Any Layer 3 capable devices such as routers or switches can function as the DHCP relay agent.<br>
<br>



