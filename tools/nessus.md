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

>**[Note]** A free version of Nessus can be obtained using a student email address from the Tenable website.


### Installation from command prompt on Linux

Red Hat version 6
```
# rpm -ivh Nessus-<version number>-es6.x86_64.rpm
# .etc/init.d/nessusd start
```
Debian version 6
```
# dpkg -i Nessus-<version number>-debian6_amd64.deb
# .etc/init.d/nessusd start
```
FreeBSD version 10
```
# pkg add Nessus-<version number>-fbsd10-amd64.txz
# .etc/init.d/nessusd start
```   
>**[Note]** Perform the remaining **Nessus installation steps** in your web browser.


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


### Nessus installation steps

1. In **Browser** open:
```
https://user:port/#/
```
2. Choose **Nessus Essentials**.
3. Press **Skip**.
4. Write your *Activation Code*.
>**[Note]** A free version of Nessus can be obtained using a student email address from the Tenable website.

5. Press **Continue**.
6. Login to your account.


## Nessus scan setup

>**[Note]** Head to the **+ New Scan** button on the top right corner of *My Scans*.


### Advanced Scan

>**[Note]** It includes all the other available scans inside it, and it is usually the best one to use.

>**[Note]** It takes more time to complete this scan.


#### Settings Tab


##### Basic


###### General

1. **Name*** - your choice.
2. **Targets*** - include all the ip addresses that you want to perform a scan on.


###### Schedule

Lets you set a schedule when to perform this scan again.


###### Notifications

Lets you choose **Email Recipient(s)** to receive new *Scan Results*.


##### Discovery


###### Host Discovery

Allows you to choose if you want to **Ping the Remote Host**.


###### Port Scanning

Lets you select **Port scan range**.

Local Host Enumerators:
- **SSH (netstat)**.
- **WMI (netstat)**.
- **SNMP**.
- **Only run network port scanners if local port enumeration failed**.
- Verify open TCP ports found by local port enumerators.


###### Port Scanning
- **SYN**.
    - Override automatic detection
        - Use soft detection (*recommended*)
        - Use aggressive detection (*makes scan slower*)
- **UDP**.


###### Service Discovery

>**[Note]** Recommended to leave default values.


##### Assessment


###### General

1. Set **Override normal accuracy** and check **Avoid potential false alarms**.
2. **SMTP** lets you choose your own *3rd party domain*.

###### Malware

Turn on **Scan for malware**.


##### Advanced

Turn on **Enable safe checks**.


#### Compliance

Has a set of presets for different compliances of the scan.


#### Plugins

Recommended to turn on all the plugins for the best result.


## Nessus Scanner Templates Chart

### Vulnerability Scans (Common)

| Template                    | Description                                                                                                                                                                                                                                                                                                                                                     |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Advanced  Network  Scan     | A scan without any recommendations, so that you can fully customize the scan settings.                                                                                                                                                                                                                                                                          |
| Basic Network Scan          | Performs a full system scan that is suitable for any host. For example, you could use this template  to perform an internal vulnerability scan on your organization's systems.                                                                                                                                                                                  |
| Credentialed Patch Audit    | Authenticates hosts and enumerates missing updates.                                                                                                                                                                                                                                                                                                             |
| Host Discovery              | Performs a simple scan to discover live hosts and open ports.                                                                                                                                                                                                                                                                                                   |
| Internal PCI Network Scan   | Performs an internal PCI DSS (11.2.1) vulnerability scan.                                                                                                                                                                                                                                                                                                       |
| Legacy Web App Scan         | Uses a Nessus scanner to scan your web applications. **[Note]**   Unlike the  Tenable.io Web Application Scanning   scanner, the Nessus scanner does not use a browser to scan your web applications. Therefore, a  **Legacy Web App Scan**  is not as comprehensive as a  **Web App Scan**. For more information, see the  Tenable.io   Web Application Scanning User Guide. |
| Mobile Device Scan          | Assesses mobile devices via Microsoft Exchange or an MDM.                                                                                                                                                                                                                                                                                                       |
| PCI Quarterly External Scan | Performs quarterly external scans as required by PCI. **[Note]**     Because the nature of a PCI ASV scan is more paranoid and may lead to false positives, the scan data is not included in the aggregate   Tenable.io   data. This is by design.


### Configuration Scans

| Template                   | Description                                             |
|----------------------------|---------------------------------------------------------|
| Audit Cloud Infrastructure | Audits the configuration of third-party cloud services. |
| MDM Config Audit           | Audits the configuration of mobile device managers.     |
| Offline Config Audit       | Audits the configuration of network devices.            |
| Policy Compliance Auditing | Audits system configurations against a known baseline.  |
| SCAP and OVAL Auditing     | Audits systems using SCAP and OVAL definitions.         |


