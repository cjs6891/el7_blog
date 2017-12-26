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
