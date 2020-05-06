# Nmap

[home](../README.md)
- [Installing Nmap](#Installing-Nmap)
	- [Linux](#Linux)
	- [Windows](#Windows)
	- [MacOS](#MacOS)
- [Usage](#Usage)
- [Common Options](#Common-Options)
	- [Target Specification](#Target-Specification)
	- [Host Discovery](#Host-Discovery)
	- [Scan Techniques](#Scan-Techniques)
	- [Port Specification and Scan Order](#Port-Specification-and-Scan-Order)
	- [Service Version Detection](#Service-Version-Detection)
	- [Script Scan](#Script-Scan)
	- [OS Detection](#OS-Detection)
	- [Misc.](#Misc.)
	- [Common Ports](#Common-Ports)

## About

Nmap is a free and open-source network scanner that is used to discover hosts and services on a network by sending packets and analyzing the responses. It provides a number of features for probing computer networks, including host discovery and service and operating system detection.

## Installing Nmap

### Linux

To install Nmap, check [Installing And Managing Packages](./command_line_nix.md#Installing-And-Managing-Packages) on *nix systems
>Some distributions include Nmap by default. Check by running the following command: `nmap --version`

### Windows

Download and run the **Latest _stable_ release self-installer** for Windows from the
[Nmap download page](https://nmap.org/download.html).
>This will also install the Zenmap GUI. You can use this if you prefer a graphical frontend over a command window.

### MacOS

Download the **Latest _stable_ release self-installer** for Mac OS from the
[Nmap download page](https://nmap.org/download.html).

1. Once you have downloaded the file nmap-\<version>\.dmg, double-click the icon to open it.
2. The contents of the disk image will be displayed. One of the files will be a Mac meta-package file named nmap-<version>.mpkg. Open it to start the installer.
>If the .mpkg file cannot be opened you will need to right-click or control-click on the .mpkg and select “Open”. When a new dialog pops up click "Open".
3. Follow the instructions in the installer. You will be asked for your password since Nmap installs in a system directory.
4. Once the installer is finished, eject the disk image by control-clicking on its icon and selecting “Eject”. The disk image may now be placed in the trash.

You will now be able to type your commands in a terminal window.
>By default the root user is disabled on Mac OS X. To run a scan with root privileges prefix the command name with [sudo](./command_line_nix.md##General-Commands).

## Usage


```shell
$ nmap [OPTIONS] <HOST> #Scan HOST (HOST can be a single ip, range, subnet, or individual hosts separated with spaces)
$ namp 10.0.24.5
$ namp 10.0.24.1-6
$ namp 10.0.24.1 10.0.24.2  10.0.24.3
$ nmap 10.0.24.0/24
$ nmap 10.0.24.*
```
>With only HOST as an argument, nmap will perform the default scan based on user privileges (`-sS` for privileged users, `-sT` for unprivileged users).

## Common Options

Nmap has hunderds of valid options. Use [man](./command_line_nix.md#I-Need-Help,-Where-Can-I-Go? "man on *nix") on *nix systems for a detailed list. 
>Mixing and matching of options is allowed, however, some options do not work with each other.

### Target Specification

```shell
$ nmap -iL <FILE> #Scan hosts listed in FILE
$ nmap -iR <NUMBER> #Scan NUMBER random hosts
$ nmap <HOST(S)> --exclude <HOST2> #Exclude HOST2 from scan
```

### Host Discovery

Network scans usually begin by discovering which targets on the network are online and thus worth deeper investigation. This process is called host discovery or ping scanning.

```shell
$ nmap -sn <HOST(S)> #No port scan
$ nmap -Pn <HOST(S)> #Treat all hosts as online -- skip host discovery
```

### Scan Techniques

```shell
$ nmap -sU <PORT> <HOST> #UDP port scan
$ nmap -sS <HOST> #Stealth scan (TCP SYN)
$ nmap -sT <HOST> #Check only common ports
$ nmap -sN <HOST> #TCP NULL scan
$ nmap -sA <HOST> #TCP ACK scan
```

>`-sS` TCP SYN scanning is often referred to as "half-open" scanning, because you don’t open a full TCP connection. The primary advantage to this scanning technique is that fewer sites will log it. You need root privileges to build these custom SYN packets. This is the default scan type for privileged users.

>`-sT` is the most basic form of TCP scanning. One strong advantage to this technique is that you don’t need any special privileges. This sort of scan is easily detectable as target host logs will show a bunch of connection and error messages for the services which accept() the connection just to have it immediately shut- down. This is the default scan type for unprivileged users.

### Port Specification and Scan Order

Network ports are the communication endpoints for a machine that is connected to the Internet. When a service listens on a port it can receive data from a client application, process it and communicate a response. Port scanning allows you to find all network entry points available on a target system.

```shell
$ nmap -p <PORT(S)> <HOST> #Scan specific PORT(S) (PORT can be a single port, range, or individual ports separated with spaces) defaults to TCP
$ nmap -F <HOST> #Fast scan (scans fewer ports to reduce time for large scans)
```

### Service Version Detection

```shell
$ nmap -sV <HOST> #Find HOST's service versions
```

### Script Scan

```shell
$ locate *.nse #Show all nmap scripts available
$ nmap --script=<NAME>
```

### OS Detection

```shell
$ nmap -O <HOST> #OS detection
```

### Misc.

```shell
$ nmap -A <HOST> #Enable OS detection, version detection, script scanning, and traceroute
```

### Common Ports
>(MOVE THIS TO THE NETWORKING PAGE)
- 21 - FTP (File Transfer Protocol)
- 22 - SSH (Secure Shell)
- 23 - Telnet
- 25 - SMTP (Mail)
- 80 - HTTP (Web)
- 110 - POP3 (Mail)
- 143 - IMAP (Mail)
- 443 - HTTPS (Secure Web)
- 445 - SMB (Microsoft File Sharing)
- 3389 - RDP (Remote Desktop Protocol)
