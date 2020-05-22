# server.conf

[**Graylogs Home**](../README.md)

**Source:** http://docs.graylog.org/en/2.4/pages/installation/os/ubuntu.html

**Summary:** This config includes general information, web and rest API, and elastic search. If any other infromation is needed for config visit the link above.

### The file server.conf is the Graylog configuration file.

**Note:** Check Default file locations to locate it in your installation.

It has to use ISO 8859-1/Latin-1 character encoding. Characters that cannot be directly represented in this encoding can be written using Unicode escapes as defined in Java SE Specifications, using the u prefix. For example, u002c.

**Entries are generally expected to be a single line of the form, one of the following:**

* propertyName=propertyValue

* propertyName:propertyValue

**White space that appears between the property name and property value is ignored, so the following are equivalent:**

* name=Stephen

* name = Stephen

White space at the beginning of the line is also ignored.

Lines that start with the comment characters ! or # are ignored. Blank lines are also ignored.

The property value is generally terminated by the end of the line. White space following the property value is not ignored, and is treated as part of the property value.

*A property value can span several lines if each line is terminated by a backslash (\) character. For example:**

    targetCities=\
       Detroit,\
       Chicago,\
       Los Angeles

This is equivalent to **targetCities=Detroit,Chicago,Los Angeles** (white space at the beginning of lines is ignored).

The characters newline, carriage return, and tab can be inserted with characters \n, \r, and \t, respectively.

The backslash character must be escaped as a double backslash. For example:

    path=c:\\docs\\doc1


# Properties #


## General ##

**is_master = true**

* If you are running more than one instances of Graylog server you have to select only one graylog-server node as the master. This node will perform periodical and maintenance actions that slave nodes won’t.

* Every slave node will accept messages just as the master nodes. Nodes will fall back to slave mode if there already is a master in the cluster.

	node_id_file = /etc/graylog/server/<node-id>

* The auto-generated node ID will be stored in this file and read after restarts. It is a good idea to use an absolute file path here if you are starting Graylog server from init scripts or similar.

**password_secret = <secret>**

* You MUST set a secret that is used for password encryption and salting. The server will refuse to start if it’s not set. Use at least 64 characters. If you run multiple graylog-server nodes, make sure you use the same password_secret for all of them!

**Note:**

**Generate a secret with for example:**

    pwgen -N 1 -s 96

**root_username = admin**

* The default root user is named admin.

	root_password_sha2 = <SHA2>

* A SHA2 hash of a password you will use for your initial login. Set this to a SHA2 hash generated with echo -n "Enter Password: " && head -1 </dev/stdin | tr -d '\n' | sha256sum | cut -d" " -f1 and you will be able to log in to the web interface with username admin and password yourpassword.

**Caution:**
**You MUST specify a hash password for the root user (which you only need to initially set up the system and in case you lose connectivity to your authentication backend). This password cannot be changed using the API or via the web interface. If you need to change it, modify it in this file.**


       root_email = ""

* The email address of the root user. Default is empty.

	root_timezone = UTC

* The time zone setting of the root user. See this list of valid time zones. Default is UTC.

	bin_dir = bin

* This directory contains binaries that are used by the Graylog server. (relative or absolute)

	data_dir = data
      
* This directory is used to store Graylog server state. (relative or absolute)

	plugin_dir = plugin

* Set plugin directory here (relative or absolute)

## Web & REST API ##

    http_bind_address = 127.0.0.1:9000

* The network interface used by the Graylog HTTP interface.

* This network interface must be accessible by all Graylog nodes in the cluster and by all clients using the Graylog web interface.

* If the port is omitted, Graylog will use port 9000 by default.

	http_publish_uri = http://$http_bind_address/

* The HTTP URI of this Graylog node which is used to communicate with the other Graylog nodes in the cluster and by all clients using the Graylog web interface.

* The URI will be published in the cluster discovery APIs, so that other Graylog nodes will be able to find and connect to this Graylog node.

* This configuration setting has to be used if this Graylog node is available on another network interface than $http_bind_address, for example if the machine has multiple network interfaces or is behind a NAT gateway.

* This configuration setting must not be configured to a wildcard address!

* If 

	http_bind_address 

contains a wildcard IPv4 address (0.0.0.0), http_publish_uri will be filled with the first non-loopback IPv4 address of this machine instead.

    http_external_uri = $http_publish_uri

