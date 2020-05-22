# Default file locations

[**Graylogs Home**](../README.md)
- [DEB Package](#DEB-Package)
	- [Graylog](#Graylog)
	- [Elasticsearch](#Elasticsearch)
	- [MongoDB](#MongoDB)
- [RPM Package](#RPM-Package)
	- [Graylog](#Graylog)
	- [Elasticsearch](#Elasticsearch)
	- [MongoDB](#MongoDB)

## DEB Package

Each installation flavor of Graylog will place the configuration files into a specific location on the local files system. The goal of this section is to provide a short overview about the most common and most important default file locations.

### Graylog

| File system path | |
|-|-|
| Configuration | /etc/graylog/server/server.conf |
| Logging configuration | /etc/graylog/server/log4j2.xml |
| Plugins | /usr/share/graylog-server/plugin |
| Binaries | /usr/share/graylog-server/bin |
| Scripts | /usr/share/graylog-server/scripts|
| JVM settings | /etc/default/graylog-server |
| Message journal files | /var/lib/graylog-server/journal |
| Log Files | /var/log/graylog-server/ |

### Elasticsearch

| File system path | |
|-|-|
| Configuration | /etc/elasticsearch |
| Data files | /var/lib/elasticsearch/data |
| JVM settings | /etc/default/elasticsearch |
| Log Files | /var/log/elasticsearch/ |

### MongoDB

| File system path | |
|-|-|
| Configuration | /etc/mongod.conf |
| Data files | /var/lib/mongodb/ |
| Log Files | /var/log/mongodb/ |

## RPM Package

This paragraph covers Graylog installations on Fedora Linux, Red Hat Enterprise Linux, CentOS Linux, and other Red Hat Linux derivates installed with the RPM package.

### Graylog

| File system path | |
|-|-|
| Configuration | /etc/graylog/server/server.conf |
| Logging configuration | /etc/graylog/server/log4j2.xml |
| Plugins | /usr/share/graylog-server/plugin |
| Binaries | /usr/share/graylog-server/bin |
| Scripts | /usr/share/graylog-server/scripts |
| JVM settings | /etc/sysconfig/graylog-server |
| Message journal files | /var/lib/graylog-server/journal |
| Log Files | /var/log/graylog-server/ |

### Elasticsearch

>These are only the most common file locations. Please refer to the Elasticsearch documentation for a comprehensive list of default file locations.

| File system path | |
|-|-|
| Configuration | /etc/elasticsearch |
| Data files | /var/lib/elasticsearch/data |
| JVM settings | /etc/sysconfig/elasticsearch |
| Log Files | /var/log/elasticsearch/ |

### MongoDB
| File system path | |
|-|-|
| Configuration | /etc/mongod.conf |
| Data files | /var/lib/mongodb/ |
| Log Files | /var/log/mongodb/ |
