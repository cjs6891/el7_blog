---
layout: page
title: "Cisco CCNA Cyber Ops SECFND 210-250, Section 4: Understanding Basic Cryptography Concepts"
---

<a href="#Impact of Cryptography on Security Investigations">4.2 Impact of Cryptography on Security Investigations</a><br>
<a href="#Cryptography Overview">4.3 Cryptography Overview</a><br>
<a href="#Hash Algorithms">4.4 Hash Algorithms</a><br>
<a href="#Encryption Overview">4.5 Encryption Overview</a><br>
<a href="#Cryptanalysis">4.6 Cryptanalysis</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>
<a href="#">4.</a><br>

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

<a name="Impact of Cryptography on Security Investigations"></a>
<b>Impact of Cryptography on Security Investigations</b><br>
Over the years, numerous cryptographic algorithms have been developed and used in many different protocols and functions. Cryptography is by no means static. Steady advances in computing and the science of cryptanalysis have made it necessary to continually adopt newer, stronger algorithms, and larger key sizes. The security analyst job role requires a good understanding of the different cryptographic algorithms and operations. The security analyst must be able to investigate security incidents involving the use of cryptography.<br>
<br>
Security analysts must also continue their cryptography study to stay up-to-date on the latest cryptographic innovations. Furthermore, security analysts need to understand that attackers can attack the cryptographic algorithms, and they can use cryptography to hide their attacks.<br>
<br>
A cryptographic attack is a method for circumventing the security of a cryptographic system by finding a weakness in the cryptographic algorithms. For example, in 2014, the OpenSSL Heartbleed vulnerability was assigned the common vulnerabilities and exposure ID CVE-2014-0160. This vulnerability leverages the implementation of the TLS heartbeat extension (RFC 6520) and the way an SSL enabled server validates heartbeat requests to provide a response. The vulnerability could allow an attacker that has crafted a heartbeat request with an improper length to receive responses that contain private data that is stored in the server memory.<br>
<br>
Cryptography can also be used by attackers as an attack technology. For example, attackers can also use TLS/SSL encryption to hide their attack's command and control traffic. Attackers use their command and control infrastructure to maintain communications with the compromised machines. TLS/SSL encryption makes the detection of the command and control communications very difficult. One detection method is to perform TLS/SSL decryption and inspection, and then run signatures that are based on detection over the decrypted traffic. Another method of detection is to perform traffic analysis using NetFlow to detect anomalous TLS/SSL flows. NetFlow will be discussed in a later section.<br>
<br>
The example below illustrates one of the very basic skills that are required by the security analysts when investigating security incidents involving the use of digital certificates. A digital certificate contains a set of information about an entity. Explore the details of what's in a digital certificate later on in this section.<br>
<br>
The two figures below show two different digital certificates.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515426141.png" alt="" style="">
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515426193.png" alt="" style="">
<br>
As the security analyst or even as an end user, one must be able to recognize the difference between these two digital certificates. The security analyst must be able to determine if the presented server's digital certificate is valid or not.<br>
<br>
The security analyst should be able to determine that the top one is a valid digital certificate that was issued to http://www.cisco.com by Symantec, and this digital certificate is valid until January 28, 2018. Symantec is the trusted third party that signed the digital certificate.<br>
<br>
The security analyst should also be able to determine that the bottom one is an untrusted digital certificate because it is a self-signed digital certificate. The certificate was issued to security onion, and it was also issued by security onion.<br>
<br>
<a name="Cryptography Overview"></a>
<b>Cryptography Overview</b><br>
Cryptography is the practice and study of techniques to secure communications in the presence of third parties. Historically, cryptography was synonymous with encryption. Its goal was to keep messages private. In modern times, cryptography includes other responsibilities:<br>
<br>
<ul>
<li><b>Confidentiality:</b> Ensuring that only authorized parties can read a message</li><br>
<li><b>Data integrity:</b> Ensuring that any changes to data in transit will be detected and rejected</li><br>
<li><b>Origin authentication:</b> Ensuring that any messages received were actually sent from the perceived origin</li><br>
<li><b>Non-repudiation:</b> Ensuring that the original source of a secured message cannot deny having produced the message</li>
</ul>
<br>
Cryptanalysis is the practice and study of determining and exploiting weakness in cryptographic techniques. Cryptology is an umbrella term which covers both cryptography and cryptanalysis. There is a symbiotic relationship between the two disciplines, because each improves the other one. National security organizations employ members of both disciplines and put them to work against each other.<br>
<br>
At times, one discipline has been further along than the other. For example, during the Hundred Years' War between France and England, the cryptanalysts were ahead of the cryptographers. France believed that the Vigenère cipher was unbreakable; however, the British were able to break it. Some historians believe that World War II largely turned on the fact that the winning side on both fronts was much more successful than the losing side was at cracking the encryption of its adversary. Currently, it is believed that cryptographers are further along than cryptanalysts.<br>
<br>
It is an ironic fact of cryptography that it is impossible to prove that an algorithm is secure. You can prove only that it is not vulnerable to known cryptanalytic attacks. If there are methods that have been developed but are unknown to the cryptographers, then an algorithm may be able to be cracked. You can prove only invulnerability to known attacks, except for a brute-force attack.<br>
<br>
All algorithms are vulnerable to brute force. If every possible key is tried, one of the keys has to work. Therefore, no algorithm is unbreakable. The best you can hope for are algorithms that are vulnerable only to brute-force attacks.<br>
<br>
<b>Cryptography History</b><br>
Cryptography began in diplomatic circles thousands of years ago. Messengers from the court of a ruler would take encrypted messages to other courts. Occasionally, other courts that were not involved in the communication would attempt to steal any message that was sent to a rival kingdom. Encryption was first used for this purpose.<br>
<br>
Not long after, military commanders started using encryption to secure messages. These messengers faced greater challenges than the diplomatic messenger faced, because killing the messenger to get the message was very common. With such high stakes involved, military commanders used encryption to secure their military communications.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515427806.png" alt="" style="">
<br>
There are many famous ciphers from history. The cipher that is attributed to Julius Caesar was a simple substitution cipher that was used on the battlefield to quickly encrypt messages that could easily be decrypted by field commanders. Thomas Jefferson, the third president of the United States, was a man of many interests. Among his many inventions was an encryption system that was likely used when serving as Secretary of State from 1790 to 1793.<br>
<br>
In 1918, Arthur Scherbius invented a machine that served as a template for the machines that all the major participants in World War II used. He called the machine Enigma and sold it to Germany, estimating that if 1000 cryptanalysts tested four keys per minute, all day, every day, it would take 1.8 billion years to try them all.<br>
<br>
During World War II, both the axis and Allies had machines that were modeled after the Scherbius machine. These machines were the most sophisticated encryption devices that had been developed then. In response to those machines, the British arguably invented the first computer in the world, the Colossus, to break the encryption that was used by the Enigma.<br>
<br>
<b>Ciphers for Everyone</b><br>
A cipher is an algorithm for performing encryption and decryption. Ciphers are a series of well-defined steps that you can follow as a procedure. Different types of ciphers have proven useful historically.<br>
<br>
<ul>
<li><b>Substitution ciphers:</b> Substitution ciphers substitute one letter for another. In their simplest form, substitution ciphers retain the letter frequency of the original message. The cipher that was attributed to Julius Caesar was a substitution cipher. Every day was assigned a different key, and that key was used to adjust the alphabet accordingly. For example, if the key for a certain day was five, then an “A” was moved five letters ahead in the alphabet, resulting in an encoded message that used “F” in place of “A.” “B” was then “G,” “C” was “H,” and so on. The next day, the key might be eight, and the process would begin again with “A” now becoming “I,” “B” becoming “J,” and so on.<br>
<br>
One of the drawbacks of substitution ciphers is that if the message is long enough, it may be vulnerable to what is called “frequency analysis,” because it retains the frequency patterns of letters that are found in the original message. Because of this weakness, polyalphabetic ciphers were invented.</li><br>
<li><b>Polyalphabetic ciphers:</b> Polyalphabetic ciphers are based on substitution, using multiple substitution alphabets. The famous Vigenère cipher is an example. That cipher uses a series of different Caesar ciphers that are based on the letters of a keyword. It is a simple form of polyalphabetic substitution and is therefore invulnerable to frequency analysis.<br>
<br>
To illustrate how this type of cipher works, suppose that a key of “SECRETKEY” is used to encode “ATTACK AT DAWN.” The “A” is encoded by looking at the row starting with “S” for the letter in the “A” column. In this case, the “A” is replaced with “S.” Then you look for the row that begins with “E” for the letter “T,” resulting in “X” as the second character. If you continue this encoding method, the message “ATTACK AT DAWN” is encrypted as “SXVRGDKXBSAP.”</li><br>
<li>Transposition ciphers: Transposition ciphers rearrange or permutate letters, instead of replacing them. Transposition is also known as permutation. An example of this type of cipher takes the message “THE PACKAGE IS DELIVERED” and transposes it to read “DEREVILEDSIEGAKCAPEHT.” In this example, the key is to reverse the letters. The Rail Fence Cipher is a transposition cipher in which the words are spelled out as if they are a rail fence. Each subsequent letter of the text is written downwards and diagonally on successive "rails" of an imaginary fence until the bottom rail is reached. At that point, each subsequent letter is written upwards and diagonally until the top rail is reached, and so on. The number of rails used is the cipher key. The example below illustrates a key of three.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515428550.png" alt="" style="">
<br>
<pre>
<code>
Note:
In order to read the message, simply read diagonally up and down, following the rail fence. You will find that the message "THE COVER IS BLOWN FLEE AT ONCE" has been encoded as "TOIOLTEHCVRSLWFEAOCEEBNEN."
</code>
</pre>
<br>
Some modern algorithms, such as DES and 3DES, still use transposition as part of the algorithm.</li><br>
<li><b>One-time pad:</b> The one-time pad was invented and patented by Gilbert Vernam in 1917 while working at AT&T. A one-time pad is also known as a Vernam cipher. Vernam's idea was a stream cipher that would apply the XOR operation to plaintext with a key. Joseph Mauborgne, a captain in the U.S. Army Signal Corps, contributed the idea of using random data as a key. This combined idea is so significant that the NSA has called this patent “perhaps the most important in the history of cryptography.”<br>
<br>
There are several difficulties inherent in using one-time pads in the real world. The first is the challenge of creating random data. Computers, because they have a mathematical foundation, are incapable of creating truly random data. Also, if the key is used more than once, it is trivial to break. Key distribution is also challenging.</li>
</ul>
<br>
<a name="Hash Algorithms"></a>
<b>Hash Algorithms</b><br>
Hashing is a mechanism that is used for data integrity assurance. Hashing is based on a one-way mathematical function: functions that are relatively easy to compute, but significantly difficult to reverse. Grinding coffee is a good example of a one-way function: It is easy to grind coffee beans, but it is almost impossible to put back all the tiny pieces together to rebuild the original beans.<br>
<br>
The figure below illustrates how hashing is performed. Data of an arbitrary length is input into the hash function, and the result of the hash function is the fixed-length hash, which is known as the “digest” or “fingerprint.” When the same data is passed through a hash algorithm twice, the output is identical. Any small modification to the data produces an entirely different output. This characteristic is often referred to as the avalanche effect. Data is deemed to be authentic if running the data through the hash algorithm produces the expected fingerprint. Since hash algorithms produce a fixed-length output, there are a finite number of possible outputs. It is possible for two different inputs to produce an identical output. They are referred to as hash collisions.<br>
<br>
Hashing is similar to the calculation of CRC checksums, but it is much stronger cryptographically. CRCs were designed to detect randomly occurring errors in digital data where hash algorithms were designed to assure data integrity even when data modifications are intentional with the objective to pass fraudulent data as authentic. One primary distinction is the size of the digest produced. CRC checksums are relatively small, often 32 bits. Commonly used hash algorithms produce digests in the range of 128 to 512 bits in length. It is relatively easier for an attacker to find two inputs with identical 32-bit checksum values than it is to find two inputs with identical digests of 128 to 512 bits in length.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515430414.png" alt="" style="">
<br>
The figure below shows one use of hash algorithms to provide data integrity. Organizations that offer software for download often publish hash digests on the download page that can be used to verify data integrity of the downloaded software.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515430474.png" alt="" style="">
<br>
<b>Cryptographic Authentication Using Hash Technology</b><br>
Two systems that have agreed on a secret key can use the key along with a hash function to verify data integrity of communication between them by using a keyed hash. A message authentication code is produced by passing the message data along with the secret key through a hash algorithm. Only the sender and the receiver know the secret key, and the output of the hash function now depends on the message data and the secret key. Therefore, only parties who have access to that secret key can compute the appropriate hash digest. This behavior defeats man-in-the-middle attacks and provides authentication of the data origin. If two parties share a secret key and use hash technology for authentication, receipt of a properly constructed message authentication code indicates that the other party was the originator of the message, because it is the only other entity possessing the secret key.<br>
<br>
The figure below illustrates how the message authentication code is created. Data of an arbitrary length is input into the hash function, together with a secret key. The result is the fixed-length hash that depends on the data and the secret key.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515430631.png" alt="" style="">
<br>
<pre>
<code>
Note:
RFC 2104 describes a particularly strong hash-based cryptographic authentication mechanism called HMAC (Hashed Message Authentication Code). The HMAC algorithm actually performs two nested hash computations of the message data, key, and padding material processed with Boolean logic. The HMAC algorithm is used for data integrity by IPsec.
</code>
</pre>
<br>
<b>Cryptographic Authentication in Action</b><br>
The figure below illustrates cryptographic authentication in action. The sender wants to ensure that the message is not altered in transit and wants to provide a way for the receiver to authenticate the origin of the message.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515430786.png" alt="" style="">
<br>
The sending device inputs data and the secret key into the hashing algorithm and calculates the fixed-length message authentication code, or fingerprint. This authenticated fingerprint is then attached to the message and sent to the receiver. The receiving device removes the fingerprint from the message and uses the received message with its copy of the secret key as input to the same hashing function. If the fingerprint that is calculated is identical to the fingerprint that was received, then data integrity has been verified. Also, the origin of the message is authenticated, because only the sender possesses a copy of the shared secret key. The keyed hash function has ensured the authenticity of the message.<br>
<br>
Cisco products use hashing for entity authentication, data integrity, and data authenticity purposes:<br>
<br>
<ul>
<li>IPsec gateways and clients use hashing algorithms to verify packet integrity and authenticity. The algorithm, which is defined in RFC 2104, is more complex than a simple keyed hash and uses two hash computations to produce the message authentication code.</li><br>
<li>Cisco IOS routers use keyed hashing with secret keys to add authentication information to routing protocol updates.</li><br>
<li>Cisco software images that you can download from Cisco.com have an MD5-based checksum that is available, so that customers can check the integrity of downloaded images.</li><br>
<li>Hashing can also be used in a feedback-like mode to encrypt data. For example, TACACS+ uses MD5 to encrypt its session.</li>
</ul>
<br>
The figure below shows how route authentication occurs on Cisco routers. Route authentication using a keyed hash allows the validation of route integrity. If the route information is tampered with during transit, the receiving router upon calculating the keyed hash finds the computed hash to be different from the received hash. Even if an attacker intercepts the route information and injects a new hash after changing the route information, the attempt fails, because the attacker does not know the secret key. Without the secret key, the attacker cannot produce a message authentication code that will be accepted by the receiver.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515431103.png" alt="" style="">
<br>
<pre>
<code>
Note:
You can configure neighbor authentication for the following routing protocols: BGP, IS-IS, EIGRP, OSPF, and RIPv2.
</code>
</pre>
<br>
This technique is only as strong as the secret key. If the attacker knows the secret key, they can generate a malicious routing update and the appropriate keyed hash that will be accepted by the peer routers. Also note that this technique does not provide privacy. While it prevents an attacker from manipulating a routing update that they intercept, it does not prevent the attacker from reading the routing update.<br>
<br>
<b>Comparing Hashing Algorithms</b><br>
The three most commonly used cryptographic hash functions are MD5, SHA-1, and SHA-2.<br>
<br>
The MD5 algorithm is a ubiquitous hashing algorithm that was developed by Ron Rivest. Although MD5 is used in various Internet applications today, it is not recommended for new applications.<br>
<br>
MD5 is a one-way function that makes it easy to compute a hash from the given input data, but makes it unfeasible to compute the original input data that are given only a hash. MD5 is essentially a complex sequence of simple binary operations, such as XORs and rotations, that is performed on input data and produces a 128-bit digest. MD5 was originally thought to be collision-resistant, but has been shown to have collision vulnerabilities.<br>
<br>
<pre>
<code>
Note:
Collision-resistant means that two messages with the same hash are very unlikely to occur.
</code>
</pre>
<br>
The main algorithm itself is based on a compression function, which operates on blocks. The input is a data block, plus feedback of previous blocks. The 512-bit blocks are divided into sixteen 32-bit subblocks. These blocks are then rearranged with simple operations in a main loop, which consists of four rounds. The output of the algorithm is a set of four 32-bit blocks, which concatenate to form a single 128-bit hash value. The message length is also encoded into the digest.<br>
<br>
The U.S. NIST developed SHA, the algorithm that is specified in the Secure Hash Standard (SHS). SHA-1 is a revision to SHA that was published in 1994. The revision corrected an unpublished flaw in SHA. Its design is very similar to the Message Digest 4 (MD4) family of hash functions that Ron Rivest developed.<br>
<br>
The SHA-1 algorithm takes a message of up to 2^64 bits in length and produces a 160-bit message digest. The algorithm is slightly slower than MD5, but the larger message digest makes it more secure against brute-force collision and inversion attacks.<br>
<br>
Secure Hash Algorithm 2 (SHA-2) specifies six SHAs—SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224 and SHA-512/256. When a message of any length up to 2^64 bits (for SHA-224 and SHA-256) or up to 2^128 bits (for SHA-384 and SHA-512) is input to an SHA-2 algorithm, the result is a message digest that ranges in length from 224 to 512 bits, depending on the algorithm. SHA-512 is actually more efficient to implement than SHA-256 on 64-bit computational systems. SHA-512/224 and SHA-512/256 are based on the SHA-512 algorithm, modifying the internal initialization vector and truncating the digest output to 224 bits and 256 bits respectively. They were introduced to allow the use of the SHA-512 algorithm in situations where it is faster than SHA-256 but a smaller digest size is desirable.<br>
<br>
The SHA-2 family of hash functions was approved by NIST for use by federal agencies in 2006, for all applications using SHAs. The publication encouraged all federal agencies to stop using SHA-1 for digital signatures, digital time stamping, and other applications that require collision resistance when practical, and it mandated the use of the SHA-2 family of hash functions for these applications after 2010. After 2010, federal agencies used SHA-1 only for the following applications: HMACs, key derivation functions (KDFs), and random number generators (RNGs). This change was triggered in 2005, when security flaws were identified for SHA-1 in theoretical exploits that exposed weakness to collision attacks.<br>
<br>
<a name="Encryption Overview"></a>
<b>Encryption Overview</b><br>
Encryption is the process of disguising a message in such a way as to hide its original contents. With encryption, the plaintext readable message is converted to ciphertext, which is the unreadable, “disguised” message. Decryption reverses this process. Encryption is used to guarantee confidentiality so that only authorized entities can read the original message.<br>
<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1515435916.png" alt="" style="">
<br>
Old encryption methods, such as the Caesar cipher, were based on the secrecy of the algorithm to achieve confidentiality. It is difficult to maintain the secrecy of an encryption algorithm, and it is difficult to devise new secret encryption algorithms to replace ones which are no longer secret. Modern encryption relies on public algorithms that are cryptographically strong using secret keys. It is much easier to change keys than it is to change algorithms. In fact, most cryptographic systems dynamically generate new keys over time, limiting the amount of data that may be compromised with the loss of a single key.<br>
<br>
Encryption can provide confidentiality at various layers of the OSI model, such as the following:<br>
<br>
<ul>
<li>Encrypt application layer data, such as encrypting email messages with PGP (Pretty Good Privacy).</li><br>
<li>Encrypt session layer data using a protocol such as SSL or TLS.</li><br>
<li>Encrypt network layer data using protocols such as those provided in the IPsec protocol suite.</li><br>
<li>Encrypt data link layer using MACsec (IEEE 802.1AE) or proprietary link-encrypting devices.</li>
</ul>
<br>
<b>Encryption Algorithm Features</b><br>
A good cryptographic algorithm is designed in such a way that it resists common cryptographic attacks. The best way to break data that is protected by the algorithm is to try to decrypt the data using all possible keys. The amount of time that such an attack needs depends on the number of possible keys, but the time is generally very long. With appropriately long keys, such attacks are usually considered unfeasible.<br>
<br>
Variable key lengths and scalability are also desirable attributes of a good encryption algorithm. The longer the encryption key is, the longer it takes an attacker to break it. For example, a 16-bit key means that there are 65,536 possible keys, but a 56-bit key means that there are 7.2 x 10^16 possible keys. Scalability provides flexible key length and allows you to select the strength and speed of encryption that you need.<br>
<br>
Changing only a few bits of the plaintext message causes its ciphertext to change completely, which is known as an avalanche effect. The avalanche effect is a desired feature of an encryption algorithm, because it allows very similar messages to be sent over an untrusted medium, with the encrypted (ciphertext) messages being completely different.<br>
<br>
You must carefully consider export and import restrictions when you use encryption internationally. Some countries do not allow the export of encryption algorithms, or they allow only the export of those algorithms with shorter keys. Some countries impose import restrictions on cryptographic algorithms.<br>
<br>
In January 2000, the restrictions that the U.S. Department of Commerce placed on export regulations were dramatically relaxed. Currently, any cryptographic product is exportable under a license exception, unless the end users are governments outside of the United States or are embargoed.<br>
<br>
<b>Encryption Algorithms and Keys</b><br>
A key is a required parameter for encryption algorithms. There are two classes of encryption algorithms, which differ in their use of keys:<br>
<br>
<ul>
<li><b>Symmetric encryption algorithm:</b> Uses the same key to encrypt and decrypt data</li><br>
<li><b>Asymmetric encryption algorithm:</b> Uses different keys to encrypt and decrypt data</li>
</ul>
<br>
<a name="Cryptanalysis"></a>
<b>Cryptanalysis</b><br>
Cryptanalysis is the practice of breaking codes to obtain the meaning of encrypted data. An attacker who tries to break an algorithm or encrypted ciphertext may use one of the following attacks:<br>
<br>
<ul>
<li><b>Brute-force attack:</b> In a brute-force attack, an attacker tries every possible key with the decryption algorithm, knowing that eventually one of the keys will work. All encryption algorithms are vulnerable to this attack. On average, a brute-force attack will succeed about 50 percent of the way through the key space, which is the set of all possible keys. The objective of modern cryptographers is to have a key space large enough that it takes too much money and too much time to accomplish a brute-force attack.<br>
<br>
<pre>
<code>
Note:
Existing technology and computing power has resulted in cracking machines that are able to crack DES (Data Encryption Standard) in just a few hours. It is estimated that it would take 149 trillion years to crack AES (Advanced Encryption Standard) using the same method.
</code>
</pre>
</li><br>
<li><b>Ciphertext-only attack:</b> In a ciphertext-only attack, the attacker has the ciphertext of several messages, all of which have been encrypted using the same encryption algorithm, but the attacker has no knowledge of the underlying plaintext. The job of the attacker is to recover the plaintext of as many messages as possible—or better yet, to deduce the key or keys that are used to encrypt the messages in order to decrypt other messages that are encrypted with the same keys. The attacker can use statistical analysis to achieve the result. These kinds of attacks are no longer practical, because modern algorithms produce pseudorandom output that is resistant to statistical analysis.</li><br>
<li><b>Known-plaintext attack:</b> In a known-plaintext attack, the attacker has access to the ciphertext of several messages but also knows something about the plaintext that underlies that ciphertext. With knowledge of the underlying protocol, file type, or some characteristic strings that may appear in the plaintext, the attacker uses a brute-force attack to try keys, until decryption with the correct key produces a meaningful result. This attack may be the most practical attack, because attackers can usually assume the type and some features of the underlying plaintext, if they can only capture the ciphertext. However, modern algorithms with enormous key spaces make it unlikely for this attack to succeed, because on average an attacker has to search through at least half of the key space to be successful.</li><br>
<li><b>Chosen-plaintext attack:</b> In a chosen-plaintext attack, the attacker chooses what data the encryption device encrypts and observes the ciphertext output. A chosen-plaintext attack is more powerful than a known-plaintext attack, because the attacker gets to choose the plaintext blocks to encrypt, allowing the attacker to choose plaintext that might yield more information about the key. This attack might not be very practical, because it is often difficult or impossible to capture both the ciphertext and plaintext, unless the trusted network has been broken into and the attacker already has access to confidential information.</li><br>
<li><b>Chosen-ciphertext attack:</b> In a chosen-ciphertext attack, the attacker can choose different ciphertext to be decrypted and has access to the decrypted plaintext. With the pair, the attacker can search through the key space and determine which key decrypts the chosen ciphertext in the captured plaintext. For example, the attacker has access to a tamper-proof encryption device with an embedded key. The attacker must deduce the embedded key by sending data through the box. This attack is analogous to the chosen-plaintext attack. This attack might not be very practical, because it is often difficult or impossible to capture both the ciphertext and plaintext, unless the trusted network has been broken into, and the attacker already has access to confidential information.</li><br>
<li>Birthday attack: The birthday attack gets its name because of an amazing statistical probability that is involved in two individuals having the same birthday. According to statisticians, the probability that two people in a group of 23 people share the same birthday is greater than 50 percent.<br>
<br>
This particular attack is a form of brute-force attack against hash functions. If a specific function, when supplied with a random input, returns one of k equally likely values, then by repeating the function with different inputs, the same output is expected after 1.2k^1/2 number of times.<br>
<br>
<pre>
<code>
Note:
To test the birthday theory, input 365 in the place of k.
</code>
</pre>
<br></li><br>
<li><b>Meet-in-the-middle:</b> The meet-in-the-middle attack is a known-plaintext attack. In a meet-in-the-middle attack, the attacker knows a portion of the plaintext and the corresponding ciphertext. The plaintext is encrypted with every possible key, and the results are stored. The ciphertext is then decrypted by using every key, until one of the results matches one of the stored values.</li>
</ul>
<br>