---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 1: Understanding the TCP/IP Protocol Suite"
---

<b>The OSI Model (Open Systems Interconnection Reference Model)</b><br>
The OSI reference model separates network functions into seven categories, or layers, and defines the network functions that occur at each layer. Each layer provides services to the layer above it, uses services from the layer below it, and has an abstract connection to the same layer on the peer system. This modularization of function simplifies the implementation of complex network functions. And by defining these functions, the OSI model helps users understand how data from an application program travels through a network medium to an application program that is located in another computer.<br>

<img src="https://cjs6891.github.io/el7_blog/public/img/1514079693.png" alt="" style="">
The layers of the OSI model are as follows:
<ul>
<li><b>Layer 1, Physical:</b> The physical layer defines the electrical, mechanical, procedural, and functional specifications for activating, maintaining, and deactivating the physical link between end systems. Characteristics such as voltage levels, timing of voltage changes, physical data rates, maximum transmission distances, physical connectors, and other similar attributes are defined by physical layer specifications. Examples of Layer 1 devices are transceivers, modems, CSU/DSU, and hubs.</li>
<br>
<li><b>Layer 2, Data Link:</b> The data link layer defines how data is formatted for transmission and how data accesses the physical layer. This layer also typically includes error checking. Examples of Layer 2 devices are bridges and switches, which forward and flood traffic based on MAC addresses. Although MAC addresses are typically physical addresses, they operate at the data link layer of the OSI model.</li>
<br>
<li><b>Layer 3, Network:</b> The network layer provides connectivity between two host systems that can be located on geographically separated networks. It provides logical addressing, selects the best path for data delivery, and routes data packets. An example of a Layer 3 device is a router.</li>
<br>
<li><b>Layer 4, Transport:</b> The transport layer segments data from the system of the sending host and reassembles the data into a data stream on the system of the receiving host. For example, business users in large corporations often transfer large files from field locations to a corporate site. Reliable delivery of the files is important, so the transport layer breaks down large files into smaller pieces, which are known as segments, that are less likely to incur transmission problems.
<br>
<br>
The boundary between the transport layer and the session layer can be thought of as the boundary between application protocols and data-flow protocols. Whereas the application, presentation, and session layers are concerned with application issues, the lower four layers are concerned with data transport issues.
<br>
<br>
The transport layer shields the upper layers from transport implementation details. Specifically, issues such as reliability of transport between two hosts are assigned to the transport layer. In providing a communication service, the transport layer establishes, maintains, and properly terminates virtual circuits. Transport error detection, error recovery, and information flow control ensure reliable service.</li>
<br>
<li><b>Layer 5, Session:</b> The session layer establishes, manages, and terminates sessions between two communicating hosts. The session layer also synchronizes dialog between the presentation layers of the two hosts and manages their data exchange. For example, web servers have many users, so there are many communication processes open at a given time. Therefore, it is important to keep track of which user communicates on which path.</li>
<br>
<li><b>Layer 6, Presentation:</b> The presentation layer ensures that the information that is sent at the application layer of one system is readable by the application layer of another system. For example, a PC program communicates with another computer, with one computer using EBCDIC and the other using ASCII to represent the same characters. If necessary, the presentation layer translates between multiple data formats by using a common format.</li>
<br>
<li><b>Layer 7, Application:</b> The application layer is the OSI layer that is closest to the user. This layer provides network services to the applications of the user, such as email, file transfer, and terminal emulation. The application layer differs from the other layers in that it does not provide services to any other OSI layer, but only to applications outside the OSI model. The application layer establishes the availability of intended communication partners and synchronizes and establishes agreement on procedures for error recovery and control of data integrity</li>
</ul>
<br>
<b>Data Encapsulation and De-Encapsulation</b><br>
Information that is to be transmitted over a network must undergo a process of conversion at both the sending end and the receiving end of the communication. That conversion process is known as encapsulation and de-encapsulation.<br>
<br>
The information that is sent on a network is referred to as data or data packets. If one computer wants to send data to another computer, the data must first be packaged by a process called encapsulation. Encapsulation works very similarly to sending a package through a postal service. The first step is to put the contents of the package into a container. Next, you write the address of the location to which you want to send the package on the outside of the container. Then you put the addressed package into the postal service collection bin, and the package begins its route toward its destination.<br>
<br>
Encapsulation wraps data with each network layer's necessary protocol information before network transit. As the data moves down through the layers of the OSI reference model, each OSI layer adds a header (and a trailer, if applicable) to the data before passing it down to a lower layer. The process is illustrated in the figure below. The headers and trailers of an upper layer are not for use by the lower layers, instead they contain control information for the network devices along the way, and ultimately, the receiver. The control information ensures proper delivery of the data and to ensure that the receiver can correctly interpret the data.<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514081219.png" alt="" style="">
The following steps occur to encapsulate data:
<ol>
<li>The user data is presented to the application layer.</li>
<br>
<li>The application layer adds the application layer header (Layer 7 header) to the user data. The Layer 7 header and the original user data become the data that is passed down to the presentation layer.</li>
<br>
<li>The presentation layer adds the presentation layer header (Layer 6 header) to the data. The combined data and header then become the data that is passed down to the session layer.</li>
<br>
<li>The session layer adds the session layer header (Layer 5 header) to the data. This combination then becomes the data that is passed down to the transport layer.</li>
<br>
<li>The transport layer adds the transport layer header (Layer 4 header) to the data. This combination, which is known as a segment, becomes the data that is passed down to the network layer.</li>
<br>
<li>The network layer adds the network layer header (Layer 3 header) to the data. This combination, which is known as a packet, becomes the data that is passed down to the data link layer.</li>
<br>
<li>The data link layer adds the data link layer header and trailer (Layer 2 header and trailer) to the data. A Layer 2 trailer is usually the FCS (Frame Check Sequence. Extra characters added to a frame for error control purposes.), which is used by the receiver to detect whether the data is in error. This combination, which is known as a frame, then becomes the data that is passed down to the physical layer.</li>
<br>
<li>The physical layer then transmits the bits onto the network media.</li>
</ol>
<pre><code>
Note:
The format of the data at each layer is generically known as the PDU. There is also terminology that is used for the PDU (Protocol Data Unit) at certain layers. For example, the Layer 2 (data link layer) PDU is called a "frame." The Layer 3 (network layer) PDU is called a "packet." The Layer 4 (transport layer) PDU is called a "segment" for TCP or a "datagram" for UDP.
</code></pre>
When the remote device receives a sequence of bits, the physical layer at the remote device passes the bits to the data link layer for manipulation, beginning the de-encapsulation process. The de-encapsulation process is similar to that of reading the address on a package to see if it is for you, and then removing the contents of the package if it is addressed to you.
<pre><code>
Note:
The term "decapsulation" is sometimes used in place of the term "de-encapsulation." Both terms are acceptable.
</code></pre>
When the data link layer receives the data, it checks the data-link trailer (the FCS) to see if the binary data has been corrupted in transit. While some data-link technologies can request retransmission for corrupt data, most modern data-links, including Ethernet, will simply discard the corrupted frame. In such environments, if reliability is required, it must be provided by upper layers in the stack. If the data is not in error, the data link layer reads and interprets the control information in the data-link header. The data link layer strips the data-link header and trailer, and then passes the remaining data up to the network layer based on the control information in the data-link header. Each subsequent layer performs a similar de-encapsulation process eventually presenting the original user data from the source to the program running on the peer system.<br>
<br>
<b>TCP/IP Model</b><br>
Development of the 4-layer TCP/IP model started before work began on the 7-layer OSI model. As it turned out, TCP/IP had too much momentum to be overtaken by the OSI model or any of the other competing network models. The TCP/IP model is now the dominant protocol suite that is used on today's Internet. The TCP/IP model is also referred to as the TCP/IP protocol suite, the Internet protocol suite, the TCP/IP stack, and the DoD model.<br>
<br>
Development of the OSI model began in the late 1970s, and the model was published in 1984. Although the OSI model was never actually implemented, the theory that it embodies has influenced the continual development and maturation of TCP/IP. TCP/IP was developed in a rather ad hoc fashion. The timeline includes the following:
<ul>
<li>ARPANET, the precursor to the Internet, was developed in the late 1960s.</li>
<br>
<li>In May of 1974, Kahn and Cerf published a paper titled “A Protocol for Packet Network Intercommunication,” which described the early ideas of what would become the TCP/IP model.</li>
<br>
<li>In March of 1982, the US Department of Defense declared TCP/IP as the standard for all military computer networking.</li>
<br>
<li>On January 1, 1983 (known as "Flag Day"), the ARPANET switched from the old networking protocol, NCP, to TCP/IP.</li>
</ul>
<br>
TCP/IP includes not only TCP and IP, but also specifications for other protocols, such as UDP, ICMP, and so on. It also includes common applications such as electronic mail, terminal emulation, and file transfer. TCP/IP embodies every aspect of modern network communications that use IP at the network layer. TCP operates at the transport layer of the OSI and TCP/IP models and is responsible for making sure that the data that the source device sends arrives at its destination. IP operates at the network layer of the OSI model (Internet layer of the TCP/IP model) and is responsible for the transmission of data. It does not do any error correction itself. The figure below provides a comparison of the OSI and TCP/IP models.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514082772.png" alt="" style="">
In the late 1970s through the 1980s, no networking protocol was dominant. There were many, including IBM SNA, DEC DECnet, Apple AppleTalk, Banyan Vines, and Novell IPX. Due to many historical circumstances and compared to all the competitors, TCP/IP has gained momentum, and has become the de facto standard in the industry.<br>
<br>
Take a closer look at the four layers of the TCP/IP model:<br>
<br>
<ul>
<li><b>Link layer:</b> This layer is also known as the network access layer and is the equivalent of both the physical and data link layers of the OSI model. It deals with components such as cables, connectors, and network cards, like OSI Layer 1. Like Layer 2 of the OSI model, the link layer of the TCP/IP model is concerned with hardware addresses.</li>
<br>
<li><b>Internet layer:</b> This layer aligns directly with Layer 3 of the OSI model. You may also know this layer as the network layer. It routes data from the source to the destination by defining the packet and the addressing scheme, moving data between the link and transport layers, routing packets of data to remote hosts, and performing fragmentation and reassembly of data packets. The Internet layer is where IP operates.</li>
<br>
<li><b>Transport layer:</b> This layer is directly aligned with Layer 4 of the OSI model: It is the core of the TCP/IP architecture. It is the layer where TCP and UDP operate. This layer provides communication services directly to the application processes that are running on network hosts.</li>
<br>
<li><b>Application layer:</b> This layer corresponds to Layers 5, 6, and 7 of the OSI model. It provides applications for file transfer, network troubleshooting, and Internet activities. It also supports network APIs, which allow programs that have been created for a particular operating system to access the network.</li>
</ul>
Variants of both the TCP/IP model and IP itself have been developed. IPv4 was the basis of the DoD standard in 1982. Later IPv6 was developed to deal with many of the shortcomings of IPv4. The industry is currently working through a long transition period between IPv4 and IPv6.<br>
<br>
The example in the figure below illustrates encapsulation and de-encapsulation in light of the TCP/IP model. It shows what happens when you use a web browser to go to a site on the Internet.<br>
<br>
Your web browser is an application that operates at the application layer. After you enter an address in the address bar, the browser passes data (an HTTP “GET” request) to the application layer. When the application layer passes the data to the transport layer, the transport layer may split the data into segments (if the amount of data is deemed large enough). The transport layer adds a TCP header to the segment, encapsulating it in TCP. If there are multiple segments, TCP sequences them so the data stream can be reassembled when it reaches its destination. The segment is then passed to the Internet layer, where it receives an IP header to encapsulate it as an IP packet. The IP header contains source and destination IP addresses, which will enable the data to be properly routed to the destination. The Internet layer may also break a large packet into smaller fragments, then the fragments are reassembled at the Internet layer at the destination system. When the IP packet reaches the link layer, it is encapsulated in an Ethernet frame, which contains source and destination hardware, or MAC, addresses. The frame is then transmitted in the form of bits onto the physical network.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514083207.png" alt="" style="">
At the destination, the process is reversed. As information in each header is read, the header is stripped and the remaining data is sent up to the next layer.<br>
<br>
<b>Introduction to the Internet Protocol</b><br>
The IP layer in TCP/IP determines where packets of data are to be routed based on their destination IP addresses. IP uses packets to carry information through the network. A packet is a self-contained, independent entity that contains data and sufficient information to be routed from the source to the destination without reliance on previous packets.<br>
<br>
IP has these characteristics:<br>
<br>
<ul>
<li>IP operates at Layer 3 of the OSI model (network layer), and Layer 2 of the TCP/IP stack (Internet layer).</li>
<br>
<li>IP is a connectionless protocol in which a one-way datagram is sent to the destination without advance notification to the destination device. The destination device receives the data and does not return any status information to the sending device.</li>
<br>
<li>IP uses hierarchical addressing in which the network ID resembles a street and the host ID resembles a house or office building on that street.</li>
<br>
<li>IP provides service on a best-effort basis and does not guarantee packet delivery. A packet can be misdirected, duplicated, or lost on the way to its destination.</li>
</ul>
IP does not provide any special features that recover corrupted packets. If these services are required, they must be provided by higher layers in the protocol stack.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514300452.png" alt="" style="">
Attackers may manipulate the fields in the IP header to carry out their attacks, so it is important for an analyst to understand the different fields of the IP headers. The IPv4 header fields are:<br>
<ul>
<li><b>Version:</b> A 4-bit field that identifies the IP version being used. Version is 4 referred to as IPv4.</li>
<br>
<li><b>IP Header length:</b> A 4-bit field containing the length of the IP header. The minimum length of an IP header is 20 bytes</li>
<br>
<li><b>Type of service:</b> The 8-bit ToS field traditionally uses 3 bits for IP Precedence. The newer redefinition of the ToS field uses a 6-bit DSCP (Differentiated Services Code point) field and a 2-bit ECN (Explicit Congestion Notification) field to identify the level of service a packet receives in the network.</li>
<br>
<li><b>Total length:</b> Specifies the length of the IP packet that includes the IP header and the user data. The length field is 2 bytes, so the maximum size of an IP packet is 65,535 bytes.</li>
<br>
<li><b>Identifier, flags, and fragment offset:</b> As an IP packet moves through the Internet, it might need to cross a route that cannot handle the size of the packet. The packet will be divided, or fragmented, into smaller packets and reassembled later. These fields are used to fragment and reassemble packets.</li>
<br>
<li><b>Time to live:</b> It is possible for an IP packet to roam aimlessly around the Internet. If there is a routing problem or a routing loop, then you don't want packets to be forwarded forever. A routing loop is when a packet is continually routed through the same routers over and over. The TTL field is initially set to a number and decremented by every router that is passed through. When TTL reaches 0, the packet is discarded.</li>
<br>
<li><b>Protocol:</b> In the layered protocol model, the layer that determines which application the data is from or which application the data is for is indicated using the Protocol field. This field does not identify the application, but identifies a protocol that sits above the IP layer that is used for application identification. For example, protocol number 1 = ICMP, 6 = TCP, 17 = UDP.</li>
<br>
<li><b>Header checksum:</b> A value that is calculated based on the contents of the IP header. Used to determine if any errors have been introduced during transmission.</li>
<br>
<li><b>Source IP address:</b> 32-bit IP address of the sender.</li>
<br>
<li><b>Destination IP address:</b> 32-bit IP address of the intended recipient.</li>
<br>
<li><b>Options and padding:</b> A field that varies in length from 0 to a multiple of 32 bits. If the option values are not a multiple of 32 bits, 0s are added or padded to ensure that this field contains a multiple of 32 bits.</li>
</ul>
<br>
<b>IP Addressing</b><br>
Consider how physical street addresses are necessary to locate specific homes and businesses, so that mail can reach those real-world locations efficiently. In a similar way, logical IP addresses are used to identify the location of specific devices on an IP network so that data can reach those network locations efficiently. Every host, computer, networking device, or peripheral connected to the Internet must have an IP address. Without a structure for allocating all those IP addresses, it would be impossible to route packets efficiently.<br>
<br>
The IPv4 address is the most common type of address that is currently used on the Internet. An IPv4 addresses is a 32-bit number that describes the location of a network device.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514302668.png" alt="" style="">
<br>
In the decimal representation of an IP address, the value of each octet can range from 0 to 255. The octets are separated by a period, or dot. This scheme is known as dotted decimal notation. The IP address that is shown in the table can be written as 172.16.128.17 and spoken as "172 dot 16 dot 128 dot 17."<br>
<br>
An IP address is a hierarchical address and consists of two parts, the network ID and the host ID. The network ID (network address portion) identifies the network of which an IP address is a part. It starts from the leftmost bits and extends to the right. The host ID (the host address portion) uniquely identifies a host, or endpoint, on a network. These endpoints are the servers, computers, and other devices that are connected to the network. The host ID starts from the right-most bits and extends to the left. Many computers can share the same network ID, but combining the network ID with a host ID in an IP address uniquely identifies a device on the network. For example, in the figure below, hosts 192.168.1.2, 192.168.1.3, and 192.168.1.4 share the network ID 192.168.1.0, but they have their own unique host IDs, .2, .3, and .4, respectively.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514302817.png" alt="" style="">
<br>
Hosts that share the same network ID are said to be on the same network. Most hosts on a network can directly communicate only with devices on the same network. If the hosts need to communicate with devices that have interfaces that are assigned with other network IDs, there needs to be a network device that can route data between the networks. Routers can route data between networks because they maintain information about routes to the various networks. A network ID enables a router to put a packet onto the appropriate network.<br>
<br>
Networks have their own IP addresses. These addresses have binary 0s in all host bit positions. In the figure, a router sits between two different networks, the 192.168.1.0 network and the 192.168.2.0 network. Hosts on the 192.168.1.0 network can communicate directly with each other, but any packets they send to hosts on the 192.168.2.0 network must be sent through the router. Also notice that host 192.168.1.2 and host 192.168.2.2 have the same host ID. Although it is possible for two devices on different networks to have the same host ID, each host on the same network must have a unique host ID.<br>
<br>
<b>IP Address Masks</b><br>
For IPv4, a subnet mask is a 32-bit combination that identifies which part of the address is the network portion and which part is the host portion. It performs this function by using 1s and 0s. A subnet mask is created by placing a binary 1 in each bit position that represents the network portion and placing a binary 0 in each bit position that represents the host portion. For example, a subnet mask of 255.255.255.0 (11111111.11111111.11111111.00000000) applied to the IP address 192.168.7.5 specifies that the binary digits of the first three octets are the network portion of the address and every bit of the last octet specifies the host address. Hence, 192.168.7.0 is the network address and .5 is the host address. A subnet mask helps routers determine the network path for packets. The figure below provides another example.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514303149.png" alt="" style="">
<br>
When you express an IP address, you accompany it with a subnet mask in dotted decimal format, or you append a prefix length. A prefix length performs the same function as a subnet mask by providing the number of bits in the address that are used for the network portion. For example, in 172.16.55.87/20, /20 is the prefix length. It tells you that the first 20 bits are the network address. The remaining 12 bits make up the host portion. A /20 prefix is the equivalent of the subnet mask 255.255.240.0 (11111111.11111111.11110000.00000000).<br>
<br>
<b>IP Address Classes</b><br>
To accommodate different sizes of networks and to aid in classifying them, IP addresses are divided into categories that are called classes. Assigning IP addresses to classes is known as classful addressing. The classes were determined by the IANA (Internet Assigned Numbers Authority).<br>
<br>
As mentioned before, each IP address consists of a network ID and a host ID. Each address class uses a fixed number of octets (that is, a fixed set of bits) to indicate the network ID. The remaining octets of the 32-bit IP address are used for host addresses. A bit or bit sequence at the start of a classful IP address determines the class of the address. This starting bit or bit sequence is known as the MSB (Most Significant Bit).<br>
<br>
The table below shows three of the five IP address classes.<br>
<br>
<ul>
<li><b>Class A:</b> The first 0 of a Class A address is always in the first bit (MSB) position. Because the first bit is a 0, the lowest number that can be represented is 00000000 (decimal 0), and the highest number that can be represented is 01111111 (decimal 127). However, these 2 network numbers, 0 and 127, are reserved and cannot be used as network addresses. An address that has a value in the range of 1 to 126 in the first octet of the 32-bit number is a Class A address.</li><br>
<li><b>Class B:</b> The first 0 of a Class B address is always in the second bit position. Starting the first octet with binary 10 ensures that the Class B space is separated from the upper levels of the Class A space. The remaining 6 bits in the first octet can be populated with either 1s or 0s. Therefore, the lowest number that can be represented with a Class B address is 10000000 (decimal 128), and the highest number that can be represented is 10111111 (decimal 191). An address that has a value in the range of 128 to 191 in the first octet is a Class B address.</li><br>
<li><b>Class C:</b> The first 0 of a Class C address is always in the third bit position. Therefore, the lowest number that can be represented is 11000000 (decimal 192), and the highest number that can be represented is 11011111 (decimal 223). If an address contains a number in the range of 192 to 223 in the first octet, it is a Class C address.</li>
</ul><br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514304579.png" alt="" style="">
<br>
<pre><code>
Note: 127 (01111111) is a Class A address reserved for local loopback interfaces and cannot be assigned to a network.
</code></pre>
<br>
Each address class has a default mask, but each default mask can be extended to break networks into subnetworks. The default masks (and corresponding prefixes) are:<br>
<ul>
<li><b>Class A:</b> 255.0.0.0 or a/8</li><br>
<li><b>Class B:</b> 255.255.0.0 or a/16</li><br>
<li><b>Class C:</b> 255.255.255.0 or a/24</li>
</ul>
<br>
<b>Reserved IP Addresses</b><br>
The following IP addresses are reserved and cannot be assigned to individual devices on a network:<br>
<br>
<ul>
<li><b>Network address:</b> An IP address that has binary 0s in all host bit positions is reserved for the network address. The network address is used to identify the network itself. For example, 172.16.0.0 is an example of a Class B network address. In this address, the first two octets are reserved for the network address; that address is never used as an address for any device that is attached to it. The last two octets contain 0s because those 16 bits are for host numbers and are used for devices that are attached to the network. An example of an IP address for a device on the 172.16.0.0 network would be 172.16.16.1. Routers use network addresses when they search their IP route tables for destination network locations.</li><br>
<li><b>Directed broadcast address:</b> To send data to all the devices on a network, a broadcast address is used. Broadcast IP addresses end with binary 1s in the entire host part of the address (the host field). Consider the network in the example 172.16.0.0, in which the last 16 bits make up the host field (or host part of the address). The broadcast that would be sent out to all devices on that network would include a destination address of 172.16.255.255. The directed broadcast is capable of being routed. However, for some versions of Cisco IOS Software, routing directed broadcasts is not the default behavior.</li><br>
<li><b>Local broadcast address:</b> If an IP device wants to communicate with all devices on the local network, it sets the destination address to all 1s (255.255.255.255) and transmits the packet. For example, hosts that do not know their network number and are asking some server for the number can use this address. The local broadcast is never routed.</li><br>
<li><b>Local loopback address:</b> A local loopback address is used to let the system send a message to itself for testing. A typical local loopback IP address is 127.0.0.1.</li><br>
<li><b>Autoconfiguration IP addresses:</b> Sometimes, neither a statically nor a dynamically configured IP address is found on startup. In such instances, hosts supporting IPv4 link-local addresses (RFC 3927) generate an address in the 169.254/16 prefix range. This address can be used only for local network connectivity and operates with many caveats, one of which is that it will not be routed. You will mostly see this address as a failure condition when a PC fails to obtain an address via DHCP.</li>
</ul>
<br>
<b>Public and Private IP Addresses</b><br>
Internet stability depends directly on the uniqueness of publicly used network addresses. Therefore, some mechanism is needed to ensure that addresses are, in fact, unique. Originally, it was the responsibility of an organization that is known as the InterNIC. IANA succeeded the InterNIC. IANA carefully manages the remaining supply of IP addresses to ensure that duplication of publicly used addresses does not occur. Such duplication would cause instability in the Internet and would compromise its capability to deliver datagrams to networks using the duplicated addresses.<br>
<br>
To obtain a public (globally unique) IP address or a block of public IP addresses, you must contact an ISP. The ISP then contacts the upstream registry or the appropriate regional registry at one of these organizations:<br>
<ul>
<li>AfriNIC (African Network Information Center)</li><br>
<li>APNIC (Asia Pacific Network Information Center)</li><br>
<li>ARIN (American Registry for Internet Numbers)</li><br>
<li>LACNIC (Latin American and Caribbean Network Information Center)</li><br>
<li>RIPE NCC (Réseaux IP Européens Network Coordination Centre)</li>
</ul>
<br>
While Internet hosts require a globally unique IP address, private hosts that are not connected to the Internet can use any valid address. However, these addresses must be unique within the private network. But because many private networks exist alongside public networks, grabbing "just any address" is strongly discouraged. RFC 1918 specifies a set of IP addresses that is reserved for private networks.<br>
<br>
These addresses are not routed on the Internet backbone. When a network using private addresses must connect to the Internet, it is necessary to translate the private addresses to public addresses. This translation process is known as NAT. A router is often the network device that performs NAT. The tables below show the private and public IP address ranges.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514307539.png" alt="" style="">
<br>
<b>IPv6 Addresses</b>
The IPv4 address space provides approximately 4.3 billion addresses. Of that address space, approximately 3.7 billion addresses are actually assignable; the other addresses are reserved for special purposes, such as multicasting, private address space, loopback testing, and research.<br>
<br>
The IPv4 public address space has now been exhausted. Many enterprises have sufficient address space (public or private) to manage their intranet needs for the next few years. However, the length of time that is needed to transition to IPv6 demands that administrators and managers consider the issue well in advance. The largest enterprises may need to act sooner rather than later to ensure sufficient enterprise connectivity.<br>
<br>
A simplified IPv6 header architecture and protocol operation translates into reduced operational expenses. Built-in security features mean easier security practices that are sorely lacking in many current networks. However, perhaps the most significant IPv6 improvement is the address autoconfiguration features.<br>
<br>
The Internet is rapidly evolving from a collection of stationary devices to a fluid network of mobile devices. IPv6 allows mobile devices to quickly acquire and transition between addresses as they move among foreign networks, with no need for a foreign agent. A foreign agent is a router that can function as the point of attachment for a mobile device when it roams from its home network to a foreign network.<br>
<br>
IPv6 address autoconfiguration also means more robust plug-and-play network connectivity. Autoconfiguration supports consumers who can have any combination of computers, printers, digital cameras, digital radios, IP phones, Internet-enabled household appliances, and robotic toys that are connected to their home networks. Many manufacturers already integrate IPv6 into their products.<br>
<br>
The figure below compares the fields of an IPv6 header to the fields of an IPv4 header.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1514337004.png" alt="" style="">
<br>
