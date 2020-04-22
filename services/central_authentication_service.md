# Central Authentication Service

[home](../README.md)
- [Example](#Example)

## Incident Overview  

The Central Authentication Service (CAS) is a single sign-on protocol for the web.  
Its purpose is to permit a user to access multiple applications while providing their credentials (such as userid and password) only once.   
It also allows web applications to authenticate users without gaining access to a user's security credentials, such as a password.   
The name CAS also refers to a software package that implements this protocol.      

Research and provide information on the following concepts:  

- How to find an instance of CAS running on a system
    - Note differences in OS (e.g. Windows, macOS, Linux)
    - Note differences in privilage requirement (e.g. whether ```sudo``` is needed on Linux)
- Common vulnerabilities and how to protect against them
- Strategies for maintenance (e.g. how to notice malicious activity, protect against attackers etc.)

## Overview of CAS

CAS is an enterprise multilingual single sign-on solution for the web and attempts to be a comprehensive platform for your authentication and authorization needs. CAS is an open and well-documented authentication protocol.   
The primary implementation of the protocol is an open-source Java server component by the same name hosted here, with support for a plethora of additional authentication protocols and features.  

CAS can be implemented in two main different ways, those being **Apereo CAS Implementation** or **Django Implemention**  

>**[Note]** This incident response will cover Apereo as opposed to Django due to Apereo's extensive documentation. Django CAS information may be added at a later date.

Looking at Apereo, it supports the contains the follow features: 

| Feature                                                                                                                                                       |
| :---                                                                                                                                                          |
| CAS v1, v2 and v3 Protocol                                                                                                                                    |                  
| SAML v1 and v2 Protocol                                                                                                                                       |                    
| OAuth Protocol                                                                                                                                                |                     
| OpenID & OpenID Connect Protocol                                                                                                                              |                     
| WS-Federation Passive Requestor Protocol                                                                                                                      |                 
| Authentication via JAAS, LDAP, RDBMS, X.509, Radius, SPNEGO, JWT, Remote, Trusted, BASIC, Apache Shiro, MongoDB, Pac4J and more.                              |                     
| Delegated authentication to WS-FED, Facebook, Twitter, SAML IdP, OpenID, OpenID Connect, CAS and more.                                                        |                    
| Authorization via ABAC, Time/Date, REST, Internet2's Grouper and more.                                                                                        |                   
| HA clustered deployments via Hazelcast, Ehcache, JPA, Memcached, Apache Ignite, MongoDB, Redis, Couchbase and more.                                           |                     
| Application registration backed by JSON, LDAP, YAML, JPA, Couchbase, MongoDB and more.                                                                        |                    
| Multifactor authentication via Duo Security, SAASPASS, YubiKey, RSA, Google Authenticator (TOTP) and more                                                     |                    
| Administrative UIs to manage logging, monitoring, statistics, configuration, client registration and more.                                                    |                   
| Global and per-application user interface theme and branding.                                                                                                 |                     
| Password management and password policy enforcement.                                                                                                          |                   

## CAS Architecture (Apereo CAS Enterprise)

![casarchitecture](https://apereo.github.io/cas/6.1.x/images/cas_architecture.png)

### System Components

The CAS server and clients comprise the two physical components of the CAS system architecture that communicate by means of various protocols.

### CAS Server

The CAS server is Java servlet built on the Spring Framework whose primary responsibility is to authenticate users and grant access to CAS-enabled services, commonly called CAS clients, by issuing and validating tickets. An SSO session is created when the server issues a ticket-granting ticket (TGT) to the user upon successful login. A service ticket (ST) is issued to a service at the user’s request via browser redirects using the TGT as a token. The ST is subsequently validated at the CAS server via back-channel communication. These interactions are described in great detail in the CAS Protocol document.

### CAS Clients

The term “CAS client” has two distinct meanings in its common use. A CAS client is any CAS-enabled application that can communicate with the server via a supported protocol. A CAS client is also a software package that can be integrated with various software platforms and applications in order to communicate with the CAS server via some authentication protocol (e.g. CAS, SAML, OAuth). CAS clients supporting a number of software platforms and products have been developed.

**Platforms:**

    Apache httpd Server (mod_auth_cas module)
    Java (Java CAS Client)
    .NET (.NET CAS Client)
    PHP (phpCAS)
    Perl (PerlCAS)
    Python (pycas)
    Ruby (rubycas-client)

**Applications:**

    Canvas
    Atlassian Confluence
    Atlassian JIRA
    Drupal
    Liferay
    uPortal
    etc.

When the term “CAS client” appears in this manual without further qualification, it refers to the integration components such as the Java CAS Client rather than to the application relying upon (a client of) the CAS server.

### Suppported Protocols 

Clients communicate with the server by any of several supported protocols. All the supported protocols are conceptually similar, yet some have features or characteristics that make them desirable for particular applications or use cases. For example, the CAS protocol supports delegated (proxy) authentication, and the SAML protocol supports attribute release and single sign-out.

**List of Supported Protocols:**

    CAS (versions 1, 2, and 3)
    SAML 1.1 and 2
    OpenID Connect
    OpenID
    OAuth 2.0
    WS Federation

### Software Components

It is helpful to describe the CAS server in terms of *three* layered subsystems:

    Web (Spring MVC/Spring Webflow)
    Ticketing
    Authentication

Almost all deployment considerations and component configuration involve those three subsystems. The Web tier is the endpoint for communication with all external systems including CAS clients. The Web tier delegates to the ticketing subsystem to generate tickets for CAS client access. The SSO session begins with the issuance of a ticket-granting ticket on successful authentication, thus the ticketing subsystem frequently delegates to the authentication subsystem.

The authentication system is typically only processing requests at the start of the SSO session, though there are other cases when it can be invoked (e.g. forced authentication).

## Installation

Installation of CAS is broken into 6 sections:

1. Java
2. Serverlet Containers
3. Build Tools
4. Git (Optional but Recommended)
5. OS
6. Internet Connectivity 
7. Hardware

### Java

CAS at its heart is a Java-based web application. Prior to deployment, you will need to have JDK 11 installed.

#### Windows

Step 1: Go to this [link](https://download.java.net/openjdk/jdk11/ri/openjdk-11+28_windows-x64_bin.zip)

Step 2: Run the downloaded installer to install.

#### Linux

Step 0 (Optional): Install ```wget```.

```shell
sudo apt install wget
```

Step 1: Download JDK 11 using the ```wget``` command.

```shell
wget https://download.java.net/openjdk/jdk11/ri/openjdk-11+28_linux-x64_bin.tar.gz
```

**Sources:**

https://apereo.github.io/cas/6.1.x/index.html   
https://apereo.github.io/cas/6.1.x/planning/Architecture.html  
https://apereo.github.io/cas/6.1.x/planning/Getting-Started.html  
https://apereo.github.io/cas/6.1.x/planning/Installation-Requirements.html  
https://apereo.github.io/cas/6.1.x/installation/WAR-Overlay-Installation.html  

>**[Note]** Remember to use markdown syntax to organize information in useful ways.