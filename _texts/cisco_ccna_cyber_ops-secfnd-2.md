---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 2: Understanding the Network Infrastructure"
---

<a href="#Analyzing DHCP Operations">2.2 Analyzing DHCP Operations</a><br>
<a href="#IP Subnetting">2.3 IP Subnetting</a><br>
<a href="#Hubs, Bridges, and Layer 2 Switches">2.4 Hubs, Bridges, and Layer 2 Switches</a><br>
<a href="#VLANs and Trunks">2.5 VLANs and Trunks</a><br>
<a href="#Spanning Tree Protocols">2.6 Spanning Tree Protocols</a><br>
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
<li><b>DHCPNAK:</b> A DHCPNAK is a negative acknowledgment from the DHCP server. For example, the server sends DHCPNAK if the client requests an address that is already in use by another client.</li><br>
<li><b>DHCPDECLINE:</b> If the DHCP client determines the offered configuration parameters are invalid, it sends a DHCPDECLINE packet to the server, and the client must begin the lease process again.</li><br>
<li><b>DHCPRELEASE:</b> After the client is ready to give up the DHCP IP address, it sends a DHCPRELEASE message.</li><br>
<li><b>DHCPINFORM:</b> A DHCP client that already has an IP address can use DHCPINFORM message to request more information from the server. For example, browsers use DHCP Inform to obtain web proxy settings.</li>
</ul>
<br>
<b>DHCP Relay Agent</b><br>
The DHCP server does not have to reside directly on the same subnet where the DHCP client resides. Moreover, it’s impractical to have a DHCP server on every subnet. Most enterprise networks will have a few centralized DHCP servers. The DHCP relay agent acts as an intermediary and ensures that local DHCP client requests are passed onto centralized DHCP servers. Any Layer 3 capable devices such as routers or switches can function as the DHCP relay agent.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514641575.png" alt="" style="">
<br>
The primary function of a DHCP relay agent is to forward DHCP messages from the local clients to the remote DHCP server.<br>
<br>
When a DHCP relay agent receives a broadcast packet from a connected client, it examines the giaddr(Gateway IP Address) field. If the field has an IP address of 0.0.0.0, then the DHCP relay agent changes the giaddr field in DHCP packets from zero to the relay agent IP address and forwards the message to the remote subnet where the DHCP server is located.<br>
<br>
The DHCP server uses this IP address to select an IP address pool from which to assign the IP addresses to the DHCP client.<br>
<br>
The return packets from the DHCP server are directly sent to the relay agent identified in the giaddr field. The DHCP relay agent forwards or relays the reply to the DHCP client.<br>
<br>
<b>Capturing DHCP Examples</b><br>
If you want to monitor DHCP communication between a DHCP server and a client, you can run a packet sniffing tool, such as tcpdump or dhcpdump, on the same local network and capture DHCP traffic. You can also run debug commands on Cisco IOS routers and switches if they are acting as DHCP servers or relay agents to view DHCP traffic going to or transiting these devices.<br>
<br>
Below is a sample <code>tcpdump</code> output from a Linux machine. The <code>tcpdump</code> capture shows renewals. Typically a client sends a REQUEST when the lease lifetime is 50% used up, and an ACK from the server resets the lifetime back to its full value.<br>
<br>
<pre>
<code>
root@Kali:~# tcpdump -i eth0 port 67 or port 68 -e -n
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes

