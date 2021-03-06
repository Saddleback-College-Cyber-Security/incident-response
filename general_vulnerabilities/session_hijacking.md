<!-- This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA. -->

# Session Hijacking & Countermeasures

[**Incident Response Home**](../README.md)
- [Abstract](#Abstract)
- [Introduction](#Introduction)
- [Active Session Hijacking 1](#Active-Session-Hijacking-1)
- [Active Session Hijacking 2](#Active-Session-Hijacking-2)
- [Passive Session Hijacking](#Passive-Session-Hijacking)
- [Cross-site scripting](#Cross-site-scripting)
- [Blind Spoofing Attack](#Blind-Spoofing-Attack)
- [Brute Force](#Brute-Force)
- [TCP/Hijacking](#TCP/Hijacking)

## Abstract

Session Hijacking by definition is when an attacker gains unauthenticated access over a valid TCP connection between two computers. Based on most authentication happening at the beginning of a TCP session, this permits an attacker to have access to a machine. An attack can uses a vulnerability scanning tools to capture all networking traffic through a TCP connection to perform Identity theft, information theft, fraud, even inject client-side scripts using Java onto pages on the web that cause a web browser to execute arbitrary code when it loads a page that is compromised page. If a server fails to set the HTTP only settings in session cookies, scripts that are injected now have entry to the session ID, this allows attackers with the necessary information for session hijacking. In this paper I have mentioned several concept pertaining to session hijacking I discuss the different types of session hijacking, proper procedures for counter measures as well as man in the middle attacks and vulnerabilities associated with session Hijacking. 

## Introduction

When it comes to cyber security, Cyber Security or information technology security guarding of computer systems as well as networks from theft or damage to hardware, software, electronic data as well as from disruption or redirection of networking traffic packets that are provided. According to a study conducted by Varonis,64% of Americans have never checked to see if they were compromised by a data Breach. Another study conducted by a Varonis found that 56% of Americas are not aware of the steps necessary to protect themselves from cyber security attacks. Only about 5% of companies are protected in business.   When it comes to Session Hijacking, there are several different topics to discuss. 

## Active Session Hijacking 1

In an active attack, the attacker takes over an existing session either by tearing down the connection on one side of the conversation or by actively participating. An example of an active attack is a man-in-the-middle (MITM) attack. In order to make this attack be successful, the attacker must guess the sequence number before the target responds to the server. On most current networks, sequence number prediction does not work because operating-system vendors use random values for the initial sequence number, which makes it harder to predict sequential numb

## Active Session Hijacking 2

In Active Session Hijacking The attackers, take control over a session that’s already in progress between the user and the server. The attacker will themselves in the place of the using by using a technique called Dos an attacker uses a packet Analyzer such as Wireshark or Nmap to capture network traffic and data. The attacker sends sometimes hundreds and sometimes even thousands of packet requests or information requests that are direct at a target network to make the server overload and eventually shut down. The Server will sometimes pause before it sends another request to the users system to connect ,spoof and authentic as a legitimate user and send conformation to the server and attacker to a create a connection with a legitimate user. 

## Passive Session Hijacking

In a Passive Hijacking Session an attack takes control of a session but overwatches and records all of the incoming and outgoing traffic. When a passive Hijacker uses a packet analyzer to view vulnerabilities on a network an attacker can use a packet sniffer to scan the network that will allow the attackers to locate data like Session user IDs and passwords.  The attacker is able to later use the information to log on as a legitimate user with all of the same benefits as a regular user. You can use a password sniffer such a John the Ripper to have direct network access. There is one big disadvantage for the attacker, he or she only has access to the  the information from the user and the server as long as the  between user and server until and unless a session is active, in the circumstance that user logs out or there is a reset on the server with the connection for any chance the attacker won’t be able to view the packet information or the session and will be immediately removed from the session permanently.  

## Cross-site scripting

Cross Site scripting(XSS)  is a common way to steal session IDs.  This XSS also called client side code injection attack, this code has a capability to initiate the mischievous script onto a website or application on the web. In this attack, vulnerabilities on the websites and any user information that is put into the website displays it as un-encrypted or unencoded and delivers the data to an attacker in normal text.. .  A website that creates dynamic page has no control over how their output is read by clients. Which gives the attackers the ability to input mischievous code such as Javascript,VBScript,ActiveX, HTML or Flash applet on a vulnerable dynamic page. When a page initiates a script on a users computer It also is able to capture critical data from a user, acquire cookies, reroute users to unknown pages.  To excute this an attacker will send a crafted link to the victim containing mischievous JavaScript. (similar to phishing email) the user will click on the link the JavaScript runs automatically and performs the instructions set by the attacker. The result shows the active session ID of the user. Using the exact same technique, an attacker can design a particular Javascript that captures him or hers the user’s session ID.  one of the mains cons for the attacker is that for the attack to work on a vulnerable target but nowadays many websites have been patched with these security issues.

## Blind Spoofing Attack

Blind Spoofing is when an attacker seeks a target system with out making modifications in the connection from the server and the users system. All the attacker has to do is capture the network traffic from the user and the server to figure out the TCP sequence number in order to get authentication for the server to gain full access to the networking session. The hard part of this attack is that it can be very challenging to search or try to guess the number for a TCP sequence from network traffic that was captured, because the TCP sequence number changes every time it creates a fresh and random TCP sequence number this make it almost impossible to figure out the right sequence number it needs long period to search and if the attacker is to continue to capture the networking traffic to analyze for the TCP sequence. In order to figure the correct sequence number, it could take a long time, or the attack must be patience in this type of attack.  

## Brute Force

Brute Force Attack is designed to crack any password, character number or symbol as well as specific characters bringing together a username and password. When an attacker is using Brute Force the attack will more than likely use more time to ensure their work is done properly. With a Brute Attack an attack could set a series of the character. Special character,symbols and number based on their requirement an attacker can create the number of words. To do this lets say a user has an password that is 8 characters. The attacker will guess the passwords length till the characters match to create the proper combination of characters that are created by the attacker until the 8th digit. With these types of attacks, an attacker must take their time. In order for the brute force attack to be efficient the attacker must look at every combinations that are set by the user to gain access to the session ID and find the right session ID so that the attacker can gain control on a session that was already authenticated. 

## TCP/Hijacking

In  TCP/IP Hijacking an attacker seizes a connection with the user and server using packets that are spoofed than precedes like it is one of the users. By using this attack the attacker has packets that are spoofed and rerouted to TCP Traffic on the attackers system. For this to occur, the connection of the victims connection is visible and the attack can send packets to the host system on the victims behalf. In order for the hijacking attack to be initiated by the attacker and the victim systems can be traced anywhere in the world. With this method an attack can easily take control over the system, which uses one-time passwords. To launch a TCP/IP hijacking attack, both victim and attacker must be on the same network. The target and the victim machines can be located anywhere. Using this technique, an attacker can easily attack the system, which uses one-time passwords. 
