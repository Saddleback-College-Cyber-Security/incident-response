# CEH Incident Response

- [Welcome](#Welcome)
	- [Table Of Contents](#Table-Of-Contents)
- [For Students in CEH](#For-Students-in-CEH)
	- [Grading](#Grading)
	- [Getting Started](#Getting-Started)
	- [Commit Formatting](#Commit-Formatting)
	- [Adding New Files](#Adding-New-Files)
	- [Final Remarks](#Final-Remarks)

## Welcome

Hello!  

If you are reading this, it means you have found the CEH / Saddleback College Cyber Operations Club Incident Response Github.

This document serves to provide information on the various technologies and protocols commonly seen throughout the information security world. 

Inside the directory `readme` you will find the following goodies to get you started on your journey.

- A list of topics being investigated (feel free to add to this!)
- A cheatsheet for markdown
- A list of all CEH students and their respective section assignments (this list is mostly for grading; feel free to add to any section!)
- A *very large* PDF with some introductory information on many of the topics in this 

### Table Of Contents

- General Vulnerabilities
	- [Linux System Vulnerabilities](./general_vulnerabilities/linux_system_vulnerabilities.md)
	- [Malware](./general_vulnerabilities/malware.md)
	- [Phishing](./general_vulnerabilities/phishing.md)
	- [Session Hijacking](./general_vulnerabilities/session_hijacking.md)
	- [Viruses](./general_vulnerabilities/viruses.md)
	- [Windows System Vulnerabilities](./general_vulnerabilities/windows_system_vulnerabilities.md)
- Hardware
	- [Network Switches](./hardware/network_switches.md)
- Services
	- [Central Authentication Service](./services/central_authentication_service.md)
	- [Central Logging (Graylogs)](./services/graylogs/README.md)
	- [File Transfer Protocol](./services/ftp.md)
	- [Jenkins](./services/jenkins.md)
	- [Network File Serviced](./services/network_file_service.md)
	- [Network Topology](./services/network_topology.md)
	- [Password Management](./services/password_management.md)
	- [Web Application Firewall](./services/web_application_firewall.md)
- Tools
	- [Command Line *nix](./tools/command_line_nix.md)
	- [Command Line Windows](./tools/command_line_win.md)
	- [Nessus](./tools/nessus.md)
	- [NetCat](./tools/netcat.md)
	- [Nmap](./tools/nmap.md)


## For Students in CEH

If you are a student in Professor Barnett's & Professor Karla's Certified Ethical Hacker course, you are required to participate in the creation of this document. 

As threatening as that sounds, don not fret - this will be **fun**!

### Grading

Grading is at the discretion of Professo Karla, and as such any final grading questions should be directred to her via discord or email. Grades will be based on participation in this project (again, at the discretion of Professor Karla).

Participation is tracked through your contributions to the git repo you are reading this from. As long as you are remembering to push your changes, your grade is secure.

### Getting Started

For those who are new to git/github, I *highly* recommend taking a look at [this link.](https://learngitbranching.js.org/?locale=en_US)

It contains a web app for learning git, starting as simple as making your first commit and getting as complicated as merge conflicts and complex branching.

For those looking to skip straight into using git, it can be downloaded and installed [here](https://git-scm.com/downloads)

Graphical options for git are available, however most develepors opt to use the command line version instead. The tutorial mentioned previously uses command line tools.

### Commit Formatting 

For those already getting started, please try to adhear to the formatting standards found in the various files already populating this repository.

When creating a commit, please attempt to adhear to the following format: 

```
[ADD] Text explaing what was added.
[EDIT] Text explaing what was edited.
[REMOVE] Text explaing what was removed.
```

### Adding New Files

When adding new files to the repository, please attempt to place them in reasonable locations based on their relevency to the designated directory names (e.g. put `tools` like nmap in the `tools` folder before you commit)

Also before pushing to github, please remember to go through the following steps in your process for commiting:

1. Create a new branch for different topics (e.g. if you are switching from working on passwords to session hijacking, make a new branch called `section/session-hijacking)
2. Add your changes to the working tree and commit them.
3. Push your changes, remembering to run the first-time push command if this is a new branch (if you are lazy like me you can just let the command line tell you what it is)
4. Go to this repository on Github and create a pull request. Assuming you completed the following 3 steps correctly, Github *should* automatically tell you to make one. 
5. Await your pull request's approval, as Karla and Felix will be approving pull requests in order to maintain the repository

>If this all seems alien to you, don't panic! The tutorial mentioned earlier can help you learn these terms and steps!

### Final Remarks

With all that said, happy researching and feel free to reach out to Karla or Felix with any questions or concerns!