15:40:44.336909 00:0c:29:1b:a3:84 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 342: 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:0c:29:1b:a3:84, length 300
15:40:44.337311 00:50:56:fd:83:cd > 00:0c:29:1b:a3:84, ethertype IPv4 (0x0800), length 342: 192.168.198.254.67 > 192.168.198.1.68: BOOTP/DHCP, Reply, length 300
16:01:58.549937 00:0c:29:1b:a3:84 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 365: 192.168.198.1.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:0c:29:1b:a3:84, length 323
16:01:58.551804 00:50:56:fd:83:cd > 00:0c:29:1b:a3:84, ethertype IPv4 (0x0800), length 342: 192.168.198.254.67 > 192.168.198.1.68: BOOTP/DHCP, Reply, length 300		
</code>
</pre>
<br>
Packet sniffing is enabled on the port 67 (DHCP server port) and port 68 (DHCP client port). The <code>–e</code> parameter instructs the command to display the source and the destination MAC addresses. The <code>–n</code> parameter instructs the command not to convert the addresses to names. The <code>–i</code> parameter instructs the command to listen on the particular interface. Here, eth0 is the name of the interface.<br>
<br>
For in-depth analysis of the DHCP packets, use the dhcpdump tool. The following is a sample <code>dhcpdump</code> output from the Linux machine on the eth0 interface.<br>
<br>
<pre>
<code>
root@Kali:~# dhcpdump -i eth0
[output omitted]

TIME: 2016-07-22 18:03:26.783 
    IP: 192.168.198.254 (0:50:56:fd:83:cd) > 192.168.198.128 (0:c:29:lb:a3:84) 
    OP: 2 (BOOTPREPLY) 
