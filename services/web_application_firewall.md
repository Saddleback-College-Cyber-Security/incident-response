# Web Application Firewall

[**Incident Response Home**](../README.md)
- [Overview of WAF](#overview-of-waf)
- [Common Business Usecases](#common-business-usecases)
- [Common Tasks Performed](#common-tasks-performed-eg-setup-configuration-etc)
- [How to Find Instance of WAF Running on System](#how-to-find-an-instance-of-a-waf-running-on-a-system)
	- [Linux](#Linux)
- [Common vulnerabilities and how to protect against them](#common-vulnerabilities-and-how-to-protect-against-them)
- [Strategies for maintenance](#strategies-for-maintenance-eg-how-to-notice-malicious-activity-protect-against-attackers-etc)
- [List of Web Application Firewalls](#list-of-web-application-firewalls)

## Overview of WAF

A web application firewall (WAF) filters, monitors, and blocks HTTP traffic to and from a web application.

A WAF is differentiated from a regular firewall in that a WAF is able to filter the content of specific web applications while regular firewalls serve as a safety gate between servers.

## Common Business Usecases

Web application firewalls help to protect company websites and any web applications/services that are run via their websites/web servers. If the websites involve interaction with customers and their information (e.g. financial or e-commerce websites), a WAF can help protect the customers information against theft or manipulation. They do this by filtering and monitoring all the traffic between each web application and the Internet and can screen/block harmful traffic. This helps to protect against certain types of web application attacks like cross-site scripting (XSS) and Injection attacks (SQL, Command, LDAP, File etc). A WAF can also be useful in health orgranizations and may help the company keep in compliance with HIPPA or PCI-DSS regulations. They can also help prevent DDoS attacks and act as a real-time IDS.

## Common Tasks Performed (e.g. setup, configuration, etc.)

Setup:
>note: this was largely based of the Baraccuda WAF installation, others might differ)

1) Depending on the needs/type of business or organization, you can choose different deployment methods and placements. Some common placements are between the business/org and the service or in between the application/service and other services. 
2) Prepare for the installation. This includes hardware setup, any necessary network changes like opening network ranges, software changes, etc.
3) Install firewall and activate the subscription status if needed
4) Update the firmware and any definitions  

Configuration:

1) Choose the type of WAF model best suited for your setup. There are 3 main ones:
	- Whitelist model (Allows traffic that meet certain criteria)
	- Blacklist model (Blocks malicious or suspiscious traffic based on pre-defined signatures)
	- Hybrid model (A combination of Whitelist and Blacklist models)
2) Based on the model, configure and customize the firewall policies and preferences of the WAF
	- Includes how it validates HTTPS and FTPS, configuring log levels, trusted host actions, different modes, etc.

## How to find an instance of a WAF running on a system

>Note differences in OS (e.g. Windows, macOS, Linux)

### Linux

In Linux you can use various fingerprinting techniques do detect a WAF. These include:
1) Fingerprinting with Telnet - This method might be able to reveal server infomation and cookies.

	```shell
	$ telnet yoursite.com 80
	GET/HTTP/1.1
	```

2) Fingerprinting with NMap - detect WAF

	```shell
	$ nmap -script=http-waf-fingerprint yoursite.com
	$ nmap -p80 --script http-waf-detect <your site host>
	```

3) Other tools that automatically detect WAF such as Wafw00f

	```shell
	$ wafw00f yoursite.com
	```

>Note differences in privilage requirement (e.g. whether ```sudo``` is needed on Linux)

## Common vulnerabilities and how to protect against them

## Strategies for maintenance (e.g. how to notice malicious activity, protect against attackers etc.)

## List of Web Application Firewalls
*In no particular order and not exhaustive*
1) dotDefender
2) Barracuda Web Application Firewall
3) Nginx 
4) AWS WAF
5) Cloudflare WAF
6) ModSecurity
7) Sucuri
8) Alert Logic
9) ThreadSentry
10) IBM Security AppScan
11) QualysGuard WAF
12) Citrix WAF
13) Reblaze
14) AppSecure
15) Templarbit Shield
16) AppWall by Radware
17) Imperva WAF

## Sources

EC-Council. Certified Ethical Hacker (CEH) Version 10 eBook w/ iLabs (Volumes 1 through 4).. [eVantage].
https://sucuri.net/guides/what-is-a-waf/
https://www.webarxsecurity.com/bypassing-modern-web-application-firewall/
