# Nessus

[home](../README.md)
- [Example](#Example)

## Incident Overview

Nessus, a vulnerability detection software, is one of the tools which our teams will be using to find vulnerabilities in our systems.  

Research and provide information on the following concepts:

- Process for installing Nessus
- Configuration settings for making user scans and policies
- Running different kinds of scans
    - Quick Scan
    - Full Scan
    - etc. (look into other scans that may be useful to know)

## Installation

### Installation from browser
Nessus has [downloader](https://www.tenable.com/downloads/nessus) on their website for most of the popular operating systems.
### Installation from command prompt on Linux
Red Hat version 6
```
# rpm -ivh Nessus-<version number>-es6.x86_64.rpm
```
Debian version 6
```
# dpkg -i Nessus-<version number>-debian6_amd64.deb
```
FreeBSD version 10
```
# pkg add Nessus-<version number>-fbsd10-amd64.txz
```   
### Installation on Windows
#### Download Nessus Package File

>**[Note]** For details, refer to the **Installation from browser**.

#### Start Nessus Installation

1. Navigate to the folder where you downloaded the Nessus installer.
2. Next, double-click the file name to start the installation process.

#### Complete the Windows InstallShield Wizard.

1. First, the **Welcome to the InstallShield Wizard for Tenable, Inc. Nessus** screen appears. Select **Next** to continue.
2. On the **License Agreement** screen, read the terms of the Tenable, Inc. Nessus software license and subscription agreement.
3. Select the **I accept the terms of the license agreement** option, and then click **Next**.
4. On the **Destination Folder** screen, select the **Next** button to accept the default installation folder. Otherwise, select the **Change** button to install Nessus to a different folder.
5. On the **Ready to Install the Program** screen, select the **Install** button.

    The **Installing Tenable, Inc. Nessus** screen will be displayed and a **Status** indication bar will illustrate the installation progress. The process may take several minutes.

##### If presented, Install WinPcap

As part of the Nessus installation process, WinPcap needs to be installed. If WinPcap was previously installed as part of another network application, the following steps will not appear, and you will continue with the installation of Nessus.

1. On the **Welcome to the WinPcap Setup Wizard** screen, select the **Next** button.
2. On the **WinPcap License Agreement screen**, read the terms of the license agreement, and then select the **I Agree** button to continue.
3. On the **WinPcap Installation options** screen, ensure that the **Automatically start the WinPcap driver at boot time** option is checked, and then select the **Install** button.
4. On the **Completing the WinPcap Setup Wizard** screen, select the **Finish** button.
The **Tenable Nessus InstallShield Wizard Completed** screen appears.
5. Select the **Finish** button.

    After the **InstallShield Wizard** completes, the **Welcome to Nessus** page loads in your default browser.
>**[Note]** Perform the remaining **Nessus installation steps** in your web browser.



>**[Note]** A free version of Nessus can be obtained using a student email address from the Tenable website.





## Sources:

- https://www.tenable.com/downloads/nessus
- https://docs.tenable.com/nessus/Content/InstallNessusLinux.htm
- https://docs.tenable.com/nessus/Content/InstallNessusWindows.htm

>**[Note]** Remember to use markdown syntax to organize information in useful ways.