### Tactical Scans

| Template                           | Description                                                                           |
|------------------------------------|---------------------------------------------------------------------------------------|
| Badlock Detection                  | Performs remote and local checks for CVE-2016-2118 and CVE-2016-0128.                 |
| Bash Shellshock Detection          | Performs remote and local checks for CVE-2014-6271 and CVE-2014-7169.                 |
| DROWN Detection                    | Performs remote checks for CVE-2016-0800.                                             |
| Intel AMT Security BypassDetection | Performs remote and local checks for CVE-2017-5689.                                   |
| Malware Scan                       | Scans for malware on Windows and Unix systems.                                        |
| Shadow Brokers Scan                | Scans for vulnerabilities disclosed in the Shadow Brokers leaks.                      |
| Spectre and Meltdown               | Performs remote and local checks for CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754. |
| WannaCry Ransomware                | Scans for the WannaCry ransomware.                                                    |


### Tenable-Provided Agent Templates

| Template                                                                                                                                                       | Description                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Advanced Agent Scan **[Note]** When you create an agent scan using the Advanced Agent Scan template, you must also select the plugins you want to use for the scan. | Scans without any recommendations.                                                                                                                                                                                                                 |
| Basic Agent Scan                                                                                                                                               | Scans systems connected via Nessus Agents.                                                                                                                                                                                                         |
| Custom Agent Scan                                                                                                                                              | Scans using a previously defined template.                                                                                                                                                                                                         |
| Malware Scan                                                                                                                                                   | Scans for malware on systems connected via Nessus Agents. **[Note]** See the Application, Malware, and Content Audits videoand the Application, Malicious Software, and Content Audits video for more information about scanning for malware in Nessus. |
| Policy Compliance Auditing                                                                                                                                     | Audits systems connected via Nessus Agents.                                                                                                                                                                                                        |
| SCAP and OVAL Agent Auditing                                                                                                                                   | Audits systems using SCAP and OVAL definitions.                                                                                                                                                                                                    |


## Nessus Scan Start

In *My Scans* press on **Launch** button


## Exporting of Scan Results

1. Open Scan Result
2. Press on **Export** drop down menu.
3. Export as **HTML file** or **pdf**, depends on the situation, usually HTML variant is a better solution.


## Create a New Report


1. On the top navigation bar, click **Reports**.

    The **Reports** page appears.

2. In the upper right corner, click the **New Report** button.

    The **Report Templates** section appears, displaying a list of the available report templates.

3. Select a template from the list.

    The **New Report** section appears, displaying the **General** settings.

4. Configure the **General settings**:

    - In the **Targets** box, select a target for the report. By default, the **Target** box is set to **All Assets**.
    - *(Optional)* Set the **Encrypt PDF** option to **On** and specify a password for the PDF.
    - *(Optional)* In the **Name** box, specify a name for the report.
    - *(Optional)* In the **Description** box, modify or replace the default report description.
    - *(Optional)* In the **Email** box, enter the email addresses for report recipients.

5. *(Optional)* Configure the **Schedule settings**:

    - In the **Settings** section, under **BASIC**, click **Schedule**.

    The Schedule settings appear.

    - Set **Enabled** to **On**, and then specify the desired frequency, start time and date, and timezone.

6. *(Optional)* Configure the **Permissions settings**:

    >**[Note]** If you do not configure the Permissions settings, only you and users with administrator accounts will have access to the report and its results.

In the Settings section, under BASIC, click Permissions.

The Permissions settings appear.

Permissions settings

In the Add users or groups box, type the name of the user or group that you want to give permissions for the report.

The specified user or group appears in a row at the bottom of the User Sharing section.

In the row corresponding to the user or group that you added, in the drop-down box, select a permission.

(Optional) In the Settings section, under BASIC, click Chapters and then review the structure of the results that will be created by the report. This structure cannot be modified.
At the bottom of the Reports page, click the Save button.

The new report appears in the list in the My Reports folder.


## Sources:

- https://www.tenable.com/downloads/nessus
- https://docs.tenable.com/nessus/Content/InstallNessusLinux.htm
- https://docs.tenable.com/nessus/Content/InstallNessusWindows.htm
- https://docs.tenable.com/tenableio/vulnerabilitymanagement/Content/Scans/ScannerTemplates.htm

>**[Note]** Remember to use markdown syntax to organize information in useful ways.
