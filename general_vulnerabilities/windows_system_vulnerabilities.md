# Windows System Vulnerabilities

[home](../README.md)
- [Example](#Example)

## Introduction

A system Vulnerability is that weaknesses of a system that allows threats to affect the system, generally in a negative manner. All around the world, there are vulnerabilities found in systems which expose systems to threats. With the advent of cybercrimes, there has been an n increase in finding vulnerabilities of systems for exploitations. Over the years, penetration testing has evolved as a major domain which aims at focusing on vulnerabilities of system. In this document, we focus on various vulnerabilities like Operating system vulnerabilities, protocol vulnerabilities, application vulnerabilities and various other vulnerabilities due to older versions of systems. We also present a few protection strategies for all these vulnerabilities for added security of systems and latest strands in security.


## Common Windows OS Vulnerabilities

There are many windows vulnerabilities discovered from the time Windows was launched. As compared to other operating systems like Linux and Mac OS, Windows is quite vulnerable to exploitations. Most dangerous Windows vulnerability was Win32k Elevation of Privilege Vulnerability which his discovered in Windows 10 GUI(“Top Windows 10 OS Vulnerabilities and How to Fix Them”, 2020). Windows by default shares wife credentials to contacts of Facebook and other social networking platforms. If any of those contacts in within close vicinity of the user, he or she can easily get access to Wi-Fi connection.

Another common vulnerability is Microsoft Font Driver Vulnerability which arises because if Fonts not being displayed properly which requires remote code execution over the machine. Hence the machine becomes vulnerable to attacks. Microsoft Edge Vulnerabilities are another common vulnerabilities that are present in any system that has a windows OS installed. Since Windows browser has never been secure, there are still vulnerabilities after it has evolved from Internet Explorer to Edge. Vulnerabilities like remote code execution enable hacktivists to gain control over the device and browser system. Other common vulnerabilities include .NET Framework Escalation of Privilege Vulnerability, Redirect to SMB Vulnerability, Internet Explorer Vulnerabilities, Microsoft Graphics Component Vulnerabilities, Microsoft Windows Journal Vulnerability, Mount Manager Vulnerability and many others.

## Default Application Vulnerabilities

One of The vulnerability we mentioned above, Microsoft Edge Vulnerabilities also falls under this category since Edge comes as a default application in Windows. Since there is too much research going on in the field of security, researchers have highlighted that there are severe flaws in native iOS Mail app for the iPhone. This makes the phone vulnerable to attack. Since iOS Mail app is native to iPhone, this vulnerably is built in into the iPhone.

## Protocol Vulnerabilities

In networking, protocols are used for communicating between different layers. TCP/IP vulnerabilities are very common for network professionals. IP Spoofing is one attack that leads to network exploitation via Protocols. In this attack, the hacktivists get unauthorized access of a computer system on the network. Another attack of TCP/IP is SYN Flooding. In this attack, the basic vulnerability of TCP/IP is exploited. The attacker is able to send a sequence of SYN requests to the destination server.

There are other protocols vulnerabilities like the SMTP vulnerability with a SMTP hack; the attacker can gain unauthorized access on the email server. In addition to this there are many vulnerabilities HTTP (Hyper Text Transfer Protocol) like SQL injection vulnerability and cross site scripting in which malicious code is injected usually in a scripting language like javascript which is executed as the website loads on the client side.

## Older Version Vulnerabilities
By older version vulnerabilities, we mean, vulnerabilities in unpatched OS versions. Windows and other operating systems have to be patched for security vulnerabilities to keep the system security up to date. Many softwares and operating system are vulnerable to attacks if their older versions are used. For example Mozilla Firefox older versions are vulnerable to XSS attacks, javascript clipboard access, Buffer overflow when displaying VCard and many others.
PHP is a scripting language that runs at the server. Much vulnerability has been discovered in older versions which were then patched and new versions were introduced. Vulnerabilities like out-of-bounds read for crafted JPEG data, Reflected XSS on the PHAR 403 and 404 error pages, stack-based buffer overflow and application crash that leads to a denial of service attack and many others. Older Windows versions also have vulnerabilities like Blue Keep vulnerability, Oracle Web Logic Server vulnerability and Adobe Flash Player vulnerability.

## Popular Application Vulnerabilities
Many popular applications like Office 365 are also vulnerable to attacks. Microsoft Office 365 is a leading application in the software market. A few vulnerabilities were discovered in the application like the Microsoft Office Spoofing Vulnerability. In this vulnerability, the attacker could perform spoofing and read or writer into a document without the consent or knowledge of the user. In vulnerability, Microsoft Office Access Connectivity Engine Remote Code Execution Vulnerability, the attacker could execute a code remotely into the system and thus memory objects could be altered or destroyed. In Microsoft Excel Remote Code Execution Vulnerability, the same vulnerability explained previously for Access is there for Excel; hence Exec Code overflow is the type of this vulnerability.

### Zoom app vulnerabilities: 

Zoom app is a very popular video conferencing app. There are many discovered vulnerabilities of this software. For example the Exec Code vulnerability in which a remote attacker can execute malicious code on macOS. Vulnerability is when an attacker can force a user to join a meeting while the camera active. The machine on which the app was installed remains vulnerable even after the app is uninstalled(“Zoom : Security Vulnerabilities”, n.d.).

## Skype app vulnerabilities: 

Skype is collaboration software widely used in business industry. There are much vulnerability like stack buffer overflow vulnerability in Microsoft Skype 7.2, 7.35, Exec Code vulnerability and many others(“Microsoft Skype : Security Vulnerabilities”, n.d).

### Protection Strategies for the Above Vulnerabilities
Now we discuss a few protection strategies for the vulnerabilities he latest Windows 10 must be installed with the latest patch. To stay protected from Web based attacks, it is important to disable javascript. For protection from network protocol vulnerabilities, the network admin must deploy Intrusion prevention Systems and Intrusion detection systems for effective security.
For Microsoft Office 365 security, it is advised to setup multi-factor authentication, make use of dedicated admin accounts, protect email from phishing attacks, take proper protection against ransomware attack and raise level of 
protection against malware. For Zoom related vulnerabilities, it is important to adopt best practices like disable guest screen sharing, keep credentials safe, ensure the use of waiting rooms [@Aten , 2020] (Aten, 2020).

## Conclusion
Vulnerability management is a very important aspect of security management. For many years pen testers have been keen in discovering vulnerabilities in systems before an attacker does. It is hence important to know the vulnerabilities of every system under use. In this document, we have discussed vulnerabilities from various aspects like Common Operating system vulnerabilities, vulnerabilities of older systems, network protocol vulnerabilities and Popular Application Vulnerabilities like Office 365 and Zoom. Protection strategies against vulnerabilities and best practices from security perspectives are also mentioned. It is nevertheless, necessary to keep user credentials safe, the antivirus and operating system updated and adopts state of the art security practices.


## References
[Top Windows 10 OS Vulnerabilities and How to Fix Them(Guidelines)](https://antivirus.comodo.com/blog/computer-safety/fix-top-10-windows-vulnerabilities/)    

[PHP: Security Vulnerabilities](https://www.cvedetails.com/vulnerability-list/vendor_id-74/product_id-128/PHP-PHP.html)  

[Wordpress : Security Vulnerabilities](https://www.cvedetails.com/vulnerability-list/vendor_id-2337/product_id-4096/)    

[A Quick Look at Some Old and New Security Vulnerabilities Which Need to be Patched Before 2020:](https://cyware.com/news/a-quick-look-at-some-old-and-new-security-vulnerabilities-which-need-to-be-patched-before-2020-8152ed02)    

[Microsoft Office 365 : Security Vulnerabilities](https://www.cvedetails.com/vulnerability-list/vendor_id-26/product_id-51636/Microsoft-Office-365.html)  

[Zoom : Security Vulnerabilities](https://www.cvedetails.com/vulnerability-list/vendor_id-2159/Zoom.html)  

[Microsoft Skype : Security Vulnerabilities](https://www.cvedetails.com/vulnerability-list/vendor_id-26/product_id-35646/Microsoft-Skype.html)  

[5 Ways to Protect Your Zoom Meetings From Hackers.](https://www.inc.com/jason-aten/hackers-are-trying-to-get-into-your-zoom-meetings-here-are-5-ways-to-stop-them.html)   
>**[Note]** Remember to use markdown syntax to organize information in useful ways.
