<!-- This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA. -->

# Security Overview

[**Graylogs Home**](../README.md)
- [Default Ports](#Default-Ports)
- [Configuring TLS Ciphers](#Configuring-TLS-Ciphers)

To secure Graylogs, you should not use the pre-configured images, create a unique installation where you understand each component and secure the environment. Expose only the services that are needed and secure them whenever possible with TLS/SSL and some kind of authentication. 

When using Amazon Web Services and pre-configured AMI, never open all ports in the security group. Do not expose the server to the internet. Access Graylog only from within your VPC. Enable encryption for the communication.

## Default Ports

| Component | Port |
|-|-|
| Graylog \(web interface / API\) | 9000 \(tcp\) |
| Graylog to Elasticsearch | 9200 \(tcp\) |
| Elasticsearch node communication | 9300 \(tcp\) |
|  MongoDB | 27017 \(tcp\) |


## Configuring TLS Ciphers

All TLS enabled services are configured to support TLS 1.2 or greater by default.

When using nginx or Apache httpd for SSL termination the [Mozilla SSL Configuration Generator](https://ssl-config.mozilla.org/) will help to create a reasonably secure configuration for them.
