<!-- This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA. -->

# Network File System (NFS)

[**Incident Response Home**](../README.md)
- [Incident Overview](#Incident-Overview)
- [How to setup an NFS server](#How-to-setup-an-NFS-server)
	- [Windows Installation](#Windows-Installation)
	- [Ubuntu Installation](#Ubuntu-Installation)
	- [CentOS Installation](#CentOS-Installation)
	- [Configuration](#Configuration)
- [How to access and use an NFS server](#How-to-access-and-use-an-NFS-server)
	- [Client Installation](#Client-Installation)
		- [Windows](#Windows)
		- [Ubuntu](#Ubuntu)
		- [CentOS](#CentOS)
	- [Client Configuration](#Client-Configuration)
		- [Windows](#Windows)
		- [Linux Configuration](#Linux-Configuration)
- [Sources](#Sources)

## Incident Overview

The Network File System (NFS) was developed to allow machines to mount a disk partition on a remote machine as if it were a local disk.

NFS is a distributed file system protocol originally developed by Sun Microsystems in 1984, allowing a user on a client computer to access files over a computer network much like local storage is accessed. 

Research and provide information on the following concepts:  

- Overview of NFS
	- Use a Windows NFS file server to provide multi-protocol access to the same file share over both SMB and NFS protocols from multi- platform clients.
	- Deploy a Windows NFS file server in a predominantly non-Windows operating system environment to provide non-Windows client computers access to NFS file shares.
	- Migrate applications from one operating system to another by storing the data on file shares accessible through both SMB and NFS protocols.

(https://docs.microsoft.com/en-us/windows-server/storage/nfs/nfs-overview#practical-applications)

	- Common Tasks performed (e.g. setup, configuration, etc.

## How to setup an NFS server

### Windows Installation

```powershell
> Import-Module ServerManager
> Add-WindowsFeature FS-NFS-Service
> Import-Module NFS
```

### Ubuntu Installation

```shell
$ sudo apt install nfs-kernel-server
$ sudo systemctl start nfs-kernel-server.service
```

### CentOS Installation

```shell
$ yum install nfs-utils
```

Co-req: portmap needs to be runing before nfs

### Configuration

There are 3 files used in configuring NFS: `exports`, `hosts.allow`, and `hosts.deny`

You can decide who has access to which directories by editing `/etc/exports`

Formating ex:

```
/user/local 192.168.0.1(rw,sync,no_subtree_check) 192.168.0.2(rw)
/home 192.168.0.0/255(rw,sync,no_subtree_check)
/user/mike *(rw,sync,no_subtree_check)
/user/shared foo.cybercity.com(rw,sync,no_subtree_check) *.cybercity.com(rw)
```

- rw: Read + write permission (default)
- ro: Read only
- no_root_squash: A root user on the client computer will have root access on the server. (security risk)
- no_subtree_check: Verifies that a file that is requested from the client is in the appropriate part of the volume
- sync: Helps prevent data corruption 

`hosts.allow` and `hosts.deny` act like whitelists and blacklists for who has access to what service.

Formating ex:

```
service:host
portmap: 192.168.0.1 , 192.168.0.2
portmap:ALL
```

When a client tries to connect, `host.allow` is checked first, if the host is in the file they can connect. It then checks `host.deny` and rejects any hosts listed, if the client is in neither list they will connect.

## How to access and use an NFS server

### Client Installation

#### Windows

1. Start > Control Panel > Programs
2. Turn Windows features on or off
3. Services for NFS
4. Open regedit
5. Make two new DWORD inside `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default` called `AnonymousUid` and `AnonymousGid`. Enter the UID and GID of the system hosting the NFS server
6. Restart the client or computer

#### Ubuntu

```shell
$ sudo apt install nfs-common
```

#### CentOS

```shell
$ yum install nfs-utils
```

### Client Configuration

#### Windows

	$ sudo mount [IP/domain name]:[filepath of the directory on the server] [Drive letter]
	$ sudo mount 192.198.0.1:/home l:

#### Linux Configuration

The client system needs to mount the remote directory from the host server onto a local directory to access the shared files. Preferably the mount point on the client should be located in the ```/mnt``` directory and must be empty

Command ex:

```shell
$ sudo mount [IP/domain name]:[filepath of the directory on the server] [filepath on client]
$ sudo mount 192.198.0.1:/home /mnt/home
$ sudo mount bar.cybercity.com:/home/server_folder /mnt/client_mnt_point
```

You can also unmount

```shell
$ sudo unmount [filepath on client]  
```

- How to find an instance running on a system
	- Note differences in OS (e.g. Windows, macOS, Linux)
	- Note differences in privilage requirement (e.g. whether ```sudo``` is needed on Linux)
- Common vulnerabilities and how to protect against them
- Strategies for maintenance (e.g. how to notice malicious activity, protect against attackers etc.)

## Sources

sources: http://nfs.sourceforge.net/
