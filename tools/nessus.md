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

- ### Installation from browser
    - Nessus has downloader on their website for most of the popular operating systems: https://www.tenable.com/downloads/nessus
- ### Installation from command prompt on Linux
    - Red Hat version 6
      ```
      # rpm -ivh Nessus-<version number>-es6.x86_64.rpm
      ```
    - Debian version 6
      ```
      # dpkg -i Nessus-<version number>-debian6_amd64.deb
      ```
    - FreeBSD version 10
      ```
      # pkg add Nessus-<version number>-fbsd10-amd64.txz
      ```   


>**[Note]** Remember to use markdown syntax to organize information in useful ways.
>**[Note]** A free version of Nessus can be obtained using a student email address from the Tenable website.
