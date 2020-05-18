# Password Management

[home](../README.md)
- [Incident Overview](#Incident-Overview)
- [NIST Guidelines](#NIST-Guidelines)
- [Changing Passwords](#Changing-Passwords)
	- [Windows](#Windows)
	- [Linux](#Linux)
- [Password Lifetimes](#Password-Lifetimes)
	- [Linux](#Linux)
	- [Windows](#Windows)
- [Sources](#Sources)

## Incident Overview

We all know what a password is, however management of passwords is a big part of information technology.

This incident covers several different aspects of passwords, updated frequently to adhere to ever-changing guidelines for password length and complexity.

>Note that instructions for windows listed are for windows 10. If you are working on a different version, please see [https://support.microsoft.com/].

## NIST Guidelines

Current standard for minimum password length and complexity (as of April 2020)
- NIST recommends no password complexity requirements
- NIST also recommends no password lifetime requirements - only forcing a password change when a password is suspected to be compromised.
- NIST does require a list of common passwords to disallow
- NIST also recommends increasing the length of passwords

## Changing Passwords

### Windows

- local accounts
	- version 1803 and onward
		1. click the reset button
		2. answer the security questions
	- prior to version 1803
		- reset the device
		- this WILL wipe your data however. make sure to backup important data!
- Microsoft accounts
	1. sign in to your Microsoft account.
		- if you forgot your password:
		- click "Forgot my Password"
		- follow the instructions listed
	2. go to security in the settings app
	3. select password security
	4. follow the instructions listed

### Linux

```shell
$ sudo passwd <USERNAME> #Change password for USERNAME
```

For more see [passwd](../tools/command_line_nix.md#User-Manipulation).

## Password Lifetimes

### Linux

```shell
$ chage -M <DAYS> <USERNAME> #Force the user to change password in DAYS days
```

### Windows
1. make sure you are a global admin! you cannot do any password lifetime changes unless you are a global admin
2. go to the settings app
3. navigate to security and privacy
4. select password expiration policy

## Sources

- [password requirements](https://pages.nist.gov/800-63-FAQ/)
- [for local account password reset on Windows 10](https://support.microsoft.com/en-us/help/4028457/windows-10-reset-your-local-account-password)
- [password lifetime](https://docs.microsoft.com/en-us/microsoft-365/admin/manage/set-password-expiration-policy?view=o365-worldwide)
- [microsoft account password reset on windows 10](https://support.microsoft.com/en-us/help/4026971/microsoft-account-how-to-reset-your-password)
- [linux changing of passwords](https://www.cyberciti.biz/faq/linux-set-change-password-how-to/)
- [linux changing of passwords](https://www.cloudibee.com/change-password-expiry-in-linux/)
