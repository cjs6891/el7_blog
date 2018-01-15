---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 5: Describing Information Security Concepts"
---

<a href="#Information Security Confidentiality, Integrity, and Availability">5.2 Information Security Confidentiality, Integrity, and Availability</a><br>
<a href="#Personally Identifiable Information">5.3 Personally Identifiable Information</a><br>
<a href="#Risk">5.4 Risk</a><br>
<a href="#Vulnerability Assessment">5.5 Vulnerability Assessment</a><br>
<a href="#CVSS v3.0">5.6 CVSS v3.0</a><br>
<a href="#Access Control Models">5.7 Access Control Models</a><br>
<a href="#Regulatory Compliance">5.8 Regulatory Compliance</a><br>
<a href="#Information Security Management">5.9 Information Security Management</a><br>
<a href="#Security Operations Center">5.10 Security Operations Center</a><br>

<a name="Information Security Confidentiality, Integrity, and Availability"></a>
<b>Information Security Confidentiality, Integrity, and Availability</b><br>
As networks become increasingly interconnected, the importance of providing security services in the network increases. In the commercial world, connectivity is no longer optional and the possible risks of connectivity do not outweigh its benefits. Therefore, security services must provide adequate protection to companies that conduct business in a relatively open environment.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515888703.png" alt="" style="">
<br>
When compared with classical approaches to computer security, several new assumptions must be made about today's computer networks:<br>
<br>
<ul>
<li>Modern networks are very large and very interconnected. As such, modern networks are often more open to being accessed, and a potential attacker can easily attach to or remotely access such networks.</li><br>
<li>Widespread use of TCP/IP for internetworking increases the probability that more attacks are carried out over large, heavily interconnected networks such as the Internet using a common set of widely known and open protocols.</li><br>
<li>Computer systems and applications that are attached to these networks are becoming increasingly complex. Therefore, it has become more difficult to analyze, secure, and properly test the security of computer systems, the operating systems that run them, and their applications. When these systems and their applications are attached to large networks, the risk to the systems dramatically increases.</li>
</ul>
<br>
To provide adequate protection of networked resources, the procedures and technologies that you deploy must guarantee three things:<br>
<br>
<ul>
<li><b>Confidentiality:</b> Providing confidentiality of data guarantees that only authorized users can view sensitive information.</li><br>
<li><b>Integrity:</b> Providing integrity of data guarantees that only authorized subjects can change sensitive information. Integrity might also guarantee the authenticity of data.</li><br>
<li><b>Availability:</b> Providing system and data availability guarantees uninterrupted access by authorized users to important computing resources and data.</li>
</ul>
<br>
The confidentiality, integrity, and availability triad (also known as the CIA triad) is a fundamental information security concept. It is these three elements of the information system that each organization is trying to protect. Confidentiality prevents unauthorized disclosure of sensitive information. Encryptions can be used to ensure the confidentiality of the data transfers traversing across the network. Integrity prevents unauthorized modification of information, providing assurance of the accuracy of the information. Cryptographic hash functions (such as SHA-1 or SHA-2) can be used to provide data integrity. Availability is the prevention of loss of access to resources and information to ensure that information is available for use when it is needed. It is imperative to make sure that the requested information is always readily accessible to the authorized users. DoS is one of several types of security attacks that attempt to deny access to the information system resources. Methods that are used to protect against loss of availability include deploying fault tolerant systems, redundancies, and data backups.<br>
<br>
<a name="Personally Identifiable Information"></a>
<b>Personally Identifiable Information</b><br>
PII (Personally Identifiable Information), as used in U.S. privacy law and information security, is information that can be used on its own, or with other information, to identify, contact, or locate a single person, or to identify an individual in context.<br>
<br>
NIST SP 800-122(4) defines PII as "any information about an individual that is maintained by an agency, including any information that can be used to distinguish or trace an individual's identity, such as name, social security number, date and place of birth, mother's maiden name, or biometric records; and any other information that is linked or linkable to an individual, such as medical, educational, financial, and employment information."<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515889579.png" alt="" style="">
<br>
Examples of PII data include the following:<br>
<br>
<ul>
<li>Name, such as full name, maiden name, mother's maiden name</li><br>
<li>Telephone numbers, including home, and mobile numbers</li><br>
<li>Date and place of birth</li><br>
<li>Passport number, social security number, driver license number</li><br>
<li>Personal characteristics, including photographic image (especially of face or other distinguishing characteristic), x-rays, fingerprints, or other biometric image or template data (for instance, retina scan, voice signature, and facial geometry)</li>
</ul>
<br>
The concept of PII has become prevalent as information technology and the Internet have made it easier to collect PII through breaches of Internet security, network security, and web browser security, leading to a profitable market in collecting and reselling PII. Threat actors also exploit PII to stalk or steal the identity of a person, or to aid in the planning of criminal acts. It has been estimated that over 12 million Americans fall victim to identity theft each year, with a financial impact of over $26 billion.<br>
<br>
Numerous third parties either control or have access to your PII including federal, state, and local government agencies, employers, medical providers, financial services providers, and so on. Since so many third parties have access to PII, the confidentiality of your PII is only as good as the information security policies and procedures of the organizations that hold it. Unfortunately, the last decade of headlines indicates that these same organizations are largely failing to keep PII secure. The demand for data accessibility specifically from the web has created exploits such as SQL injection and cross site scripting that continue to plague organizations. Criminal threat actors continuously steal various pieces of the victims PII from third-party databases often with specific monetization methodologies in mind. U.S. FBI Director Robert Mueller publicly stated that there are two types of companies: those that have been hacked and those that will be in the future.<br>
<br>
Breaches involving PII are hazardous to both individuals and organizations. The development of effective incident response plans for breaches involving PII can contain and minimize the effects of these attacks. Organizations should develop plans that include elements such as determining when and how individuals should be notified, how a breach should be reported, and whether to provide remedial services, such as credit monitoring, to affected individuals.<br>
<br>
Not all PII should be protected in the same way. Organizations should apply appropriate safeguards to protect the confidentiality of PII that is based on the PII confidentiality impact level. Some PII does not need to have confidentiality that is protected, such as information that the organization has permission or authority to release publicly (for example, an organization‘s public phone directory).<br>
<br>
<ul>
<li>Office location</li><br>
<li>Business email address</li><br>
<li>Other information that is releasable to the public</li>
</ul>
<br>
The Health Insurance Portability and Accountability Act, a U.S. legislation, introduces the concept of Protected Health Information. PHI and PII are closely related. Under U.S. law, PHI is any information about health status, provision of health care, or payment for health care that is created or collected by a "covered entity" (or a business associate of a covered entity), and can be linked to a specific individual. A covered entity is any health plan, health care clearing house, or health care provider who transmits any health information in electronic form in connection with a qualified transaction and their business associates.<br>
<br>
<a name="Risk"></a>
<b>Risk</b><br>
Risk is a function of the likelihood of a given threat source’s exercising a particular potential vulnerability, and the resulting impact of that adverse event on the organization. Managing risk is a complex, multifaceted activity that requires the involvement of the entire organization. The NIST Special Publication 800-39: Risk Management Guide for Information Technology Systems defines some common risk terminology that is appropriate for security analysts, as follows:<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515890424.png" alt="" style="">
<br>
<ul>
<li>A <b>threat source</b> is an intent and method that is targeted at the intentional exploitation of a vulnerability or a situation and method that may accidentally trigger a vulnerability.</li><br>
<li>A <b>threat</b> is the potential for a threat source to exercise (accidentally trigger or intentionally exploit) a specific vulnerability.</li><br>
<li>A <b>vulnerability</b> is the weakness that makes the resource susceptible to the threat. An attack surface is the total sum of the vulnerabilities in a given system that is accessible to an attacker. The attack surface describes different points where an attacker could get into a system, and where they could get data out of the system.</li><br>
<li><b>Impact</b> is the resulting damage to the organization that is caused by the threat.</li>
</ul>
<br>
No organization can determine the exact likelihood of a threat occurring at any given time. However, the likelihood of a threat might be an educated estimation. Similarly, it is difficult to determine the impact and the cost of an attack. Factors such as employee downtime, loss of reputation, and loss of consumer confidence complicate this calculation. Again, the goal is to reach an agreed-upon and educated estimate.<br>
<br>
<b>Types of Risk</b><br>
In information security, risk pertains to the loss of confidentiality, integrity, or availability of information. Risks are ever-present; there is no way to ensure a totally risk-free, functional system. Risk management is the process of identifying risk, assessing risk, and taking steps to reduce risk to an acceptable level. A security risk assessment can only give a snapshot of the risks of the information systems at a particular point in time. Therefore, it is highly recommended to conduct security risk assessments more frequently, if not continuously. Information system risk assessment can be performed by using a qualitative or quantitative approach. Quantitative risk assessment involves trying to map a dollar amount to each specific risk, and qualitative risk assessment involves assigning a risk level such as low, medium, or high to each specific risk.<br>
<br>
Organizational risk can include many types of risk such as the following:<br>
<br>
<ul>
<li>Business risk is the risk that a business incurs merely as part of doing business. The exposure to business risk varies with the type of business. Business risk can be as simple as a competitor opening another store, a freak cold snap affecting sales at an ice cream stand, or an unexpected rise in gas prices for a delivery company.</li><br>
<li>Data risk is the risk of corruption, or even worse, disclosure, of important company data. Sometimes, data risk is small. A marketing company may not be concerned with accidental disclosure of an advertisement to be displayed on billboards, but it would be concerned if an attacker downloaded its customer list. Data risk may be intentional or accidental and could originate from either internal or external sources.</li><br>
<li>Data loss is not only probable, but likely. Hard drives fail, users accidentally overwrite data, and files become corrupted. Assuming that the organization has irreplaceable data (customer records, product development, or long-term research), the cost of data loss could be quite high. Considering the high probability and the high cost, a risk analyst might find the risk of data loss to be a high risk.</li><br>
<li>Systems risk is the likelihood that a company information system is not adequately protected from damage, loss, or compromise. Systems risk includes malicious and mistaken actions, but also poor planning. Storing paper files in a basement prone to flooding is as much an example of systems risk as an inadequately protected network.</li><br>
<li>An insider threat is an attack that is staged by a rogue employee who attempts to damage the organization by stealing confidential data, destroying systems, or causing downtime. The probability of such an attack may be medium to low, but many employees would be able to cause widespread damage. Some of these insider attacks would result in large financial losses or substantial reputational damage. Considering the medium to low probability, and the potential for very high damage, the risk might be assessed as high risk to the organization.</li><br>
<li>Application risk is the risk that business applications will fail, causing financial damage.</li>
</ul>
<br>
The potential for malware to spread inside an organization is often quite high, especially when employees have access to potentially malicious email and websites. The malware can then be used to trigger an APT (Advanced Persistent Threat). An APT is a network attack in which an unauthorized person gains access to a network and stays there undetected for a long time period. The intention of an APT is to steal data rather than to cause damage to the network or organization. Considering the high probability and high potential for damage, a risk analyst might find the risk of malware to be a high risk.<br>
<br>
<b>Risk Management</b><br>
Risk management is the process that balances the operational and economic costs of protective measures and the achieved gains in mission capability by protecting the IT systems and data that support their organizations’ missions.<br>
<br>
For example, many people decide to have home security systems and pay a monthly fee to a service provider to monitor the system for increased protection of their property. Presumably, the homeowners have weighed the cost of system installation and monitoring against the value of their household goods and their family’s safety priority.<br>
<br>
The following are options for managing risk:<br>
<br>
<ul>
<li><b>Risk acceptance</b> is a common option when the cost of other risk management options such as avoidance may outweigh the cost of the risk itself.</li><br>
<li><b>Risk avoidance</b> is the action that avoids any exposure to the risk. Risk avoidance is usually the most expensive risk mitigation option.</li><br>
<li><b>Risk limitation</b> limits a company’s risk exposure by taking some action. It is a strategy employing a bit of risk acceptance along with a bit of risk avoidance. It is the most commonly used risk mitigation strategy.</li><br>
<li><b>Risk transfer</b> is the transference of risk to a willing third party (for example, an insurance company).</li>
</ul>
<br>
<a name="Vulnerability Assessment"></a>
<b>Vulnerability Assessment</b><br>
A vulnerability is a defect in software or hardware, at least in the context of information security, and it is paired with an exploit as the means to exercise that vulnerability to some end. It is the important job of an organization's security team to keep up to date with the latest security vulnerabilities that could threaten the network and information systems.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515893317.png" alt="" style="">
<br>
The table that is shown above highlights some activities that are performed during the vulnerability assessment process.<br>
<br>
The objective of a vulnerability assessment is to ensure that the network and the information systems are tested for security vulnerabilities in a consistent and repeatable manner.<br>
<br>
Security vulnerabilities will continue to be discovered in technology products and services. These vulnerabilities, regardless of whether they are caused by an unintentional software bug or by design (such as a default administrative password), can be used by malicious persons to compromise the confidentiality, availability, or integrity of your infrastructure.<br>
<br>
Hardware and software vendors typically provide software fixes when they announce the vulnerabilities in their products. When there is no fix available, vendors typically provide a workaround or mitigation. There is usually a time period between the announcement of a security vulnerability in a particular technology and the availability of an attack method (an exploit). Within this time period, system administrators should take action to protect their systems against an attack because at this point the public knows that a flaw exists, but attackers are still trying to find a way to take advantage of that vulnerability. Unfortunately, the vulnerability-to-exploit time period has been steadily decreasing<br>
<br>
Sometimes information about a previously undisclosed vulnerability emerges on the Internet before the vendor is notified and has time to take action. In these situations, the vulnerability-to-exploit time period is “reversed,” in that the attackers have a working exploit for a vulnerability that no one knew existed except the attackers themselves. This situation is becoming far more common as vendors integrate open source and common third-party software packages. The result is that public information about vulnerabilities and exploits is often available before the vendor has a time to patch images or provide clear guidance to customers.<br>
<br>
With the large quantity of new vulnerabilities from numerous vendors, it can be overwhelming to track all the vulnerabilities. How can the security team analyze any single vulnerability and determine its relevance to the specific technology architecture? The solution is to have a good process to determine which ones are relevant to your organization.<br>
<br>
Security professionals should frequently evaluate CVSS (Common Vulnerability Scoring System) for the purposes of understanding specific vulnerability characteristics and severity. CVSS is an open framework for communicating the characteristics and severity of software vulnerabilities (https://www.first.org/cvss). CVSS scoring helps security professionals prioritize the specific vulnerabilities by vendor-defined severity, environment impact, and exploitability. Working with CVSS, the organization’s security policies, and vulnerability management procedures, the vulnerability response method can help clarify a course of action in a minimal amount of time.<br>
<br>
<pre>
<code>
Note:
Common open source tools used to perform vulnerability assessment include Metasploit and OpenVAS.
</code>
</pre>
<br>
<a name="CVSS v3.0"></a>
<b>CVSS v3.0</b><br>
Software, hardware, and firmware vulnerabilities pose critical risks to any organization operating a computer network, and can be difficult to categorize and mitigate. CVSS provides a way to capture the principal characteristics of a vulnerability and provide cybersecurity professionals a better understanding of the risk that is posed by each vulnerability. CVSS was developed as a cooperative effort between the National Infrastructure Advisory Council and several security industry vendors and research organizations, including Cisco. The Forum of Incident Response and Security Teams (FIRST) has been designated as the custodian of CVSS to promote its adoption globally.<br>
<br>
CVSS is a free and open industry standard for assessing the severity of computer system security vulnerabilities. Its development has been overseen by the CVSS SIG with input from representatives of a broad range of industry sectors, from banking and finance to technology and academia. CVSS attempts to assign severity scores to vulnerabilities, allowing responders to prioritize responses and resources according to threat. Scores are calculated based on a formula utilizing several metrics that approximate ease of exploit and its impact. Scores range from 0 to 10, with 10 being the most severe. While many analysts use only the CVSS base score for determining severity, temporal and environmental scores also exist, to factor in the availability of mitigations and how widespread the vulnerable systems are within an organization, respectively.<br>
<br>
CVSS provides a standard way to assess and score security vulnerabilities. The current version, which is known as CVSS v3.0, analyzes the scope of a vulnerability and identifies the privileges that an attacker needs to exploit it. The latest CVSS allows vendors to better analyze the impact of security vulnerabilities and more clearly define the level of urgency that is required to respond to the vulnerability.<br>
<br>
The CVSS v3.0 calculator (https://www.first.org/cvss/calculator/3.0) implements the formula as defined in the CVSS version 3.0 standard, generating scores that are based on the metric values you enter.<br>
<br>
The CVSS v3.0 base score is calculated based on the attack vector, attack complexity, privileges required, user interaction, scope, confidentiality, integrity, and availability.<br>
<br>
Example: MySQL Stored SQL Injection (CVE-2013-0375) computed to a CVSS v3.0 base score of 6.4 as calculated using the factors as shown in the table below.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515895254.png" alt="" style="">
<br>
For more information on CVSS v3.0, refer to the CVSS v3.0 User Guide at https://www.first.org/cvss/cvss-v30-user_guide_v1.4.pdf<br>
<br>
<a name="Access Control Models"></a>
<b>Access Control Models</b><br>
Access control includes control over access to the network resources, information system resources, and information. It is crucial for an organization to implement the proper access controls to protect the organization's resources and information. A security analyst should understand the different basic models for implementing access controls in order to better understand how attackers can break the access controls.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515972907.png" alt="" style="">
<br>
<ul>
<li><b>Mandatory access control:</b> MAC is the strictest control. The design of MAC was defined, and is primarily used by the government and military. MAC enforces system administrator-defined access controls to all controlled resources. MAC assigns a security label to each of the resources containing a classification (such as top secret, secret, and confidential) and a category (such as the department number and project name). Similarly, each user account on the system also includes the same classification and category properties. When a user attempts to access a resource, the system checks the user's classification and categories and compares them to the properties of the requested resource's security label. Access is only allowed if the user's two credentials match. For example, a user with a secret classification cannot access a resource with the top secret label. MAC requires high system management overhead due to the need to update the labels to accommodate new data, new users, and changes in the categorization and classification.</li><br>
<li><b>Discretionary access control:</b> DAC allows each user to control access to their own data. Instead of a security label as in the case of MAC, each resource in a DAC-based system has an ACL associated with it. An ACL contains a list of users and groups to which the user has permitted access together with the level of access for each user or group. DAC provides a much more flexible environment than MAC but also increases the risk that data will be made accessible to unauthorized users. An example of DAC method is file system permissions. On the file system, each file and folder has an owner. The owner can use ACL and decide which users or group of users have access to the file or folder.</li><br>
<li><b>Non-discretionary access control:</b> Also known as RBAC (role-based access control), access controls using RBAC are based on a user's job function within the organization, and access is allowed or denied based on a set of rules that are defined by a system administrator. In many organizations in industry and civilian government, the end users do not "own" the information for which they are allowed access. For these organizations, the corporation or agency is the actual owner of system objects, and discretionary access control may not be appropriate. RBAC allows and promotes the central administration of an organizational specific security policy. An example of using RBAC is allowing an analyst to be able to only read the firewall logs, but not be able to change any of the firewall configurations.</li>
</ul>
<br>
In addition to the access models above, other basic access control principles include the following:<br>
<br>
<ul>
<li>The principle of least privilege specifies a limited, as-needed approach to granting user and process access rights to specific information and tools. Access rights should be time-based in order to limit the resource's access to only the time that is needed to complete necessary tasks. Granting access beyond this scope increases the potential for malicious manipulation of sensitive data or processes by unauthorized actors. The assigning of access rights limits system-damaging attacks from users, regardless of whether they are intentional. All users must be authenticated and authorized, and should only be authorized at the lowest privilege level required to perform their functions.</li><br>
<li>Separation of duties is the concept of having more than one person who is required to complete a task. Separation of duties is an internal control to prevent fraud and error.</li>
</ul>
<br>
<a name="Regulatory Compliance"></a>
<b>Regulatory Compliance</b><br>
Compliance regulations are a major driver for security in organizations of all kinds. They define not only the scope and parameters for the risk and security architectures of an organization, but also the liability for those organizations that fail to comply.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515973918.png" alt="" style="">
<br>
Current trends in regulatory compliance include the following:<br>
<br>
<ul>
<li>Strengthened enforcement</li><br>
<li>Global spread of data breach notification laws</li><br>
<li>More prescriptive regulations</li><br>
<li>Growing requirements regarding third parties (business partners)</li><br>
<li>Risk-based compliance on the rise</li><br>
<li>Compliance process streamlined and automated</li>
</ul>
<br>
The following list describes several examples of compliance regulations. The list has a United States bias. Other jurisdictions may have similar regulations, and the list is not intended to be comprehensive.<br>
<br>
<ul>
<li><b>Payment Card Industry Data Security Standard:</b> The PCI DSS is a proprietary information security standard for organizations that handle branded credit cards from the major card brands including Visa, MasterCard, American Express, Discover, and JCB. Private label cards, which are without a logo from a major card brand, are not included in the scope of the PCI DSS.</li><br>
<li><b>Health Insurance Portability and Accountability Act:</b> On the healthcare side, the HIPAA legislation, which was enacted in 1996, required the U.S. Department of Health and Human Services to develop a set of national standards for healthcare transactions. These standards provide assurance that the electronic transfer of confidential patient information will be as safe as, or safer than, paper-based patient records.</li><br>
<li><b>Sarbanes-Oxley Act:</b> The SOX Act of 2002 is legislation that was passed by the U.S. Congress to protect shareholders and the general public from accounting errors and fraudulent practices in the enterprise, as well as improve the accuracy of corporate disclosures. The law was created in response to several major corporate and accounting scandals, including those affecting Enron, Tyco International, Peregrine Systems, and WorldCom. These scandals resulted in a decline of public trust in accounting and reporting practices.</li><br>
<li><b>Federal Information Security Management Act:</b> The FISMA of 2002 was intended to bolster computer and network security within the U.S. government and affiliated parties by requiring yearly audits. FISMA also brought attention within the U.S. government to cybersecurity, which the U.S. government had previously largely neglected.</li><br>
<li><b>Gramm-Leach-Bliley Act:</b> The GLBA of 1999 erased longstanding antitrust laws that prohibited banks, insurance companies, and securities firms from merging and sharing information with one another. The idea was that smaller firms would then be able to pursue acquisitions or alliances, or both, that would help encourage competition against many of the larger financial institutions. Included in the GLBA were several consumer privacy protections. Namely, companies must tell their customers what kinds of data they plan to share and with whom, and they must give their customers a chance to opt out of that data sharing.</li><br>
<li><b>Personal Information Protection and Electronic Documents Act:</b> The PIPEDA or the PIPED Act is a Canadian law relating to data privacy. It governs how private sector organizations collect, use, and disclose personal information while conducting commercial business.</li><br>
<li><b>Data Protection Directive (95/46/EC):</b> The Directive 95/46/EC (on the protection of individuals regarding the processing of personal data and on the free movement of such data) is a European Union directive that was adopted in 1995 which regulates the processing of personal data within the European Union.</li><br>
<li><b>Basel II:</b> Basel II is the second of the Basel Accords, which are recommendations on banking laws and regulations that are issued by the Basel Committee on Banking Supervision. Basel II, initially published in June 2004, was intended to create an international standard for banking regulators to control how much capital banks need to put aside to guard against the types of financial and operational risks banks face.</li><br>
<li><b>Digital Millennium Copyright Act:</b> The DMCA is a United States copyright law that implements two 1996 treaties of the World Intellectual Property Organization (WIPO). It criminalizes production and dissemination of technology, devices, or services that are intended to circumvent measures (commonly known as digital rights management or DRM) that control access to copyrighted works. It also criminalizes the act of circumventing an access control, regardless of actual infringement of copyright itself. In addition, the DMCA heightens the penalties for copyright infringement on the Internet.</li><br>
<li><b>Safe Harbor Act:</b> Related to the Organization for Economic Co-operation and Development (OECD) principles and their impact on international trade is the regulatory framework of a Safe Harbor Agreement. From the EU perspective, data transfer can happen only if there is a determination of adequate privacy processes and safeguards in place. The EU does not automatically grant that assurance of adequacy for non-EU member nations, like the United States or Canada does. To facilitate data transfer, to enable international trade, and to bridge any privacy differences, the EU, and United States, through the Department of Commerce, have developed a Safe Harbor framework that satisfies the adequacy requirement.</li>
</ul>
<br>
<a name="Information Security Management"></a>
<b>Information Security Management</b><br>
Information security management is the identification of an organization's assets, followed by the development, documentation, and implementation of policies and procedures for protecting these assets. Security management is often challenging to accomplish in the changing landscape of mobile workers and virtual data centers; cloud computing-based services add more complexity.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515974957.png" alt="" style="">
<br>
Security analysts should be familiar with the information security management system and processes being implemented inside their organization. As with all management processes, the information security management system and processes must remain effective and efficient in the long term, and adapt to changes in the internal organization and external environment.<br>
<br>
Plan–do–check–act is an iterative four-step management method that is used in business for the control and continual improvement of processes and products. It is also known as the Deming circle/cycle/wheel:<br>
<br>
<ul>
<li>The <b>Plan</b> phase is about designing the ISMS (Information Security Management System), assessing information security risks and selecting appropriate controls.</li><br>
<li>The <b>Do</b> phase involves implementing and operating the controls.</li><br>
<li>The <b>Check</b> phase is to review and evaluate the performance (efficiency and effectiveness) of the ISMS.</li><br>
<li>In the <b>Act</b> phase, changes are made where necessary to bring the ISMS to peak performance.</li>
</ul>
<br>
The list below details some of the common security management systems/processes:<br>
<br>
<ul>
<li>IT asset management entails collecting inventory, financial, and contractual data to manage the IT asset throughout its life cycle. IT asset management depends on robust processes, with tools to automate manual processes.</li><br>
<li>Configuration management is the process for establishing and maintaining consistency of a product's performance, functional requirements, and design throughout the product's life cycle.</li><br>
<li>Patch management involves acquiring, testing, and the installing of patches or code changes to the IT systems.</li><br>
<li>Vulnerability management is the practice of identifying, classifying, remediating, and mitigating vulnerabilities in software, firmware, and hardware.</li><br>
<li>MDM (Mobile Device Management) is a type of security management software that is utilized by IT to monitor, manage, and secure employees' mobile devices.</li>
</ul>
<br>
The best way to manage security risk and compliance requirements is through a systematic and comprehensive approach that is based on industry best practices.<br>
<br>
There are two widely recognized and widely deployed IT security control frameworks:<br>
<br>
<ul>
<li>Control Objectives for Information and Related Technologies (COBIT) is a good-practice framework. The framework was created by international professional association ISACA for IT management and IT governance. COBIT provides an implementable set of controls over information technology and organizes them around a logical framework of IT-related processes and enablers.</li><br>
<li>ISO/IEC 27002:2013 provides guidelines for organizational information, security standards, and information security management practices, including the selection, implementation, and management of controls, taking into consideration the organization's information security risk environment.<br>
<br>
It is designed to be used by organizations that intend to:<br>
<br>
<ul>
<li>Select controls within the process of implementing an information security management system that is based on ISO/IEC 27001</li><br>
<li>Implement commonly accepted information security controls</li><br>
<li>Develop their own information security management guidelines</li>
</ul>
</li>
</ul>
<br>
These two IT governance frameworks can be used together to help manage IT-related risk and network security compliance audit requirements, as well as the needs of current corporate governance and internal control requirements.<br>
<br>
<a name="Security Operations Center"></a>
<b>Security Operations Center</b><br>
The Verizon 2015 Data Breach Investigation Report showed that the time it took to breach 60 percent of the businesses that were covered in their report was merely minutes. Breaches tend to happen very quickly and on average take a long time to be detected by the targeted organization. These numbers demonstrate the importance of having an effective SOC (Security Operations Center).<br>
<br>
The SOC is the facility where enterprise information systems (web sites, applications, databases, data centers and servers, networks, desktops, other endpoints, and so on) are monitored, assessed, and defended.<br>
<br>
The SOC and the NOC complement each other and work in tandem. The NOC is usually responsible for monitoring and maintaining the overall network infrastructure—its primary function is to ensure uninterrupted network service.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515976068.png" alt="" style="">
<br>
A SOC is related to the people, processes, and technologies involved in providing situational awareness through the detection, containment, and remediation of information security threats. Using a measured, consistent, and creative approach to security incident response and security monitoring delivers the most effective and efficient results for the organization. This approach makes human analysts the most critical component of any SOC. SOC staffing may include different tiers/levels of security analysts, SOC managers, specialists focusing on malware reverse engineering, computer and mobile device forensics, penetration and vulnerability testing, and so on.<br>
<br>
SOC operations typically are based around an SIEM system, which aggregates and correlates data from security feeds, such as network discovery and vulnerability assessment systems, risk and compliance systems, log management systems, penetration testing tools, firewalls, IPS, NetFlow analysis systems, threat intelligence feeds, host antivirus systems, web security appliances, and email security appliances. The SIEM technology creates a "single pane of glass" for the security analysts to monitor the enterprise.<br>
<br>
There are three general types of security operations centers as follows:<br>
<br>
<ul>
<li>The <b>threat-centric SOC</b> proactively hunts for threats on the network. Most threat-centric SOCs employ 24×7 hunting through all the collected security data to discover active exploitation. Upon discovery, security investigators will typically provide guidance to safely mitigate the attacks.</li><br>
<li>The <b>compliance-based SOC</b> focuses on the state of the company’s overall security posture as it relates to compliancy testing, penetration testing, and vulnerability testing.</li><br>
<li>The <b>operational-based SOC</b> focuses on maintaining the operational integrity and functionality of the different security controls.</li>
</ul>
<br>
The present state of cybercrime calls for organizations’ defense-in-depth strategy to shift from the current “detect and prevent” approach, to a “threat-focused" paradigm. Being threat-focused means thinking like an attacker, applying visibility and context to understand and adapt to changes in the environment and then evolving the protections to take action and stop threats.<br>
<br>
Normal tasks for a security analyst working at a threat-focused SOC includes seeking out malicious activity that was not identified by traditional alerting mechanisms, and documenting the malicious activity hunting process in a living play-book that is continuously updated as threats and malicious campaigns evolve.<br>
<br>
<pre>
<code>
Note:
Companies that do not have their own managed SOC can out-source their security services to a managed security services provider. Managed security services can be CPE-based, cloud-based, or can be a hybrid CPE/cloud-based solution.
</code>
</pre>
<br>
<b>Big Data Analytics</b><br>
According to the Breach Level Index, between July and September of 2014, an average of 23 data records were lost or stolen every second—close to 2 million records every day. This data loss will continue as attackers become increasingly sophisticated in their attacks. Given this reality, traditional means of threat detection can no longer be relied upon. Technically advanced attackers often leave behind clue-based evidence of their activities, but uncovering them usually involves filtering through mountains of logs and telemetry data. The application of big data analytics to this problem has become a necessity.<br>
<br>
To help organizations leverage big data in their security strategy, Cisco prototyped the open source security analytics framework: OpenSOC in September 2013. By December 2013, Hortonworks joined, then took over, the OpenSOC project. In September 2014, OpenSOC became generally available.<br>
<br>
The following are the goals of OpenSOC:<br>
<br>
<ul>
<li>To provide a collaborative open source community for development of an extensible and scalable advanced security analytics tool.</li><br>
<li>To encourage open communication for additional features and identification of deficiencies for a stable and functionally usable tool.</li><br>
<li>To identify key feature enhancements to drive technology efforts around efficient security analytics.</li>
</ul>
<br>
By integrating numerous elements of the Hadoop ecosystem, such as Storm, Kafka, and Elasticsearch, the OpenSOC framework helps organizations make big data part of their technical security strategy by providing a platform for the application of anomaly detection and incident forensics to the data loss problem. Hadoop is an open-source software framework for distributed storage, and distributed processing of very large data sets.<br>
<br>
OpenSOC provides a scalable platform incorporating capabilities such as full-packet capture indexing, storage, data enrichment, stream processing, batch processing, real-time search, and telemetry aggregation. It also provides a centralized platform to effectively enable security analysts to rapidly detect and respond to advanced security threats.<br>
<br>
OpenSOC welcomes participation from all people and organizations for development, enhancements, and/or implementation support. For more information and to contribute to the OpenSOC community, visit the OpenSOC community website at http://opensoc.github.io/<br>
<br>