HTYPE: 1 (Ethernet) 
HLEN: 6 
HOPS: 0 
XID: 98bd7222 
SECS: 0 
FLAGS: 0
CIADDR: 0.0.0.0
YIADDR: 192.168.198.128
SIADDR: 192.168.198.254
GIADDR: 0.0.0.0
CHADDR: 00:0c:29:lb:a3:84:00:00:00:00:00:00:00:00:00:00 
SNAME:  .
FNAME:  .
OPTION: 53 (  1) DHCP message type           5 (DHCPACK)
OPTION: 54 (  4) Server identifier           192.168.198.254
OPTION: 51 (  4) IP address leasetime        1800 (30m)
OPTION:  1 (  4) Subnet mask                 255.255.255.0
OPTION: 28 (  4) Broadcast address           192.168.198.255
OPTION:  3 (  4) Routers                     192.168.198.2
OPTION: 15 ( 11) Domainname                  localdomain
OPTION:  6 (  4) DNS server                  192.168.198.2
OPTION: 44 (  4) NetBIOS name server         192.168.198.2
[output omitted]
</code>
</pre>
<br>
This output is more detailed than the <code>tcpdump</code> output. The <b>YIADDR</b> field is populated with the IP address of the client, and <b>SIADDR</b> field is populated with the IP address of the server. Notice the multiple options field in this output; multiple options were not available in the <code>tcpdump</code> output. For example, <b>Option 53</b> tells the DHCP message type. The message type in this output is <b>DHCPACK</b> message. The DHCP client lease time in the <b>Option 51</b> can also be seen.<br>
<br>
The IP address, subnet mask, default gateway, and the DNS server are the minimal configuration parameters that are required for the DHCP client to get online. In addition to that, DHCP server provides the DNS domain name, NETBIOS name servers, and so on, which can be seen in the <b>Options</b> section of this output.<br>
<br>
Apart from the configuration parameters that are mentioned in this output, DHCP server has the flexibility to provide other configuration parameters as well. For example, LWAP (Lightweight Access Point) can use the information that is provided in the <b>Option 43</b> to join the specific WLAN controllers. Similarly, IP phones and gateways can utilize the DHCP information that is provided in the <b>Option 150</b> to discover the TFTP server IP address for Image download. In this way, DHCP provides an expandable framework so that vendors can implement dynamic configuration for their product services.<br>
<br>
As an analyst examining the partially captured PCAP with the DHCP packets shown below, what suspicions should you determine?<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514642608.png" alt="" style="">
<br>
The above figure is an example of the result of using a tool that is called <b>Yersinia</b> to launch a DHCP attack against the DHCP server. The Yersinia tool is capable of generating DHCP DISCOVER requests using spoofed MAC address at a rapid rate to quickly exhaust the IP address pool on the DHCP server. All the DHCP clients of the victim network are starved of the DHCP resource. The attacker can then set up a rogue DHCP server on the network and perform man-in-the-middle attacks.<br>
<br>
As shown in the Wireshark output above, a large amount of DHCP discover packets are being broadcasted out using different spoofed MAC addresses. The DHCP server (192.168.200.1) then responded with the DHCP offer packets until all the available IP addresses are exhausted.<br>
<br>
<a name="IP Subnetting"></a>
<b>IP Subnetting</b><br>
To increase scalability, network administrators often need to divide networks (especially large networks) into subnetworks, or subnets. A subnet segments the hosts within the network. With proper network segmentation, even when attackers get in, their access is limited to only a segment of the network and not to the entire network. One very basic task that an analyst will need to perform is to determine which subnet that a given IP address belongs to. For example, when investigating the 10.1.1.36/24 IP address, one should be able to determine that this IP address belongs in the 10.1.1.0/24 subnet. Therefore, it is important for the security analyst to understand the purposes and functions of the subnets and their addressing schemes.<br>
<br>
A subnet segments the hosts within the network. Without subnets, the network has a flat topology. A flat topology has a small routing table and relies on MAC addresses to deliver packets. MAC addresses have no hierarchical structure. As the network grows, the use of the network bandwidth becomes less efficient.<br>
<br>
A company that occupies a three-story building might have a network that is divided by floors, with each floor divided into offices. Think of the building as the network, the floors as the three subnets, and the offices as the individual host addresses.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514649493.png" alt="" style="">
<br>
There are other disadvantages to a flat network. All devices share the same broadcast domain, and it is difficult to apply security policies because there are no boundaries between devices.<br>
<br>
In multiple-network environments, each subnetwork may be connected to the Internet by a single router. This figure shows one router connecting multiple subnetworks to the Internet. The details of the internal network environment and how the network is divided into multiple subnetworks are inconsequential to other IP networks.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514649614.png" alt="" style="">
<br>
The advantages of subnetting a network are as follows:<br>
<br>
<ul>
<li>Smaller networks are easier to manage and map to geographical or functional requirements.</li><br>
<li>Contain the broadcast traffic to the individual subnets to improve performance.</li><br>
<li>More easily apply network security measures at the interconnections between subnets than within a large single network.</li>
</ul>
<br>
<b>Subnet Masks</b><br>
The IP addressing that is used in the flat network must be modified to accommodate the required segmentation. A subnet mask identifies the network-significant portion of an IP address. The network-significant portion of an IP address is simply the part that identifies the network that the host device is on. This part is called the network address and defines every subnetwork. The use of segmentation is important for the routing operation to be efficient.<br>
<br>
A subnet mask:<br>
<br>
<ul>
<li>Defines the number of bits that represent the network and subnet part of the address</li><br>
<li>Is used by end systems to identify the destination IP address as either local or remote</li><br>
<li>Is used by Layer 3 devices to determine network path</li>
</ul>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514649851.png" alt="" style="">
<br>
How do you know how many bits represent the network portion of the address and how many bits represent the host portion? When you express an IPv4 network address, you add a prefix length to the network address. The prefix length is the number of bits in the address that give the network portion. For example, in 172.16.55.87 /20, /20 is the prefix length. It tells you that the first 20 bits are the network address, leaving the remaining 12 bits as the host portion. The entity that is used to specify the network portion of an IPv4 address to the network devices is called the subnet mask. The subnet mask consists of 32 bits, just as the address does, and uses 1s and 0s to indicate which bits of the address are network bits and which bits are host bits. You express the subnet mask in the same dotted decimal format as the IPv4 address. The subnet mask is created by placing a binary 1 in each bit position that represents the network portion and placing a binary 0 in each bit position that represents the host portion. Both the network and host portion of the subnet mask must be continuous. A /20 prefix is expressed as a subnet mask of 255.255.240.0 (11111111.11111111.11110000.00000000). The remaining bits (low order) of the subnet mask are zeroes, indicating the host address within the network.<br>
<br>
The subnet mask is configured on a host with its IPv4 address to help the host determine the network portion of that address. The host makes this determination by logically ANDing the binary bits of its IPv4 address with the binary bits of the subnet mask.<br>
<br>
Networks are not always assigned the same prefix. Depending on the number of hosts on the network, the prefix that is assigned may be different. Having a different prefix number changes the host range and broadcast address for each network.<br>
<br>
For example, look at the host 10.1.20.70/26:<br>
<br>
<ul>
<li>
Address:<br>
 - 10.1.20.70<br>
 - 00001010.00000001.00010100.01000110<br>
