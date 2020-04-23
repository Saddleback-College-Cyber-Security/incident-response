# Network File System (NFS)

[home](../README.md)
- [Example](#Example)

## Incident Overview  

Network File System (NFS) is a distributed file system protocol originally developed by Sun Microsystems in 1984, allowing a user on a client computer to access files over a computer network much like local storage is accessed. 

Research and provide information on the following concepts:  

- Overview of NFS
    - Use a Windows NFS file server to provide multi-protocol access to the same file share over both SMB and NFS protocols from multi- platform clients.
    - Deploy a Windows NFS file server in a predominantly non-Windows operating system environment to provide non-Windows client computers access to NFS file shares.
    - Migrate applications from one operating system to another by storing the data on file shares accessible through both SMB and NFS protocols.

(https://docs.microsoft.com/en-us/windows-server/storage/nfs/nfs-overview#practical-applications)
    
   - Common Tasks performed (e.g. setup, configuration, etc.
 
## **How to setup an NFS server**
##### Ubuntu Instalation
    $ sudo apt install nfs-kernel-server
    $ sudo systemctl start nfs-kernel-server.service
##### Configuration 
There are 3 files used in configuring NFS: exports, hosts.allow, and hosts.deny   
You can decide who can have access to which directories by eddting /etc/exports  
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
  
hosts.allow and hosts.deny act like whitelists and blacklists for who has access to what service.  
Formating ex:
```
service:host
portmap: 192.168.0.1 , 192.168.0.2
portmap:ALL
```
When a client tries to connect host.allow is checked first, if the hostis in the file they can connect. It then checks host.deny and rejects any hosts listed, if the client is in niether list they will connect.

- How to access and use an NFS server
    - Note differences in OS (e.g. Windows, macOS, Linux)
    - Note differences in privilage requirement (e.g. whether ```sudo``` is needed on Linux)
- How to find an instance running on a system
    - Note differences in OS (e.g. Windows, macOS, Linux)
    - Note differences in privilage requirement (e.g. whether ```sudo``` is needed on Linux)
- Common vulnerabilities and how to protect against them
- Strategies for maintenance (e.g. how to notice malicious activity, protect against attackers etc.)

>**[Note]** Remember to use markdown syntax to organize information in useful ways.
