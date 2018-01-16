---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 5: Understanding Network Applications"
---

<a href="#DNS Operations">6.2 DNS Operations</a><br>
<a href="#Recursive DNS Query">6.3 Recursive DNS Query</a><br>
<a href="#">6.</a><br>
<a href="#">6.</a><br>
<a href="#">6.</a><br>
<a href="#">6.</a><br>
<a href="#">6.</a><br>
<a href="#">6.</a><br>

<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>
<a name=""></a>

<a name="DNS Operations"></a>
<b>DNS Operations</b><br>
DNS (Domain Name System) provides mappings between the host names and IP addresses, or other mappings. For example, DNS can map host names, such as host.example.com, to IP address, such as 192.168.40.100 (or the IPv6 address). DNS service enables access to the network resources by their names instead of having to remember their IP addresses.<br>
<br>
In addition to mapping host names to IP addresses, DNS can perform various other types of mapping. Each mapping type is defined in a different type of RR (Resource Record). For example, an RR that maps a host name to an IPv4 address is called an A record, an RR that maps a domain name to a list of mail servers for that domain is called an MX record, and an RR that maps the name server for the domain is called an NS record. More resource record types such as AAAA (IPv6 A Record), and PTR, are discussed later in this topic.<br>
<br>
The figure below shows an example from a Microsoft DNS server. In this example, the domain name is secure-x.local. The hq-srv.secure-x.local host is the name server for the secure-x.local domain, as configured by the NS record. The A records are used to map the host name to the IP address. For example, the hq-srv host name is mapped to the 192.168.1.2 IP address, the inside-srv host name is also mapped to the 192.168.1.2 IP address, and so on. The fully qualified domain names for these two host names are hq-srv.secure-x.local and inside-srv.secure-x.local<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516027762.png" alt="" style="">
<br>
The client side of DNS is called a DNS resolver. The DNS resource mapping process is accomplished by a DNS resolver sending a DNS query to a DNS server requesting the information that is defined in an RR.<br>
<br>
DNS is a critical protocol for the network operations but weaknesses in the implementation of the DNS protocol allow it to be exploited and used for malicious activities. Security analysts should understand DNS operations to be able to recognize and detect DNS-based attacks.<br>
<br>
<b>DNS Ports</b><br>
DNS primarily uses UDP port 53 for DNS queries and responses. DNS queries consist of a UDP request from the client followed by a UDP response from the DNS server. TCP port 53 is used when the DNS response data size exceeds 512 bytes, or for tasks such as zone transfers. Zone transfer is a type of DNS transaction. Zone transfer is used by the DNS administrators to replicate the DNS databases across a set of DNS servers.<br>
<br>
<b>DNS Distributed Database</b><br>
DNS is a globally distributed, scalable, hierarchical, and dynamic database. No single DNS server on the Internet contains the entire DNS database. Authority over the different parts of the DNS database is delegated to different DNS servers in the Internet.<br>
<br>
The DNS database is composed of a hierarchical domain name space that contains a tree-like data structure of linked domain names (nodes). The tree-like data structure for the domain name space starts at the root, which is represented by the "dot" (.), which is the topmost level of the DNS hierarchy. Although it is not typically displayed in user applications, the DNS root is represented as a trailing dot in an FQDN. For example, the right-most dot in "http://www.cisco.com." represents the root zone. From the root zone, the DNS hierarchy is then split into subdomain (branches) zones.<br>
<br>
Each FQDN is composed of one or more labels. Labels are separated with a dot (.), and may contain a maximum of 63 characters. An FQDN may contain a maximum of 255 characters, including the dot (.). Labels are constructed from right to left, where the label at the far right is the TLD for the domain name. For example, .com is the TLD (Top-Level Domain) for http://www.cisco.com because it is the label furthest to the right.<br>
<br>
The following diagram illustrates a sample of the DNS hierarchy starting from the root (.). For example, everything below the .org TLD is in the .org domain, and everything below the .cisco.com domain name space is in the .cisco.com domain.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516028921.png" alt="" style="">
<br>
<b>DNS Terminology</b><br>
<ul>
<li><b>Resource record:</b> The RR defines the DNS data types that are stored in the DNS database. The most common types of RRs are for SOA, IP addresses (A and AAAA), SMTP mail servers (MX), name servers (NS), pointers for reverse DNS lookups (PTR), and domain name aliases (CNAME). An RR is composed of the following fields: NAME, TYPE, CLASS, TTL, RDLENGTH, and RDATA.</li><br>
<li>Client device OSs or applications use very simple <b>stub DNS resolvers</b>. Typically, stub DNS resolvers issue DNS queries to the DNS recursive resolvers—not only for DNS information about the internal resources, but also for DNS information about publicly registered domains.</li><br>
<li><b>DNS recursive resolver</b> is a DNS server that processes the clients' DNS queries. The DNS recursive server queries the necessary authoritative DNS servers for the RR information, then the DNS recursive server provides the answer back to the DNS client. Typically, DNS recursive resolvers are internal to an organization and should only allow DNS queries from internal clients.</li><br>
<li><b>Open DNS recursive resolvers</b> are DNS recursive resolvers that allow queries from all IP addresses and are exposed to the Internet. Examples of public open DNS recursive resolvers include GoogleDNS (8.8.8.8) and Cisco OpenDNS (208.67.222.222 and 208.67.220.220). Attackers often scan for open DNS recursive resolvers to use them in reflection or amplification DDoS attacks. Organizations must exercise care in managing and monitoring their open DNS recursive resolvers.</li><br>
<li><b>Authoritative DNS server</b> is responsible for all the domain's RRs. The authoritative DNS server returns answers to the DNS queries with information that is stored in the RRs for a domain name space that is stored on the local server. Authoritative DNS servers provide the authoritative responses to the DNS recursive resolvers. The authoritative DNS servers are exposed to the Internet and generally allow DNS queries from all IP addresses.</li>
</ul>
<br>
The figure below shows the DNS query/response flow between the stub DNS resolver, the DNS recursive resolver, and the authoritative DNS server.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516029325.png" alt="" style="">
<br>
<ul>
<li><b>Zones:</b> In addition to being divided into domains, the DNS name space is partitioned into zones to simplify DNS database management. A zone is a contiguous portion of the domain name space in the DNS for which the administrative responsibility has been delegated to a single manager. A zone is the authoritative source for information about each domain that is included in the zone.</li><br>
<li>A <b>zone file</b> is a text file that describes a DNS zone, and contains a list of the zone's resource records.</li>
</ul>
<br>
<b>DNS RR Types</b><br>
The following are examples of DNS resource record types:<br>
<br>
<ul>
<li><b>A record:</b> Used to map host names to the IPv4 address of the host. In an A record, multiple IP addresses can correspond to a single host name. There can also be multiple host names each of which maps to the same IP address. There must be a valid A record in the DNS for the host.domain.name in order for a command, such as <code>telnet host.domain.name</code>, to work.</li><br>
<li><b>AAAA record:</b> AAAA is used to map hostnames to the IPv6 address of the host.</li><br>
<li><b>MX record:</b> MX maps a domain name to a list of mail servers for that domain.</li><br>
<li><b>PTR record:</b> A PTR points to a canonical name. The most common use is for implementing reverse DNS lookups, mapping an IP address to the hostname.</li><br>
<li><b>NS record:</b> An NS record identifies the DNS servers that are responsible (authoritative) for a zone.</li><br>
<li><b>CNAME record:</b> A CNAME record is used to specify that a domain name is an alias for another domain name, which is the "canonical" domain name.</li><br>
<li><b>TXT record:</b> A TXT record is used to associate any arbitrary text with a hostname. This record type is only used in specific cases such as Domain Keys Identified Mail, used as a method to detect email spoofing.</li><br>
<li><b>SOA record:</b> Each zone contains an SOA record. The SOA record identifies the name server that is the best source of information for the data within the zone. The SOA record also contains various other parameters that define the behavior of the DNS server.</li>
</ul>
<br>
<b>The nslookup Utility</b><br>
The <code>nslookup</code> utility is available on many operating systems, such as Windows and Linux, for querying the DNS database for domain names, IP address mapping, or any specific DNS record.<br>
<br>
The examples below are taken from a Cisco lab environment, .public and .private are used instead of .com and .local to avoid conflicting with real and commonly used domain name spaces.<br>
<br>
<ul>
<li><b>A record:</b> Using the <code>nslookup</code> utility, it shows that the dmz.secure-x.public host that is resolved to the IP address of 192.0.2.50 from the 209.165.200.233 DNS server, and the 209.165.200.233 DNS server is not the authoritative DNS server for the secure-x.public domain.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516029983.png" alt="" style="">
</li><br>
<li><b>PTR record:</b> In this example, using the <code>nslookup</code> utility, the set <code>q=ptr</code> option can be used to examine the PTR record. In this example, the PTR record from DNS shows 192.0.2.50 resolves to the various hostnames in the secure-x.public domain, such as dmz.secure-x.public.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516030080.png" alt="" style="">
</li><br>
<li><b>MX record:</b> In this example, using the <code>nslookup</code> utility, the <code>set q=mx</code> option can be used to examine the MX record. In this example, the MX record from DNS shows that 192.0.2.55 is the mail server for the secure-x.public domain.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516030193.png" alt="" style="">
</li>
</ul>
<br>
<a name="Recursive DNS Query"></a>
<b>Recursive DNS Query</b><br>
Understanding how the recursive DNS query process works is important to an analyst when dealing with DNS-based attacks and interpreting packet captures with DNS flows.<br>
<br>
When a DNS recursive resolver receives a DNS query for information for which it is not authoritative, it will recursively query the DNS architecture for the authoritative DNS server information.<br>
<br>
Once the DNS recursive resolver has obtained the requested information from the authoritative DNS server, it will provide that information to the original DNS resolver using a DNS response message. In this case, the resource record will be non-authoritative (since the recursive DNS resolver is not authoritative for the requested information). A recursive DNS request requires more processing by the DNS server, when compared to a non-recursive DNS request.<br>
<br>
The DNS recursive resolver may also have knowledge about the requested information that is stored in its local DNS cache. If the requested information is present in the DNS cache, then the recursive DNS resolver will respond with the locally cached resource record information.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1516054961.png" alt="" style="">
<br>
The above figure illustrates the recursive DNS process (assuming that nothing has been cached in the DNS recursor local DNS cache yet):<br>
<br>
<ol>

</ol>