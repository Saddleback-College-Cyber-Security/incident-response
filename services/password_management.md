# Password Management

[home](../README.md)
- [Example](#Example)

## Incident Overview  

We all know what a password is, however management of passwords is a big part of information technology.   

This incident covers several different aspects of passwords, updated frequently to adhere to ever-changing guidelines for password length and complexity.

please note that instructions for windows is listed for windows 10. If you are working on a different version, please see [https://support.microsoft.com/]

- Current standard for minimum password length and complexity (as of April 2020)   
    - NIST recommends no password complexity requirements
    - NIST also recommends no password lifetime requirements - only forcing a password change when a password is suspected to be compromised.
    - NIST does require a list of common passwords to disallow.
    - NIST also recommends increasing the length of passwords
- How to perform:     
    - Change a password:
        - Linux
          - Note differences in OS (e.g. Windows, macOS, Linux)
          - Note differences in privilege requirement (e.g. whether ```sudo``` is needed on Linux)
        - Windows
          - local accounts
            - version 1803 and onward
              - click the reset button.
              - answer the security questions
            - prior to version 1803
              - reset the device
              - this WILL wipe your data however. make sure to backup important data!
          - Microsoft accounts
              - sign in to your Microsoft account.
                - if you forgot your password:
                  - click "Forgot my Password"
                  - follow the instructions listed
              - go to security in the settings app
              - select password security
              - follow the instructions listed
    - Change a password for Linux

    - Change password lifetime:
        - Linux:
          - 
        - Windows:
          - make sure you are a global admin! you cannot do any password lifetime changes unless you are a global admin
          - go to the settings app
          - navigate to security and privacy
          - select password expiration policy

[https://pages.nist.gov/800-63-FAQ/] for password requirements
[https://support.microsoft.com/en-us/help/4028457/windows-10-reset-your-local-account-password] for local account password reset on Windows 10
[https://docs.microsoft.com/en-us/microsoft-365/admin/manage/set-password-expiration-policy?view=o365-worldwide] for password lifetime
[https://support.microsoft.com/en-us/help/4026971/microsoft-account-how-to-reset-your-password] for microsoft account password reset on windows 10
>**[Note]** Remember to use markdown syntax to organize information in useful ways.
