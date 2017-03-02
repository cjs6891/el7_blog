---
layout: page
title: ldap and identity management
---

Understanding LDAP<br>
Lightweight Directory Access Protocol (LDAP) was developed as a protocol to get information from an X.500 directory service. This service was originally developed as an address book. Currently, LDAP has developed further into a service that can be used as a centralized authentication service. LDAP is an open standard, and many directory services are available that are using LDAP as their access protocol.<br>
<br>
LDAP directory servers are organized in a hierarchal, distributed and replicated way.
<ul>
<li>LDAP is hierarchal; it's organized like DNS, using domains (which in LDAP are called containers) to organize the leaf objects (such as users) in a way that makes sense.</li>
<li>LDAP is distributed because the entire database doesn't have to be available on one single server. The different containers in the LDAP hierarchy can be spread over multiple servers to make information available where it needs to be available. To distribute the information available in the LDAP directory, the directory tree is partitioned into different parts.</li>
<li>LDAP is replicated; multiple copies of one partition can be created.</li>
</ul>
<br>
<code>authconfig, authconfig-tui</code>- an interface for configuring system authentication resources