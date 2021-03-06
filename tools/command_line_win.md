<!-- This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA. -->

# Windows Command Line Tools

[**Incident Response Home**](../README.md)
- [Incident Overview](#Incident-Overview)
- [Programs](#Programs)
- [Forms of Attack](#Forms-of-Attack)
- [Useful Commands](#Useful-Commands)
	- [Find IP Address of a Site​](#Find-IP-Address-of-a-Site​)
	- [Show Route Path to Site​](#Show-Route-Path-to-Site​)
	- [Show the ARP table​](#Show-the-ARP-table​)
	- [See IP, gateway, DNS and other info​](#See-IP,-gateway,-DNS-and-other-info​)
	- [See connection status](#See-connection-status)

## Incident Overview

Windows command line tools are a comparably simple vector for cybersecurity attacks in an era of advanced cryptography, sophisticated cracking tools, DNS tunneling, and dozens more, and yet they are no less dangerous. It is not hard to see why: Windows Powershell, a ubiquitous program and command terminal that comes factory default with any Windows OS today, is often utilized for running high-level administrative tasks in an automated fashion through the use of scripts. Were an attacker to gain access to that terminal, then, they would have most of the resources on the network at their disposal.

There’s numerous other forms of command line tools and attacks, but they generally share one major function as far as attackers are concerned: they allow attackers to proxy execute code through a program that security systems will have whitelisted. ```regsvr32.exe``` is one other such popular tool, which can execute code like Powershell but can also link a computer to a file on the internet via a URL embedded in a DLL used by the program. This is referred to as a “Squiblydoo” attack and has been used against government computers in the past, having been a supremely reliable method before advancements in cybersecurity monitoring and patches were made.

## Programs

- Command Prompt
- Windows Powershell
- Powershell ISE
- Powershell Empire
- Regsvr32.exe

## Forms of Attack

- Command Injection: a vulnerable application passes unsafe user data with improper input validation, and an attacker abuses this functionality to pass commands to the OS.

- COM Scriptlets: malicious code embedded in scripts/modules used by ```regsvr32.exe```, bypassing security software that does not block actions from it (due to being a standard Windows process)

- Squiblydoo (passing URLS): ```regsvr32.exe``` can load a network-aware script containing a URL to malicious code, making no change in the registry as the code is executed without being “saved”.

## Useful Commands

### Find IP Address of a Site​

```cmd
> ping [URL]
```

### Show Route Path to Site​

```cmd
> tracert [URL]
```

### Show the ARP table​

```cmd
> arp -a
```

### See IP, gateway, DNS and other info​

```cmd
> ipconfig /all
```

### See connection status

The netstat command is used to display all open network connections and listening ports.
```
C:\WINDOWS\system32>netstat -an
```
