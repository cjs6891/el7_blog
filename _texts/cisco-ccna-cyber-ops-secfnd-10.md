---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 10: Understanding Common Endpoint Attacks"
---

<a href="#Classify Attacks, Exploits, and Vulnerabilities">10.2 Classify Attacks, Exploits, and Vulnerabilities</a><br>
<a href="#Buffer Overflow">10.3 Buffer Overflow</a><br>
<a href="#Malware">10.4 Malware</a><br>
<a href="#Reconnaissance">10.5 Reconnaissance</a><br>
<a href="#Gaining Access and Control">10.6 Gaining Access and Control</a><br>
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
<a name="Buffer Overflow"></a>
<b>Buffer Overflow</b><br>
Attackers can analyze network server applications for flaws. A buffer overflow vulnerability is one type of flaw. If a service accepts input and expects the input to be within a certain size but does not verify the size of input upon reception, it may be vulnerable to a buffer overflow attack. This means that an attacker can provide input that is larger than expected, and the service will accept the input and write it to memory, filling up the associated buffer and also overwriting adjacent memory. This overwrite may corrupt the system and cause it to crash, resulting in a DoS. In the worst cases, the attacker can inject malicious code in the buffer overflow, leading to a system compromise.<br>
<br>
Buffer overflow attacks are a common vector for client-side attacks. Malicious code can be injected into data files, and the code can be executed when the data file is opened by a vulnerable client application. For example, assume that an attacker posts such an infected file to the Internet. An unsuspecting user downloads the document and opens it with a vulnerable application. On the user's system, this spawns a malicious process that can connect to rogue systems on the Internet and download more malicious payloads. Firewalls generally do a much better job of preventing inbound malicious connections from the Internet than they do of preventing outbound malicious connections to the Internet.<br>
<br>
Techniques that are used to identify systems susceptible to buffer overflows include debugger tools, trial and error, and brute force attacks. The hacker modifies the specifics of the attack for the target application and operating system. Lengthy URL strings are one common input value that is used by attackers to overflow system buffers.<br>
<br>
<a name="Malware "></a>
<b>Malware </b><br>
Malware is malicious software that comes in several forms, including the following:<br>
<br>
<ul>
<li>Viruses: A virus is a type of malware that propagates by inserting a copy of itself into another program and becoming part of that program. It spreads from one computer to another, leaving infections as it travels. Viruses require human help for propagation, such as the insertion of an infected USB drive into a USB port on a PC. Viruses can range in severity from causing mildly annoying effects to damaging data or software and causing DoS conditions.</li><br>
<li>Worms: Computer worms are similar to viruses in that they replicate functional copies of themselves and can cause the same type of damage. In contrast to viruses, which require the spreading of an infected host file, worms are standalone software and do not require a host program or human help to propagate. To spread, worms either exploit a vulnerability on the target system or use some kind of social engineering to trick users into executing them. A worm enters a computer through a vulnerability in the system and takes advantage of file-transport or information-transport features on the system, allowing it to travel unaided.</li><br>
<li>Trojan horses: A Trojan horse is named after the wooden horse the Greeks used to infiltrate the city of Troy. It is a harmful piece of software that looks legitimate. Users are typically tricked into loading and executing it on their systems. After it is activated, it can achieve any number of attacks on the host, from irritating the user (popping up windows or changing desktops) to damaging the host (deleting files, stealing data, or activating and spreading other malware, such as viruses). Trojans are also known to create back doors to give malicious users access to the system. Unlike viruses and worms, Trojans do not reproduce by infecting other files nor do they self-replicate. Trojans must spread through user interaction such as opening an email attachment, or downloading and running a file from the Internet.</li>
</ul>
<br>
The Morris worm is often credited as the first Internet-based worm. It was launched in 1988. It was named after its author, a graduate student at Cornell University. The author claimed that it was not written to cause any damage, but instead to gauge the size of the Internet. However, the worm did cause damage as systems could be infected multiple times. The more copies of the worm running on a system, the greater drain of resources it caused, potentially making systems unusable. The worm was released from a network belonging to the Massachusetts Institute of Technology, to disguise its origin. It had the capability of exploiting multiple vulnerabilities in sendmail, finger, and rsh/rexec. It could use the local C compiler on systems to compile code. It utilized the words file on Unix systems for dictionary attacks against weak passwords. Potentially the most interesting aspect of this worm is that it was written almost three decades ago. The use of multiple attack vectors and the use of resources available on the compromised systems was quite ingenious for the first worm. The security professional must understand that the ingenuity that is brought to malware development has continued to compound over the decades.<br>
<br>
Internet worm production was especially prolific between 1999 and 2004. Examples of worms from this period include Melissa, ILOVEYOU, Anna Kournikova, Code Red, Nimda, SQL Slammer, MyDoom, and Sasser. Details for any of these worms can be found with simple Internet search queries. In general, these worms were mostly about wreaking havoc. Their targets were not directed as they victimized any vulnerable system. They consumed resources such as networking bandwidth, system CPU and memory, and IT man hours to eradicate them.<br>
<br>
Since the early 2000s, much has changed about worms in particular and network security in general. The Conficker worm, first identified in late 2008, was very different. The worm was very stealthy and resulted in a botnet with millions of infected machines. It mutated from version to version with ever-changing propagation and update strategies. The Stuxnet worm was discovered in June 2010. It was designed to attack industrial programmable logic controllers. It reportedly targeted the country of Iran’s nuclear program and was successful in destroying approximately one-fifth of the country’s nuclear centrifuges.<br>
<br>
Malware is commonly utilized by APTs (Advanced Persistent Threats). APTs are a set of continuous hacking processes targeting a specific entity, often with a specific goal. Some characteristics of APTs are obvious from the name. They are advanced; the attackers have the most advanced intelligence systems and techniques at their disposal and will use what is optimal for each step. They may utilize commonly available security tools when they are sufficient, but they may also discover and exploit zero-day (unpublished) vulnerabilities when necessary. They are also persistent. The attackers focus on their goal. They do not cash in on short-term opportunities. Instead they maintain discreet access, slowly but surely infiltrating deeper into systems until their objectives can be met.<br>
<br>
The structure of an APT attack does not follow a blueprint. As with any network attack, the scenario varies with the circumstance. However, a common methodology is as follows:<br>
<br>
<ul>
<li>Initial compromise</li><br>
<li>Escalation of privileges</li><br>
<li>Internal reconnaissance</li><br>
<li>Lateral propagation, compromising other systems on track towards goal</li><br>
<li>The end goal of the attacker, for example, maybe to exfiltrate sensitive data out</li><br>
<li>Mission completion</li>
</ul>
<br>
Each of these steps is taken very stealthily, with the goal of evading detection and maintaining presence.<br>
<br>
<a name="Reconnaissance"></a>
<b>Reconnaissance</b><br>
A reconnaissance attack is an attempt to gather information about an intended victim before attempting a more intrusive attack. Attackers can use standard networking tools such as dig, nslookup, and whois to gather public information about a target network from DNS registries. They can also use DNS queries to reveal such information as who owns a particular domain and which addresses have been assigned to that domain. Ping sweeps of the addresses revealed by the DNS queries can present a picture of the live hosts in a particular environment. After a list of live hosts is generated, the attacker can probe further by running port scans on the live hosts. In a port scan, an attacker usually sends specially crafted packets to a targeted host. By examining the packets that the host sends in response, the attacker can often determine which ports are open on the host and, either directly or by inference, which application protocols are running on those ports. Port scanning tools, such as the widely used nmap, can cycle through all well-known ports and provide a complete list of all services running on the host. They can also tell the attacker what operating system is running on the host, the MAC address of the host, and the version of software running on the host.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517579415.png" alt="" style="">
<br>
If a port scan is done rapidly or in sequence, it is fairly easy to detect. By monitoring logs such as host-based firewall logs, a security analyst may be able to see it as activity targeting many different ports on the same host during a short time. However, attackers discovered long ago that they can avoid detection by using slow, random scans, and other stealth techniques. Modern tools such as IPSs can help detect these types of scans.<br>
<br>
Attackers can use the information that is obtained from a port scan to discover the vulnerabilities of a specific endpoint. They can also use vulnerability scanners, such as Nessus and OpenVAS, to locate vulnerabilities in potential target hosts. Authorized security administrators can also use vulnerability scanners in their own networks and patch vulnerabilities before they can be exploited. However, attackers can use these tools to locate vulnerabilities before an organization even knows that they exist.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517579513.png" alt="" style="">
<br>
After completing port scans or vulnerability scans on a host, an attacker typically exploits known vulnerabilities of services that are associated with open ports that were detected and known vulnerabilities of the operating system and any other software running on the host.<br>
<br>
<a name="Gaining Access and Control"></a>
<b>Gaining Access and Control</b><br>
Acquiring access to the host is the most difficult stage in an endpoint attack. While the goal of the attacker may be to steal information from the endpoint, the goal may also be to remotely control a host inside a targeted network. In this case, the host is most commonly a public server or a user workstation, but any host will do. The attacker only needs control of a device that exists inside the network perimeter.<br>
<br>
Given a well-defended organization with modern security products, strong user training, and networks that are designed with best practices in mind, gaining access to and control of a host may seem impossible. Yet, the attacker must only find a single weakness and they have many ways of accomplishing their task.<br>
<br>
Attackers will commonly acquire employee credentials through phishing campaigns delivering malware which collects such information, or by directing a user to a portal controlled by the attacker, but looking like a legitimate company site, which requests credentials for authorization. Acquiring employee credentials for remote network access can be approached in multiple ways. If phishing fails, then attackers have several other methods at their disposal to attempt gaining access to a system.<br>
<br>
Attackers and penetration testers often keep dictionaries of common passwords from previous data breaches where password hashes have been cracked to expose the user credentials. An attacker can attempt to brute force passwords against known user names, or also brute force common configuration user names for service accounts, such as mysqladmin. Password lockout policies for a certain number of wrong password attempts for a user can make brute-forcing of limited value to an attacker. Since many organizations have lockout policies, attackers have begun to employ a technique that is called password spraying. Password spraying involves taking a list of possible user accounts and trying very common passwords such as the season+year (Summer2016), or the companyname + year (Cisco2016), or companyname + 123 (Cisco123) to capitalize on any employee using a very weak password based on randomness, but using characters and digits to conform with certain password policies. Each possible user account will be attempted for login with one or two of the very common passwords so that no lockout criteria could be reached for any user.<br>
<br>
Changing default credentials, deleting service accounts not needed on public-facing systems, and enforcing strong password policies which are regularly audited can help defend against these attacks. Sometimes credentials can also be gathered through weak web applications that allow URI paths to be passed that are directories on the web server containing user name and password information such as etc/passwd and etc/shadow.<br>
<br>
If attackers can gain access to an endpoint, they can also gain control of the endpoint and use it to launch more wide-spread attacks. The endpoint can become part of a botnet, which is a network of compromised systems that is used to perform DDoS attacks.<br>
<br>
A botnet consists of a group of "zombie" computers that run robots (or bots) and a master control mechanism that provides direction and control for the zombies. The originator of a botnet uses the master control mechanism on a command-and-control server to control the zombie computers remotely, often by using IRC.<br>
<br>
<ol>
<li>A botnet operator infects computers by sending them malicious bots. A malicious bot is self-propagating malware that is designed to infect a host and connect back to the command-and-control server. In addition to its worm-like ability to self-propagate, a bot can include the ability to log keystrokes, gather passwords, capture and analyze packets, gather financial information, launch DoS attacks, relay spam, and open back doors on the infected host. Bots have all the advantages of worms, but are generally much more versatile in their infection vector, and are often modified within hours of publication of a new exploit. They have been known to exploit back doors that are opened by worms and viruses, which allows them to access networks that have good perimeter control. Bots rarely announce their presence with high scan rates, which damage network infrastructure; instead they infect networks in a way that escapes immediate notice.</li><br>
<li>The bot on the newly infected host logs in to the CnC server and awaits commands. Often, the CnC server is an IRC channel or a web server.</li><br>
<li>Instructions are sent from the command-and-control server to each bot in the botnet to execute actions. When the zombies receive the instructions, they begin generating malicious traffic that is aimed at the victim.</li>
</ol>
<br>
In the example below, an attacker controls the zombies to launch a DDoS attack against the victim's infrastructure. These zombies run a covert channel to communicate with the CnC server that the attacker controls. This communication often takes place over IRC, encrypted channels, bot-specific peer-to-peer networks, and even Twitter.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1517590843.png" alt="" style="">
<br>
