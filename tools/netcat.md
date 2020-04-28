# Netcat

[home](../README.md)
- [About](#About)
- [Usage](#Usage)
- [Port Scanning](#Port-Scanning)
	- [TCP Scan](#TCP-Scan)
	- [UDP Scan](#UDP-Scan)
- [Sending Data](#Sending-Data)
- [Listening for Data](#Listening-for-Data)


## About

[Netcat](https://nc110.sourceforge.io/ "Official Documentation") is a powerful networking utility for reading from and writing to network using TCP or UDP. The command is designed to be a dependable back-end that can be used directly or easily driven by other programs and scripts.

Additionally, [Ncat](https://nmap.org/ncat/) (included with [Nmap](./nmap.md "Nmap")) is an expanded version that supports:
- SSL
- IPv6
- SOCKS and HTTP proxies
- Connection Brokering

## Usage

Netcat is run with the `nc` command in a unix terminal.

```shell
$ nc [OPTIONS] <HOST> <PORT(s) OR RANGE> #Connect to HOST on PORT(s) or RANGE
```

## Port Scanning

```shell
$ nc google.com 22 #Single port
$ nc 10.0.0.2 22 25 #Multiple ports
$ nc www.amazon.com 22-443 #Port range
```

### TCP Scan

```shell
$ nc -nzv -w <TIMEOUT> <HOST> <PORT(s) OR RANGE>
$ -n #Do not preform a DNS lookup
$ -v #Verbose
$ -w <NUMBER> #Timeout after <NUMBER> seconds
$ -z #Scan for listening daemons without sending data
```

### UDP Scan

```shell
$ nc -nzvu -w <TIMEOUT> <HOST> <PORT(s) OR RANGE>
$ -u #Use UDP instead of the default option, TCP
```

## Sending Data

```shell
$ echo -n "TCP test" | nc -w1 10.0.0.2 2424 #Send TCP data to 10.0.0.2 on port 2424
$ nc -u -w1 10.0.0.2 2424 < text.txt #Send UDP data to 10.0.0.2 on port 2424
```

See [here](./command_line_nix.md#Piping-Data "Piping Data") for command redirection eg. "`|`" (pipe)

## Listening for Data

```shell
$ nc -l -p <PORT> #Listen for connections on PORT
```