* The public URI of Graylog which will be used by the Graylog web interface to communicate with the Graylog REST API.

* The external Graylog URI usually has to be specified, if Graylog is running behind a reverse proxy or load-balancer and it will be used to generate URLs addressing entities in the Graylog REST API (see $http_bind_address).

* When using Graylog Collector, this URI will be used to receive heartbeat messages and must be accessible for all collectors.

* This setting can be overriden on a per-request basis with the “X-Graylog-Server-URL” HTTP request header.

	http_enable_cors = true

* Enable CORS headers for HTTP interface.

* This is necessary for JS-clients accessing the server directly.

* If these are disabled, modern browsers will not be able to retrieve resources from the server.

	http_enable_gzip = true

* This compresses API responses and therefore helps to reduce overall round trip times.

	http_max_header_size = 8192

* The maximum size of the HTTP request headers in bytes.

	http_thread_pool_size = 16

* The size of the thread pool used exclusively for serving the HTTP interface.

	http_enable_tls = false

* This secures the communication with the HTTP interface with TLS to prevent request forgery and eavesdropping.

	http_tls_cert_file = /path/to/graylog.crt

* The X.509 certificate chain file in PEM format to use for securing the HTTP interface.

	http_tls_key_file = /path/to/graylog.key

* The PKCS#8 private key file in PEM format to use for securing the HTTP interface.

	http_tls_key_password = secret

* The password to unlock the private key used for securing the HTTP interface. (if key is encrypted)

	trusted_proxies = 127.0.0.1/32, 0:0:0:0:0:0:0:1/128

* Comma separated list of trusted proxies that are allowed to set the client address with X-Forwarded-For header. May be subnets, or hosts.

##Elasticsearch##

    elasticsearch_hosts = http://node1:9200,http://user:password@node2:19200

* List of Elasticsearch hosts Graylog should connect to.

* Need to be specified as a comma-separated list of valid URIs for the http ports of your elasticsearch nodes.

* If one or more of your elasticsearch hosts require authentication, include the credentials in each node URI that requires authentication.

* Default: http://127.0.0.1:9200

	elasticsearch_connect_timeout = 10s

* Maximum amount of time to wait for successfull connection to Elasticsearch HTTP port.

* Default: 10 seconds

	elasticsearch_socket_timeout = 60s

* Maximum amount of time to wait for reading back a response from an Elasticsearch server.

* Default: 60 seconds

	elasticsearch_idle_timeout = -1s

* Maximum idle time for an Elasticsearch connection. If this is exceeded, this connection will be tore down.

* Default: infinity

       elasticsearch_max_total_connections = 200

* Maximum number of total connections to Elasticsearch.

* Default: 200

	elasticsearch_max_total_connections_per_route = 20

* Maximum number of total connections per Elasticsearch route (normally this means per elasticsearch server).

* Default: 20

	elasticsearch_max_retries = 2

* Maximum number of times Graylog will retry failed requests to Elasticsearch.

* Default: 2

elasticsearch_discovery_enabled = false

* Enable automatic Elasticsearch node discovery through Nodes Info, see Elasticsearch Reference » Cluster APIs » Nodes Info.

* Default: false

**Warning:
Automatic node discovery does not work if Elasticsearch requires authentication, e. g. with Shield.**

**Warning:
This setting must be false on AWS Elasticsearch Clusters (the hosted ones) and should be used carefully. In case of trouble with connections to ES this should be the first option to be disabled. See Automatic node discovery for more details.**

elasticsearch_discovery_filter = rack:42

* Filter for including/excluding Elasticsearch nodes in discovery according to their custom attributes, see Elastic Search Reference » Cluster APIs » Node Specification.

* Default: empty

	elasticsearch_discovery_frequency = 30s

* Frequency of the Elasticsearch node discovery.

* Default: 30 seconds

	elasticsearch_discovery_default_scheme = http

* Set the default scheme when connecting to Elasticsearch discovered nodes. (available options: http, https)

* Default: http

	elasticsearch_compression_enabled = false

* Enable payload compression for Elasticsearch requests.

* Default: false

	elasticsearch_use_expect_continue = true

* Enable use of “Expect: 100-continue” Header for Elasticsearch index requests. If this is disabled, Graylog cannot properly handle HTTP 413 Request Entity Too Large errors.

* Default: true
