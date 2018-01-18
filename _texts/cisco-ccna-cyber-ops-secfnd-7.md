---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 7: Understanding Common Network Application Attacks"
---

<a href="#Password Attacks">7.2 Password Attacks</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>
<a href="#">7.</a><br>

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

<a name="Password Attacks"></a>
<b>Password Attacks</b><br>
Password attacks have been an ongoing problem for network security engineers. Every year SplashData publishes a report on the most commonly used passwords that are leaked online. In 2014, they analyzed 3.3 million leaked passwords and reported the top 25. The password “password” was number 2 on the list. Six of the top 11 were numeric sequences starting with 1 and varying only in length of the sequence (for example, 123456). Five more of the top 25 were simple alpha-numeric sequences (such as abc123). There were a few clever, yet still poor, passwords such as trustno1 and letmein. The remaining 11 were simple dictionary words, all in lower case. These top 25 passwords represented 2.2% of the 3.3 million leaked passwords.<br>
<br>
Security analysts should be aware of the different password attack methods and implement countermeasures against password attacks. The following are some of the methods that attackers use to obtain users' passwords:<br>
<br>
<ul>
<li><b>Password guessing:</b> To perform password guessing, an attacker can either manually enter passwords or use a software tool to automate the process. Truly weak passwords can be susceptible to a lone attacker who is making informed guesses.</li><br>
<li><b>Brute-force attacks:</b> Brute-force password attacks are performed by computer programs that are called "password crackers." A password cracker performs a brute force crack by systematically trying every possible password until it succeeds. For example, it may start by trying all one-character passwords, then moving to two-character passwords, and so on, trying all possible combinations until they crack the password. With this method, the speed at which an attacker can obtain a password may depend on the speed of the attacker's computer (how many calculations it can perform per second), the speed of the attacker's Internet connection, and the length and complexity of the password. Many password crackers are available, and many at no cost.<br>
<br>
Although brute-force login attempts are by no means a new tactic for cybercriminals, their use increased threefold in recent years. Key targets for recent brute-force login attempts include widely used web CMS platforms such as WordPress. Successful attempts to gain unauthorized access to WordPress web servers give attackers the ability to upload backdoor scripts and other malicious scripts to compromised websites. Considering that there are more than 74 million WordPress web sites around the world, and that publishers are using the platform to create blogs, news sites, company sites, magazines, social networks, sports sites, and more, it is not surprising that many online criminals have their sights set on gaining access through the WordPress CMS. Other web CMSs, such as Joomla and Drupal, have been targeted as well. But it isn’t just the popularity of these CMSs that makes them desirable targets. Many of these web sites, though active, have been largely abandoned by their owners. There are likely millions of abandoned blogs and purchased domains sitting idle, and many are probably now owned by cybercriminals.</li><br>
<li><b>Dictionary attacks:</b> Dictionary attacks use word lists to structure login attempts. Word lists can contain millions of words, including words from natural language dictionaries and sports team names, profanity, and slang. Dictionary attacks are not always successful and are often attempted before a brute-force attack. In some ways, however, a dictionary attack is similar to a brute-force attack. It is an automated process that is performed by a password cracker program; the speed at which the attacker can obtain a password may depend on the speed of the attacker's computer (how many calculations it can perform per second), the speed of the attacker's Internet connection, and the length and complexity of the password. Many dictionary attack tools are available for free on the Internet. For example, Cisco security researchers have discovered a hub of dictionary data which included 8.9 million possible user name and password combinations, including strong passwords—not just the easy-to-crack “password123” variety. Stolen user credentials also help attackers keep their dictionary list well populated.</li><br>
<li><b>Phishing attacks:</b> Another way for attackers to find passwords is by indirectly asking the user. For example, a phishing email can direct victims to visit a malicious fake web site where they are asked to enter their personal information, such as their password or credit card, social security, and bank account numbers. An attacker may set up a web site that is of interest to the victim, and when the victim is lured to create an account on the attacker's site, the attacker captures the password knowing that many people reuse the same password, or major portions of it, for all their web accounts.</li>
</ul>
<br>
Password attacks can be online or offline. In an online password attack, an attacker makes repeated attempts to log in. The activity is visible to the authentication system, so the system can automatically lock the account after too many bad guesses. Account lockout disables the account and makes it unavailable for further attacks during the lockout period. The lockout period and the number of allowed logon attempts are configurable by a system administrator. It is also worth mentioning that online password attacks can actually be used as a form of DoS. If the lockout affects enough accounts, an organization can be greatly impacted by it.<br>
<br>
Offline password attacks are far more dangerous. In an online attack, the password has the protection of the system in which it is stored, but there is no such protection in offline attacks. In an offline attack, the attacker captures the password or the encrypted form of the password. The attacker can then make countless attempts to crack the password without being noticed. The longer and more complex a password is, the more difficult and time-consuming it is for attackers to crack it.<br>
<br>
Many authentication systems require a certain degree of password complexity. Specifying a minimum length of a password and forcing an enlarged character set (upper case, lower case, numeric, and special characters) can have an enormous influence on the feasibility of brute force attacks. However, if users attempt to meet the enlarged character set requirements by making simple adjustments, such as capitalizing the first letter and appending a number and an exclamation point (for example, changing unicorn to Unicorn1!), little is gained against a dictionary attack that uses simple transforms.<br>
<br>
Some common password attack tools that are openly available include Cain and Abel, John the Ripper, OphCrack, and L0phtCrack.<br>
<br>
A common approach to reduce the risk of password brute-force attacks is to lock the account or increase the delay between login attempts when there have been repeated failures. This can be effective in slowing down brute-force attacks and giving the incident response team time to react.<br>
<br>
Another countermeasure against password attacks is two-factor authentication. Two-factor authentication requires the attackers to have something more than the password to authenticate to the system. For example, requiring not only a password and user name, but also something that only the user has. For example, when you use your bank debit card to withdraw cash from the ATM machine, you also need a PIN that only you know.<br>
<br>