</li><br>
<li>
Subnet mask:<br>
 - 255.255.255.192<br>
 - 11111111.11111111.11111111.11000000<br>
</li><br>
<li>
Network address:<br>
 - 10.1.20.64<br>
 - 00001010.00000001.00010100.01000000<br>
</li>
</ul>
<br>
<b>Variable-Length Subnet Masking</b><br>
The figure below illustrates a network that uses fixed-length prefixes to address various segments. Address space is wasted because large subnets are used for addressing the WAN interfaces which are simply point-to-point segments. The three WAN segments only require the use of two host addresses, yet a subnet containing 254 hosts has been assigned to each WAN segment, wasting lots of usable IP addressing space.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514650459.png" alt="" style="">
<br>
VLSM affords the options of including more than one subnet mask within a network and of subnetting an already subnetted network address.<br>
<br>
Network using VLSM:<br>
<br>
<ul>
<li>The subnet 172.16.14.0/24 is divided into smaller subnets</li><br>
<li>One subnet has a subnet mask /27.</li><br>
<li>Further subnetting of one of the unused /27 subnets into /30 subnets.</li>
</ul>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514650630.png" alt="" style="">
<br>
VLSM offers these benefits:<br>
<br>
<ul>
<li><b>More efficient use of IP addresses:</b> Without the use of VLSM, companies must implement a single subnet mask within an entire Class A, B, or C network number.<br>
<br>
 - For example, consider the 172.16.0.0/16 network address that is divided into subnetworks using /24 masking. One of the subnetworks in this range, 172.16.14.0/24, is further divided into smaller subnetworks using /27 masking. These smaller subnetworks range from 172.16.14.0/27, 172.16.14.32/27, 172.16.14.64/27, and so on to 172.16.14.224/27.<br>
 <br>
  - In the figure, one of these smaller subnets, 172.16.14.128/27, is further divided using the /30 prefix, which creates subnets with only two hosts, to be used on the WAN links. The /30 subnets range from 172.16.14.128/30 to 172.16.14.156/30. The WAN links used the 172.16.14.132/30, 172.16.14.136/30, and 172.16.14.140/30 subnets out of the range.<br>
