# Nmap

[home](../README.md)
- [Example](#Example)

## Incident Overview  

Nmap is a free and open-source network scanner that is used to discover hosts and services on a network by sending packets and analyzing the responses. It provides a number of features for probing computer networks, including host discovery and service and operating system detection.


### Installing Nmap

#### Linux

Some distributions include Nmap by default. Check by running the following command:

 ```
 nmap --version
 ```

To install Nmap on Debian Linux and derivatives use:

```
sudo apt-get install nmap
```

#### Windows

Download and run the **Latest __stable__ release self-installer** for Windows from the
[Nmap download page](https://nmap.org/download.html).

This will also install the Zenmap GUI. You can use this if you prefer a graphical frontend over a command window.

#### Mac OS

Download the **Latest stable release installer** for Mac OS from the
[Nmap download page](https://nmap.org/download.html).

1. Once you have downloaded the file nmap-\<version>\.dmg, double-click the icon to open it.

2. The contents of the disk image will be displayed. One of the files will be a Mac meta-package file named nmap-<version>.mpkg. Open it to start the installer.

> If the .mpkg file cannot be opened you will need to right-click or control-click on the .mpkg and select “Open”. When a new dialog pops up click "Open".

3. Follow the instructions in the installer. You will be asked for your password since Nmap installs in a system directory.

4. Once the installer is finished, eject the disk image by control-clicking on its icon and selecting “Eject”. The disk image may now be placed in the trash.


You will now be able to type your commands in a terminal window.

By default the root user is disabled on Mac OS X. To run a scan with root privileges prefix the command name with sudo, as in sudo nmap -sS <target>. You will be asked for a password, which is just your normal login password. Only users with administrator privileges can do this.


### Using Nmap (scattered/unfinished)

#### Host Discovery
Network scans usually begin by discovering which targets on the network are online and thus worth deeper investigation. This process is called host discovery or ping scanning.

1.	Fast mode: ```nmap -F```
>Scan fewer ports to reduce time for large scans

2.	TCP SYN scan / half-open scan: ```nmap -sS```
>This technique is often referred to as "half-open" scanning, because you don’t open a full TCP connection.The primary advantage to this scanning technique is that fewer sites will log it. You need root privileges to build these custom SYN packets. This is the default scan type for privileged users.

3.	TCP connect() scan: ```nmap -sT```
>This is the most basic form of TCP scanning. One strong advantage to this technique is that you don’t need any special privileges.
This sort of scan is easily detectable as target host logs will show a bunch of connection and error messages for the services which accept() the connection just to have it immediately shut- down. This is the default scan type for unprivileged users.



#### Port Scanning
Network ports are the communication endpoints for a machine that is connected to the Internet. When a service listens on a port it can receive data from a client application, process it and communicate a response. Port scanning allows you to find all network entry points available on a target system.

#####  Common TCP Ports

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

##### Port Scanning Commands

1.	Service Versions: ```nmap -sV```
>Probe open ports to determine service/version info
