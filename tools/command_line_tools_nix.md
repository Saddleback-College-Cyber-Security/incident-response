## Command Line Tools for *NIX  

### Incident Overview  

Navigation and use of command line tools is a viable skill for any cyber security analyst. This section details various scenarios and commands for different *NIX systems.  

### I Need Help, Where Can I Go?  

The manual man is where most of the important info will be for any given command. The arg passed to man is normally the name of a program, utility or function.   

```shell
$ man <ARG>                                                                
$ man man #This will show how to use the man command
```

### General Commands    

Superuser do `sudo` is a way to run a command (and only that command) as root while logged in as a non-root user.  

>Note: asks for root password.  

```shell
$ sudo <COMMAND> #Run COMMAND as root from a non-root user account         
$ sudo !! #Run the previous command as root
```

The switch user `su` command is used to become another user during a login session.  

```shell
$ su #Become root                                                          
$ su <USER> #Become USER
```

`exit` is used for normal process termination including exiting login sessions (including ssh) and scripts.

```shell
$ exit #exit                                                               
$ exit(<NUM>) #exit with code NUM
```

The List command `ls` is used to show the files in the current directory.

```shell
$ ls #Print files in current directory                                     
$ ls <DIR> #Print files in DIR
```

`cd` is used to change directory.

```shell
$ cd <DIR> #Change directory to DIR
```

The concatenate `cat` command can be used to print files to the standard output.

```shell
$ cat <FILE> #Prints FILE to screen
```                                        

### Connecting

The secure shell client `ssh` is a program that allows the connection to a remote machine that is running an ssh server.  

```shell
$ ssh <USER>@<ADDRESS> #Connect to ADDRESS as USER                         
$ ssh <USER>@<ADDRESS> -p <PORT> #Connect to ADDRESS as USER on remote PORT
$ ssh <ADDRESS> #Connect to ADDRESS as your logged in username
```             
### System Identification

Identifying a fresh system you have been handed with no prior context is important for knowing which command syntax to use.

```shell
$ cat /etc/lsb-release #Print Distribution info                            
$ cat /etc/issue.net #Print Distribution info                              
$ cat /etc/debian_version  #Debian Only
```

The `uname` command shows system information.

```shell
$ uname #Print kernel name                                                 
$ uname -a #Print all system info: kernel, node, release, version, machine, processor, platform, os                                                    
```

The `hostname` command(s) can be used to show or change the name of the machine.

```shell
$ hostname #Show or set the hostname                                       
$ domainname #Show or set the domain name                                  
$ dnsdomainname #Show or set the dns domain name                           
```

### User Administration

```shell
$ cat /etc/passwd #Show pwd file for all users on the system
                  #(pwds not actually stored here. They are in /etc/shadow)      
$ getent passwd {1000..60000} #Show non-application users
```

`who` shows info about currently logged in users.

```shell
$ who                                                                      
$ who -u #Show non-application users that are logged in
```

The `lastlog` command shows info about when a user was last logged on.

```shell
$ lastlog #Show info for all users                                         
$ lastlog -u <USER> #Show info for only USER 
```

`passwd` is used for changing passwords for user accounts.

```shell
$ passwd #Change password for current user                                 
$ passwd <USER> #Change password for USER                                  
$ passwd -l <USER> #Lock user account
```

`useradd` and `groupadd` add users and groups to the system.

```shell
$ useradd <USER> #Add USER to the system                                   
$ groupadd <GROUP> #Add GROUP to the system
```

`usermod` changes system account files

```shell
$ usermod -a -G <GROUP> <USER> #Add USER to GROUP
```

`userdel` deletes a user from the system

```shell
$ userdel <USER> #Delete USER from system                                  
$ userdel -r <USER> #Delete USER from system and delete $HOME              
```

### Service Administration

Listing all services on the machine.

```shell
$ service --list-all #For older Operating Systems
$ systemctl list-unit-files
$ systemctl list-units --type service
```

Stopping/starting/restarting a service

```shell 
$ service [service] [stop/start/restart]       
$ systemctl [stop/start/restart] [service]
```

Opening/closing a port

```shell
$ ufw [allow/deny] [port] #Debian
$ firewall-cmd --zone=public --permanent  --[add/remove]-port=[port]/tcp            #CentOS
$ firewall-cmd --reload    #CentOS
```

### Kicking someone off of a system

See who's logged into your machine -- use `who` or `w`

```shell
$ who
mmrozek    tty1             Aug 17 10:03
mmrozek    pts/3            Aug 17 10:09 (:pts/2:S.0)
```

Look up the process ID of the shell their TTY is connected to

```shell 
$ ps t
PID     TTY     STAT    TIME COMMAND
30737   pts/3   Ss      0:00 zsh
```

>**[Note]** The preceding 2 steps can be combined by passing the `-u` flag to the `who` command  

Laugh at their impending disconnection (*this step is optional, but encouraged*)

```shell
$ echo "HAHAHAHAHAHAHAHAHAHAHAHAHAHAHA" | write mmrozek pts/3
```

Kill the corresponding process

```shell
$ kill -9 30737
```

>**[REQUEST]** More info needed on IP tables

>**[Note]** Remember to use markdown syntax to organize information in useful ways.