</li><br>
<li><b>Better-defined network hierarchical levels:</b> VLSM allows more hierarchical levels within an addressing plan, which enables easier aggregation of network addresses. For example, in the figure, subnet 172.16.14.0/24 describes all the addresses that are further subnets of 172.16.14.0, including addresses from subnet 172.16.14.0/27 to subnet 172.16.14.128/30, and so on.</li>
</ul>
<br>
<a name="Hubs, Bridges, and Layer 2 Switches"></a>
<b>Hubs, Bridges, and Layer 2 Switches</b><br>
LANs can vary widely in size. A LAN may consist of only two computers in a home office or small business, or it may include hundreds of computers in a large corporate office spanning a single or multiple buildings.<br>
<br>
When you connect three or more devices together, you need a dedicated network device to enable communication between hosts. Network devices, such as the hubs, bridges, and switches, form the aggregation point for LANs. These devices enable communication between hosts by connecting them to the other segments of the network. A basic understanding of how these devices operate will help a security analyst investigate any malicious or suspicious activity from the logs that the devices generate.<br>
<br>
A hub is a multiport repeater that takes an electronic signal that has been received from a device on one of its ports, magnifies the signal, and re-transmits that signal out all other ports on the hub, except for the original incoming port. Any traffic that comes into a hub or repeater port is sent out or repeated to all other ports. All ports on the hub share both a single collision domain and a single broadcast domain as the hub or repeater operates at the physical layer of the OSI model.<br>
<br>
A collision domain, which is common in early versions of Ethernet, is a section of a network that is connected by a shared medium where data packets sent from one device will be heard by all other devices on the segment.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514651517.png" alt="" style="">
<br>
In the figure above, Computer A sends the message to Computer B through the hub. The hub, in addition to sending the message to the port where Computer B is connected, also sends the message out to the ports where Computer C and Computer D are connected, with no regard for where the actual destination host is connected to the hub. The bandwidth for the Computer C and Computer D are affected when Computer A and Computer B are communicating. Because everyone that is connected in this network can hear anyone’s message, you can use sniffing tools to easily eavesdrop on the network, which can also be a major security concern.<br>
<br>
Whenever a packet is received on a port, the hub has no memory to store any data and the packet has to be transmitted. Hubs can run only in half-duplex mode where it can provide communication in both directions, but only one direction at a time. A network collision occurs when more than one device attempts to send a packet on a network segment at the same time.<br>
<br>
To avoid the collision, devices in the Ethernet segment participate in the CSMA/CD (Carrier Sense Multiple Access with Collision Detection). This method uses a carrier sensing scheme in which a transmitting data station detects other signals on the wire and they won’t send their frame if someone else is using the wire. Simultaneous transmission still takes place and collision can happen. With the collision detection mechanism, the transmitting device stops transmitting the frame and transmits a jam signal when the collision is detected. Then the transmitting device waits for a random time interval, recognizing the need to retransmit before trying to resend the frame.<br>
<br>
As the number of devices increase in hub-based environments, the problem gets much worse because of the nature of the half-duplex communication. Too many collisions and retransmissions occur which can lead to excessive LAN traffic congestion.<br>
<br>
<b>Traffic Flow: Hub vs. Bridge</b><br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514651791.png" alt="" style="">
<br>
The left side of the diagram above shows the packet flow when the hosts are connected to the hub. All the devices must compete for the same bandwidth due to the half-duplex nature. So, when PC1 sends a message to the PC3, no other communications can happen between the devices in the network.<br>
<br>
The right side of the diagram shows the packet flow when the hosts are connected to a bridge. In this example, review the simultaneous data flow, where PC1 sends traffic to PC3, PC2 sends traffic to PC4, and PC4 sends traffic to PC2. Ethernet bridges selectively forward individual frames from a receiving port to the port where the destination node is connected. This selective forwarding process can be thought of as establishing a momentary point-to-point connection between the transmitting and receiving nodes. The connection is made only long enough to forward a single frame. During this instance, the two nodes have a full-bandwidth connection between them and represent a logical point-to-point connection.<br>
<br>
<b>Need for Switches</b><br>
Bridges and switches operate at the data link layer of the OSI model and use data link MAC addresses to differentiate between hosts that are connected to their ports. Although bridges preceded switches, these devices function in a similar way. These devices learn which ports lead to which host MAC addresses by monitoring the source MAC addresses in the Ethernet headers on frames that arrive on their switch ports. The port to MAC address mappings are stored in MAC address tables. The MAC address tables are commonly called CAM tables because many switches use CAM (a special type of technology) to store the MAC address tables.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514652071.png" alt="" style="">
<br>
The figure above shows that the switch and each of its switch ports is connected to a single PC or a server. Switches are really multi-port bridges. Bridges perform the bridging logic that was usually implemented in software. In contrast, switches perform the Layer 2 switching in hardware. Today, it is common to use switches to divide a network into segments and reduce the number of devices that compete for bandwidth. Each new segment, then, results in a new collision domain. More bandwidth is available to the devices on a segment, and collisions in one collision domain do not interfere with the working of the other segments.<br>
<br>
In the figure, each switch port represents a unique collision domain. All the ports on the switch fall under a single broadcast domain.<br>
<br>
A broadcast domain is a logical division of a computer network, in which all nodes can reach each other by broadcast at the data link layer. Filtering frames by the MAC address of the switch does not extend to filtering broadcast frames. By their nature, broadcast frames must be forwarded. Therefore, all ports on a switch form a single broadcast domain. It takes a Layer 3 entity, such as a router, to terminate a Layer 2 broadcast domain.<br>
<br>
<b>Switching Operations</b><br>
Understanding switching operations will help analysts understand adversary operations against the Layer 2 devices in the network. For example, if an attacker can exhaust the switch's MAC address table, the attacker can turn the switch into a hub. Therefore, analysts must understand the content of the MAC address table and how the information in the MAC address table is learned.<br>
<br>
The switch builds and maintains a table, called a CAM table, that matches a destination MAC address with the port that is used to connect to a node. For each incoming frame, the destination MAC address in the frame header is compared to the list of addresses in the CAM table. Switches then use MAC addresses as they decide whether to filter, forward, or flood frames.<br>
<br>
The switch creates and maintains a table using the source MAC addresses of incoming frames and the port number through which the frame entered the switch. When an address is not known, a switch learns the network topology by analyzing the source address of incoming frames from all the attached networks.<br>
<br>
If a switch receives a frame that is destined for a MAC address that is in its MAC address table, then that frame is only forwarded out of the appropriate port leading to that MAC address. This conserves bandwidth on all the other ports on the switch. If the switch receives a frame that is destined for a MAC address that is not in its MAC address table, it floods the frame out of all ports, except for the port where the frame was received. If the destination replies to the source, the switch will be able to learn the new MAC address based on the source MAC address in the Ethernet header of the reply.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514652430.png" alt="" style="">
<br>
The table describes the switching process:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514652512.png" alt="" style="">
<br>
Look at a tool that an attacker uses to falsely generate MAC addresses to fill up the CAM table.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514652660.png" alt="" style="">
<br>
The above output is an example of the MAC flooding attack against the switch’s MAC address table using a Linux attack tool called <b>macof</b>, which is mainly used to flood the switch on a local network with MAC addresses. There is a limited amount of space available in the switch's MAC address table. If the space is exhausted, the switch cannot learn new addresses. Traffic that is destined for an unknown MAC address will be flooded out all the ports, turning the switch into hub, which can lead to information disclosure if the attacker captured flooded frames and obtain sensitive information. It can also lead to a denial of service as network performance can be affected.<br>
<br>
As shown in the <code>show mac address-table</code> output, many MAC addresses are learned on the port Gi0/2. Highlighted MAC addresses on the output are generated by the macof tool from the Linux system. The injection of the MAC addresses using the macof tool is very quick and can quickly fill the MAC address table of the switch.<br>
<br>
<a name="VLANs and Trunks"></a>
<b>VLANs and Trunks</b><br>
A VLAN is a logical broadcast domain that can span multiple physical LAN segments. Within the switched internetwork, VLANs provide segmentation and organizational flexibility. A VLAN structure can be designed to group stations that are segmented logically by functions, project teams, and applications, without regard to the physical location of the users.<br>
<br>
When investigating Layer 2 attacks, an analyst should understand the functions of VLANs.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514659093.png" alt="" style="">
<br>
Within the switched internetwork, VLANs provide segmentation and organizational flexibility. Using VLAN technology, you can group switch ports and their connected users into logically defined communities. Examples might include the following:<br>
<br>
<ul>
<li>Co-workers in the same department</li><br>
<li>A cross-functional product team</li><br>
<li>Diverse user groups sharing the same network application</li>
</ul>
<br>
A VLAN is a group of devices on one or more LANs that are configured to communicate as if they were attached to the same wire, when in fact they are located on several different LAN segments. Because VLANs are based on logical instead of physical connections, they are extremely flexible.<br>
<br>
VLANs define broadcast domains in a Layer 2 network. A broadcast domain is the set of all devices that will receive broadcast frames originating from any device within the set. Broadcast domains are typically bounded by routers because routers do not forward broadcast frames. Layer 2 switches create broadcast domains that are based on the configuration of the switch. Switches are multiport bridges that allow you to create multiple broadcast domains. Each broadcast domain is like a distinct virtual bridge within a switch.<br>
<br>
Each VLAN created in the switch defines a new broadcast domain. Traffic cannot pass directly to another VLAN (between broadcast domains) within the switch or between two switches. To interconnect two different VLANs, you must use routers or Layer 3 switches.<br>
<br>
You can assign each switch port to only one VLAN, adding a layer of security. Ports in a VLAN share broadcast, but ports in different VLANs do not share broadcasts. Containing broadcasts within a VLAN improves the overall performance of the network by limiting the ability of broadcast traffic to span network segments.<br>
<br>
A VLAN can exist on a single switch or span multiple switches. VLANs can include stations in a single building or multiple-building infrastructures.<br>
<br>
A port normally carries only the traffic for the single VLAN to which it belongs. For a VLAN to span across multiple switches, a trunk must be configured to connect the two switches together. A trunk can carry traffic for multiple VLANs as shown in the following figure. A trunk allows multiple VLANs to share the port connection.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514659412.png" alt="" style="">
<br>
A trunk is a point-to-point link between an Ethernet switch interface and another networking device, such as a router or a switch. Ethernet trunks carry the traffic of multiple VLANs over a single link and allow you to extend VLANs across an entire network. A trunk does not belong to a specific VLAN. Rather, it is a conduit for VLANs between switches and routers.<br>
<br>
You can configure an interface as trunking or nontrunking. If you configure an interface as trunking, it supports various trunking modes. Also, a trunk interface can be configured to negotiate trunking with neighboring interfaces.<br>
<br>
A special trunking protocol, IEEE 802.1Q is used to carry multiple VLANs over a single link between two devices. A trunk could also be used between a network device and a server or another device that is equipped with an appropriate 802.1Q-capable NIC.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514659550.png" alt="" style="">
<br>
When Ethernet frames are placed on a trunk, they need additional information about the VLANs to which they belong. They get this information by using the 802.1Q encapsulation header. 802.1Q uses an internal tagging mechanism that inserts a 4-byte tag field into the original Ethernet frame between the Source Address and Type or Length fields. Because 802.1Q alters the frame, the trunking device recomputes the FCS on the modified frame. It is the responsibility of the Ethernet switch to look at the 4-byte tag field and determine where to deliver the frame.<br>
<br>
By default, on a Cisco Catalyst switch, all configured VLANs are carried over a trunk interface. On an 802.1Q trunk port, there is one native VLAN, which is untagged (by default, VLAN 1). All other VLANs are tagged with a VLAN ID.<br>
<br>
<a name="Spanning Tree Protocols"></a>
<b>Spanning Tree Protocols</b><br>
A topology with loops can be useful and potentially harmful. A loop implies the existence of multiple paths through the internetwork, and a network with multiple paths from source to destination can increase overall network fault tolerance through improved topological flexibility.<br>
<br>
STP is a Layer 2 protocol that runs on bridges and switches. Without STP, the switched (or bridged) network will fail when there are redundant paths in the switched (or bridged) network. To understand the attacks that can be carried out against STP, analysts should understand STP.<br>
<br>
The STP was originally developed by Digital Equipment Corporation, a key Ethernet vendor, to preserve the benefits of loops while eliminating their problems. Digital's algorithm later was revised by the IEEE 802 committee and was published in the IEEE 802.1D specification.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514660180.png" alt="" style="">
<br>
The following sequence of events occurs when an application on Host A communicates with Host B which causes a broadcast storm which will disrupt all the traffic on the switched network:<br>
<br>
<ol>
<li>Host A sends a frame to Host B.</li><br>
<li>Bridge A learns that MAC address of Host A is located on its top port.</li><br>
<li>Bridge A looks up the MAC address of Host B; if no match is found (since Host B hasn't talked yet), Bridge A sends out the frame on its bottom port (known as flooding).</li><br>
<li>Bridge B also receives the frame on its top link and updates its MAC address table that Host A is located on its top port.</li><br>
<li>A split-second later, Bridge B receives the exact same frame on its bottom link; this time, it causes a new update to its MAC address table, which is known as a race condition—whichever MAC address arrives first wins the race and gets installed in the MAC address table.</li><br>
<li>Bridge B looks up the MAC address of Host B; if no match is found (since Host B has not talked yet), Bridge B sends out the frame on either its top or bottom port, depending on the outcome of the race condition described in Step 5.</li><br>
<li>Bridge A and Host B both receive the frame; however, this frame causes Bridge A to again update its MAC address table.</li><br>
<li>Return to Step 3 and loop forever. Even if Host B talks, nothing changes because both switches constantly update their MAC address tables with incorrect information (because of the never-ending loop). There is no TTL field in Ethernet headers to eventually stop the frame from looping.</li>
</ol>
<br>
In addition to basic connectivity problems, the proliferation of broadcast messages in networks with loops represents a potentially serious network problem. Assume that Host A's initial frame is a broadcast. Both bridges forward the frames endlessly, using all available network bandwidth and blocking the transmission of other packets on both segments.<br>
<br>
The spanning-tree protocol designates a loop-free subset of the network's topology by placing those bridge ports that, if active, would create loops into a standby (blocking) condition. Blocking bridge ports can be activated in the event of a primary link failure, providing a new path through the internetwork.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514660523.png" alt="" style="">
<br>
To prevent loops in a network, a reference point for the network must first be defined. This reference point is called a root bridge. A root bridge is the logical center of the spanning tree topology. All paths that are not needed to reach the root bridge from anywhere in the network are placed in STP blocking mode. The spanning-tree protocol calculation occurs when the bridge is powered up and whenever a topology change is detected. The calculation requires communication between the spanning-tree bridges, which is accomplished using BPDUs.<br>
<br>
Since the original creation of the IEEE 802.1D specification, many enhancements have been added to network devices to improve spanning-tree performance. Some of these enhancements were implemented to speed up STP performance (UplinkFast, BackboneFast, PortFast), and others are configured to increase security (BPDU guard, BPDU filter, root guard, loop guard). There are also other mechanisms that are not directly related to STP, but can be used to either complement STP operation (UDLD) or to replace it (FlexLinks).<br>
<br>
Today, there are various flavors of STP, such as the IEEE specs (802.1D Common STP, 802.1w Rapid STP, 802.1s Multiple STP) or the proprietary vendor extensions. Each of these STP implementations functions in a similar fashion—typically differentiated by the amount of time that they need to recalculate an alternate topology (or converge) when there is a link failure, and the way that STP works with multiple VLANs.<br>
<br>
Look at a sample MAC flap log message and explore it in more detail.<br>
<br>
<pre>
<code>
5d: %SW_MATM-4-MACFLAP_NOTIF: Host 0012.950a.9952 in vlan 10 is flapping between port Gi1/1 and port Gi1/2
</code>
</pre>
<br>
This log information is a MAC flap notification message and tells that the MAC address of 0012.950a.9952 in VLAN 10 is flapping between ports G1/1 and G1/2 on the switch. There could be various reasons for this event being triggered.<br>
<br>
For example, if there is an attacker on the port G1/2 trying to spoof the MAC address of the host on G1/1, then there is a possibility that the switch generated the log message. This type of event is not always triggered by an attacker. Sometimes, in a network with redundant links, due to misconfigurations or interface flaps, STP might toggle the redundant links, which also could have caused the MAC address flap.<br>
<br>
In the scenario above, a security analyst can use their knowledge of STP to analyze the log information and narrow down the issue a lot faster, which can save time while identifying or correlating attacks on the network infrastructure.<br>
<br>
