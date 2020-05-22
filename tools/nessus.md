# Nessus

TODO: Clean up markdown formatting

[**Incident Response Home**](../README.md)

- [Incident Overview](#Incident-Overview)
- [Installation](#Installation)
	- [Installation from browser](#Installation-from-browser)
	- [Installation from command prompt on Linux](#Installation-from-command-prompt-on-Linux)
	- [Installation on Windows](#Installation-on-Windows)
		- [Download Nessus Package File](#Download-Nessus-Package-File)
		- [Start Nessus Installation](#Start-Nessus-Installation)
		- [Complete the Windows InstallShield Wizard.](#Complete-the-Windows-InstallShield-Wizard.)
			- [If presented, Install WinPcap](#If-presented,-Install-WinPcap)
	- [Nessus installation steps](#Nessus-installation-steps)
- [Nessus scan setup](#Nessus-scan-setup)
	- [Advanced Scan](#Advanced-Scan)
		- [Settings Tab](#Settings-Tab)
			- [Basic](#Basic)
				- [General](#General)
				- [Schedule](#Schedule)
				- [Notifications](#Notifications)
			- [Discovery](#Discovery)
				- [Host Discovery](#Host-Discovery)
				- [Port Scanning](#Port-Scanning)
				- [Port Scanning](#Port-Scanning)
				- [Service Discovery](#Service-Discovery)
			- [Assessment](#Assessment)
				- [General](#General)
				- [Malware](#Malware)
			- [Advanced](#Advanced)
		- [Compliance](#Compliance)
		- [Plugins](#Plugins)
- [Nessus Scanner Templates Chart](#Nessus-Scanner-Templates-Chart)
	- [Vulnerability Scans (Common)](#Vulnerability-Scans-(Common))
	- [Configuration Scans](#Configuration-Scans)
	- [Tactical Scans](#Tactical-Scans)
	- [Tenable-Provided Agent Templates](#Tenable-Provided-Agent-Templates)
- [Nessus Scan Start](#Nessus-Scan-Start)
- [Exporting of Scan Results](#Exporting-of-Scan-Results)
- [Create a New Report](#Create-a-New-Report)
	- [Run a Report](#Run-a-Report)
	- [Report Templates](#Report-Templates)
- [Sources](#Sources)

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

	>**[Note]** If you do not configure the **Permissions** settings, only you and users with administrator accounts will have access to the report and its results.

	- In the **Settings** section, under **BASIC**, click **Permissions**.

	The Permissions settings appear.

	- In the **Add users or groups** box, type the name of the user or group that you want to give permissions for the report.

	The specified user or group appears in a row at the bottom of the **User Sharing** section.

	- In the row corresponding to the user or group that you added, in the drop-down box, select a permission.

7. *(Optional)* In the **Settings** section, under **BASIC**, click **Chapters** and then review the structure of the results that will be created by the report. This structure cannot be modified.

8. At the bottom of the **Reports** page, click the **Save** button.

	The new report appears in the list in the **My Reports** folder.


### Run a Report

1. In the top navigation bar, click **Reports**.

	The **Reports** page appears.

2. In the row corresponding to the report that you want to run, click the **Launch button** button.

	In that row, the **Running icon** image appears, indicating that the report is running.


### Report Templates

| Report Template                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CVE Analysis Report                             | In the early days of the internet, vulnerabilities were not publicly known or identifiable. In 1999, the information security industry endorsed the importance of using a common format in identifying vulnerabilities, and thus the Common Vulnerabilities and Exposures (CVE®) was created. Since 1999, the adoption of CVE has grown from 29 organizations to over 150 organizations. Tenable products were first CVE compatible in 2004. Tenable continues to lead the security industry in vulnerability management and continuous network monitoring by embracing accepted standards such as CVE. CVE identifiers are used to reference each of the vulnerabilities detected by Tenable Nessus. The CVE identifiers can be used for reporting, asset identification, risk management, and threat mitigation. This report helps to identify vulnerabilities by their CVE identifiers from 1999 to 2019. CVE is a widely used industry standard for identifying vulnerabilities across software vendors and vulnerability management systems. Using CVE identifiers to identify vulnerabilities allows organizations to easily target affected systems and software for remediation. As vendors provide patches for widespread vulnerabilities such as HeartBleed and ShellShock, many new plugins are released. The task of tracking vulnerabilities is simplified by using CVE identifiers, as the CVE identifiers for vulnerabilities remain the same even as new patches and plugins are released. Using CVE is a very flexible and useful method of detecting vulnerabilities to assist in the risk management process. This report provides an easy to understand executive summary showing the current count of vulnerabilities based on CVE release data and collection methods. The remaining chapters provide details on the top 100 most severe CVE vulnerabilities.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Credentialed Scan Failures                      | Scanning without credentials is a valid method for identifying what is visible to the scanner and assessing the exterior attack surface of a system, but properly configured credentialed scans are able to look beyond the surface and identify potential issues that may not be apparent. Credentialed scans provide more detailed results that can help to detect outdated software, vulnerabilities, and compliance issues. Without proper credentials, analysts will not be able to obtain accurate information to properly assess an organization's risk posture. This report delivers an organized list of failed credentialed scans that analysts can use to quickly address scanning issues on a network. The report covers a 25-day scanning history and provides a breakdown of various Windows scan issues and SSH failures, as well as general credential failures. Organizations will find this report useful when reviewed on a daily or weekly basis. The report is organized in a manner that provides timely information that analysts can use to correct any credentialed scan failures.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Critical and Exploitable Vulnerabilities Report | Identifying, prioritizing, and patching existing vulnerabilities on a network can be a difficult task for any analyst to manage effectively. By determining which vulnerabilities are most severe, analysts can properly prioritize vulnerability remediation in order to best protect systems on the network. This report presents a comprehensive look at the critical and exploitable vulnerabilities discovered on the network, which can be useful in reducing the overall attack surface and keeping critical data secured within an organization.Tenable products collect a vast amount of data on existing vulnerabilities discovered on the organization's network. Detailed analysis and understanding of risk for each vulnerability can be time consuming. However, the analyst should at least understand the impact of each vulnerability in order to understand the threat posed. The severity of a vulnerability is defined using the Common Vulnerability Scoring System (CVSS) base score. The CVSS is a method to define and characterize the severity of a vulnerability. Vulnerabilities are scored on a scale of 1 to 10, with a CVSS base score of 10 considered to be the most severe. Vulnerabilities with a CVSS base score of 10 are defined as ”critical.” In addition to specifying the severity of a vulnerability, industry sources are checked to determine if a publically-known exploit for the vulnerability exists. These critical and exploitable vulnerabilities create gaps in the network's integrity, which attackers can take advantage of to gain access to the network. Once inside the network, an attacker can perform malicious attacks, steal sensitive data, and cause significant damage to critical systems. By identifying the most severe vulnerabilities, analysts and security teams can better focus patch management efforts and better protect the network.This report provides information on critical and exploitable vulnerabilities that have been detected on the network. The report utilizes data such as the CVSS base score and information from exploit frameworks including Metasploit, Core Impact, Canvas, Elliot, and ExploitHub to determine which vulnerabilities are critical and exploitable. The report presents a cumulative view of the data to provide an analyst with a comprehensive understanding of the discovered critical and exploitable vulnerabilities. Using various visual aids, the report displays the data in an easy to understand manner. The information from this report will enable analysts to discover, prioritize, and remediate critical and exploitable vulnerabilities in a timely manner. |
| Elevated Privilege Failures                     | Organizations using Tenable Nessus gain a tremendous amount of details such as vulnerabilities, compliance status, software used, and hardware supporting the environment. Nessus provides valuable insight into systems to an analyst, to enable better protection of the network. As with any piece of software or hardware, Nessus needs to be properly configured to ensure the best scan results are returned. For scans of Linux/Unix based systems, analysts can configure the scans to use SSH username/password credentials, which allows Nessus to gather more detailed information about the systems. If a Nessus scan is configured with SSH credentials for a regular user account, basic information about a system can be retrieved. Once Nessus is able to create a session with SSH, Nessus will try to elevate privileges to retrieve further information about the system. If Nessus is unable to perform this action, Nessus plugin 12634 will report that the attempt to elevate permissions was unsuccessful (see https://community.tenable.com/message/14694). Using this report, analysts can identify systems that did not have adequate permissions to do in-depth scanning. Details are also provided to assist analysts in remediating the SSH credential issue. To prevent confusion, this report only addresses failures when Nessus attempts to elevate privileges from a scan; this report does not address attempts by users who try to elevate privileges and are unsuccessful.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Exploit Frameworks                              | Organizations of all size are faced with the challenges of maintaining a successful patch management program. In many cases, vulnerability scans and software updates are only performed on a monthly basis. The lack of visibility into the network and systems in between active scans can result in an increased risk to the organization. This point-in-time method of scanning and updating can also lead to systems being missed if the systems are not on the network or available during the scan window. A single vulnerability is often times the only necessary piece needed to gain a foothold in an environment. As an example, a network could be compromised due to a vulnerability found in out-of-date office productivity software, a PDF viewer, or a browser. Exploitation framework tools contain capabilities to detect and exploit these vulnerabilities. The vendors of these software packages are continually adding exploits to their platforms. Internal security teams and malicious actors alike can use the same tools to detect and exploit vulnerabilities. As some of the software exploitation tools are free, the bar of entry is minimal and can open up organizations to easy to perform attacks. This report can assist analysts in identifying vulnerabilities detected within the organization. Specifically, the report detects vulnerabilities that can be exploited by exploitation frameworks. Analysts can focus on the exploitable vulnerabilities to help reduce the risk to the organization. These specific exploitable vulnerabilities can present a heightened risk depending on the vulnerability and location in the organization. Analysts using this report can be more efficient at prioritizing efforts by knowing more about the vulnerabilities present in the organization. Within this report, analysts can find detailed information relating to the vulnerabilities exploitable by exploitation frameworks. The detailed information includes the host, vulnerability, and related information for each exploitation tool. There are also tables reporting vulnerabilities by plugin family, Microsoft bulletins, and CVE. Depending on the reporting metrics used within the organization, analysts can potentially compare the information from this report to their metrics for quick analysis. Information is also provided to assist analysts and administrators in fixing and mitigating the vulnerabilities.                                                                                                                                                                                                                 |
| Exploitable by Malware                          | Malware presents a risk to any organization and comes packaged in many forms. Malware can exploit weaknesses and vulnerabilities to make software or hardware perform actions not originally intended. Vulnerabilities can also be widely exploited shortly after publication as malware authors reverse engineer the fix and come up with ”1-day exploits” that can be used to attack organizations. Using this report, organizations can gain operational awareness of systems on the network with exploitable vulnerabilities. Analysts need to either mitigate the risk from vulnerabilities or remediate them, but prioritization is a necessary task, as not all vulnerabilities present an equal danger. Focusing on vulnerabilities actively exploited by malware helps to reduce the risk to the organization and offers prioritization guidance as to which vulnerabilities to remediate first. Analysts can use this report along with the knowledge of the software in the organization to better defend themselves. Vulnerabilities can also be exploited through common software applications. An attacker can use these software products to exploit vulnerabilities present in an organization. Products such as Metasploit, Core Impact, and exploits listed in ExploitHub can be used by anyone to perform an attack against vulnerabilities. Vulnerabilities that can be exploited through these means are highlighted in this report.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Malicious Code Prevention Report                | Malware can significantly impact the health and safety of critical systems within an organization. The number of new malware discovered on a daily basis continues to increase, and malware writers are constantly tweaking their code to keep it from being detected. Using malicious code, potentially massive attacks can be accomplished with relative ease. Network defenders need to use a defense-in-depth approach to both protect against malware infections and also discover and address any malware that gets through defenses. Inside this report, analysts will obtain the information needed to identify compromised hosts that have been infected with malware. Additional information on virus detections and interactions with known hostile IP addresses will highlight the presence of malware on network assets. Scans will determine whether anti-virus engines and virus definitions are running and up-to-date. Analysts will be able to obtain information on outdated or misconfigured anti-virus clients on the network. Systems are scanned for bad AutoRuns and Scheduled Tasks that may be associated with malware. Using the information presented within this report, organizations are able to quickly identify and remediate issues associated with malware or malicious activity on systems throughout the enterprise.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Outstanding Patch Tracking                      | One of the common questions often asked of the IT team is ”how many systems are missing patches and how many patches are missing on each system?” This report uses the Tenable Nessus ”Patch Report” plugin (66334) and organizes the current patch status for systems scanned with credentials. The IT team can now easily communicate the specific systems with missing patches to executives. The ”Patch Report” plugin elegantly summarizes all of the missing patches and general remediation actions required to remediate the discovered vulnerabilities on a given host. Instead of counting the number of vulnerabilities, the plugin lists applications that need to be upgraded. The approach is not only much easier for IT administrators to consume, but the count of applications provides a measure of how much ”work” is required to secure a system. In addition, this report can help analysts monitor the application of Microsoft Security Bulletin patches. The elements of this report displays information on missing Microsoft Security Bulletin patches, in order to provide a clear picture of the true state of Microsoft patch management.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Prioritize Hosts                                | What systems need attention now? What systems can be safely ignored for the time being? System administrators often have so much to do that it can be difficult for them to prioritize their host administration and mitigation efforts. This report can assist in that prioritization by presenting multiple lists of top hosts in various categories, such as top hosts infected with malware and top hosts with exploitable vulnerabilities. The elements in this report make use of active scan information from Tenable Nessus. In this way, a system administrator can obtain the most comprehensive and integrated view of the network, in order to make the best prioritization decisions about administration and mitigation efforts.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Unsupported OS Report                           | Detecting unsupported operating systems on a network can be a daunting task. Understanding which operating systems are unsupported or approaching end-of-life (EOL) can improve a security team's ability to mitigate vulnerabilities and secure the network. Systems running unsupported operating systems are more vulnerable to exploitation, so identifying and upgrading unsupported operating systems on a network is essential to an effective security program. Using this report, security teams can easily identify and address unsupported operating systems on a network. The chapters in this report provide detailed information about the unsupported operating systems detected by Nessus on the network. Elements filter by plugin name and vulnerability text in order to provide the most accurate overview of unsupported operating systems. A list of detailed information provides insight into systems running unsupported operating systems and recommended steps to address the vulnerabilities. Security teams can use the data in this report to detect and upgrade unsupported operating systems.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Vulnerabilities by Common Ports                 | Addressing vulnerable services is a key step in reducing network risk. Vulnerable services may allow malicious actors to infiltrate the network, compromise systems, and exfiltrate information. This report presents vulnerability information by common TCP ports and services, in order to alert the analyst to potentially vulnerable services. The elements in this report leverage a variety of active and passive port filters to display vulnerability information in multiple ways. System counts and vulnerability counts are presented based on specific ports, ranges of ports, and CVSS scores. Vulnerabilities that are known to be exploitable are highlighted; these vulnerabilities are especially concerning and should be addressed immediately. The vulnerability information in this report can be used to remediate service vulnerabilities and improve the security of the network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Vulnerability Detail Report                     | Vulnerability scanning and reporting are essential steps in evaluating and improving the security of a network. By knowing which vulnerabilities affect hosts on the network, security teams can coordinate their mitigation efforts more effectively. Nessus provides this vulnerability scan information. This report presents extensive data about vulnerabilities detected on the network. The report can be especially useful to security teams that are familiar with the format and content of reports generated by Nessus. Detailed information about the vulnerabilities detected on every host scanned is included. Security teams can use this report to easily identify vulnerabilities and the affected hosts in their network. The chapters in this report provide both a high-level overview and an in-depth analysis of the vulnerability status of the network. Charts are used to illustrate the ratio of vulnerability severities as well as list the most vulnerable hosts by vulnerability score. An iterator is used to provide detailed information on each host scanned. For each host, the IP address, DNS name, NetBIOS name, MAC address, repository, vulnerability total, and last scanned time are listed. A severity summary of each host shows how many vulnerabilities of each severity level impact that host. Detailed information about every vulnerability detected on that host is listed, including plugin ID, plugin name, plugin family, severity, protocol, port, exploitability, host CPE, plugin text, first discovered, and last seen times. Security teams can use this extensive data in order to identify vulnerabilities in their network and tailor their mitigation efforts accordingly.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Vulnerability Management                        | Vulnerable devices and applications on an organization's network pose a great risk to the organization. Vulnerabilities such as outdated software, susceptibility to buffer overflows, risky enabled services, etc. are weaknesses in the network that could be exploited. Organizations that do not continuously look for vulnerabilities and proactively address discovered flaws are very likely to have their network compromised and their data stolen or destroyed. This report provides a high-level overview of an organization's vulnerability management program and can assist the organization in identifying vulnerabilities, prioritizing remediations, and tracking remediation progress. In addition, this report assists in monitoring for sensitive data and data access vulnerabilities on the network. By understanding where sensitive or valuable information is kept and any associated vulnerabilities, security teams can better ensure file security and integrity.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Web Services Indicator                          | Services across enterprises are increasingly becoming web connected, but not all web services are secure. Organizations need to know what web services are operating in the environment in order to understand their vulnerability status. This report provides insight into the web services in the environment and the vulnerabilities associated with them. Administrators and analysts can better assess and defend the organization when they have the necessary information. This report provides information based around web services in the environment. Web services and the technology that hosts them are supported and implemented in various ways. The vulnerabilities of web services, web service platforms, and related technologies are displayed in ways that are easy to understand. Analysts can see vulnerabilities based on ports, web service activities leaving the organization, and web services that are present with known vulnerabilities. Network defenders can use the insight into the vulnerabilities in web services provided by this report to more effectively secure their network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Windows Unsupported and Unauthorized Software   | The proliferation of unsupported products is an issue for many organizations and increases the effort required to minimize risk. As applications reach their end-of-life (EOL), vendors stop offering support. As patches and updates are released for new versions of software, unsupported versions will be left out. Essentially zero-day vulnerabilities could be in effect for applications that are no longer supported. Therefore, security and stability decrease, raising concern as time progresses. Identifying systems running unsupported applications is an important part of assessing and minimizing organizational risk. This report presents unsupported and unauthorized products found in the environment. Elements include pie charts and tables to display, track, and report on unsupported and unauthorized applications. Vulnerability data for unsupported vulnerabilities is filtered using Nessus plugin 20811, Microsoft Windows Installed Software Enumeration, as well additional filters for unsupported applications. Within this report, sections include Wireshark, WinPcap, TeamViewer, and Steam as examples of unauthorized applications.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Wireless Configuration Report                   | As organizations continue to evolve, wireless technologies are being integrated into existing networks to support employee mobility needs. Since wireless access can expose devices to unique threats, monitoring devices for access to suspicious or malicious wireless networks is essential. This report provides extensive information about the wireless networks accessed by scanned hosts in the organization. Several specific plugins are used to gather extensive details about wireless interfaces and SSID connections from Windows and macOS hosts. Security teams can use this report to easily examine wireless configuration details for scanned hosts and tailor scanning policies in order to include additional hosts. The chapters in this report present both a high-level overview and an in-depth analysis of the wireless configurations detected on hosts in the network. Charts and tables demonstrate which plugins were able to successfully gather wireless configuration details from scanned hosts. An iterator is used to provide extensive detail about wireless configurations of each host, including network interfaces and SSID histories. Security teams can use this detailed report to identify and monitor the wireless connections and configurations of hosts in the organization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |


## Sources

- https://www.tenable.com/downloads/nessus
- https://docs.tenable.com/nessus/Content/InstallNessusLinux.htm
- https://docs.tenable.com/nessus/Content/InstallNessusWindows.htm
- https://docs.tenable.com/tenableio/vulnerabilitymanagement/Content/Scans/ScannerTemplates.htm

>**[Note]** Remember to use markdown syntax to organize information in useful ways.
