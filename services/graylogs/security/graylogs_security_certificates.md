# Security Certificates

[**Graylogs Home**](../README.md)
- [Required Certificates](#Required-Certificates)
- [Graylog Stack Certificate Template](#Graylog-Stack-Certificate-Template)
- [Generating The Keypair and Certificates](#Generating-The-Keypair-and-Certificates)
	- [Preparation](#Preparation)
	- [Execution](#Execution)
	- [Conversion](#Conversion)
- [CA Chain](#CA-Chain)
- [MongoDB](#MongoDB)
- [Graylog and ElasticSearch](#Graylog-and-ElasticSearch)

## Required Certificates

| Goal | Subject | Subject alt\. names | Filetype  |
|-|-|-|-|
| MongoDB 1 | CN=hostname1\.mydomain\.local | dns:hostname1 dns:hostname1\.mydomain\.local dns:graylogmongoalias\.mydomain\.local dns:graylogmongoalias ip:192\.168\.100\.101 | PEM PKCS\#12 \(cert\+key in one\) |
| MongoDB 2 | CN=hostname2\.mydomain\.local | dns:hostname2 dns:hostname12mydomain\.local dns:graylogmongoalias\.mydomain\.local dns:graylogmongoalias ip:192\.168\.100\.102 | PEM PKCS\#12 \(cert\+key in one\) |
| MongoDB 3 | CN=hostname3\.mydomain\.local | dns:hostname3 dns:hostname3\.mydomain\.local dns:graylogmongoalias\.mydomain\.local dns:graylogmongoalias ip:192\.168\.100\.103 | PEM PKCS\#12 \(cert\+key in one\)        |
| Graylog frontend | CN=hostname4\.mydomain\.local | dns:hostname4 dns:hostname4\.mydomain\.local dns:graylogguialias\.mydomain\.local dns:graylogguialias ip:192\.168\.100\.104 | PEM \(certificate\) PKCS\#8 \(key file\) |
| Graylog receiver 1 | CN=hostname5\.mydomain\.local | dns:hostname5 dns:hostname5\.mydomain\.local dns:graylogreceiveralias\.mydomain\.local dns:graylogreceiveralias ip:192\.168\.100\.105 | PEM \(certificate\) PKCS\#8 \(key file\) |
| Graylog receiver 2 | CN=hostname6\.mydomain\.local | dns:hostname6 dns:hostname6\.mydomain\.local dns:graylogreceiveralias\.mydomain\.local dns:graylogreceiveralias ip:192\.168\.100\.106 | PEM \(certificate\) PKCS\#8 \(key file\) |
| Graylog receiver 3 | CN=hostname7\.mydomain\.local | dns:hostname7 dns:hostname7\.mydomain\.local dns:graylogreceiveralias\.mydomain\.local dns:graylogreceiveralias ip:192\.168\.100\.107 | PEM \(certificate\) PKCS\#8 \(key file\) |
| SearchGuard Admin | CN=searchguardadmin,O=yourorganization | | PEM \(certificate\) PKCS\#8 \(key file\) |
| ElasticSearch 1 | CN=hostname8\.mydomain\.local | dns:hostname8 dns:hostname8\.mydomain\.local dns:graylogelasticalias\.mydomain\.local dns:graylogelasticalias ip:192\.168\.100\.108 | PEM \(certificate\) PKCS\#8 \(key file\) |
| ElasticSearch 2 | CN=hostname9\.mydomain\.local | dns:hostname9 dns:hostname9\.mydomain\.local dns:graylogelasticalias\.mydomain\.local dns:graylogelasticalias ip:192\.168\.100\.109 | PEM \(certificate\) PKCS\#8 \(key file\) |
| ElasticSearch 3 | CN=hostname9\.mydomain\.local | dns:hostname9 dns:hostname9\.mydomain\.local dns:graylogelasticalias\.mydomain\.local dns:graylogelasticalias ip:192\.168\.100\.109 | PEM \(certificate\) PKCS\#8 \(key file\) |

## Graylog Stack Certificate Template

Defining a new certificate template will require elevated privileges in your Active Directory domain.

> Defining the new template is done through the ADCS management tool “Certification Authority”

1. Duplicate the default ADCS WebServer template, rename it to your liking.
2. General tab:
	- Set the name to something recognizable, for example “Graylog Stack Template”.
	- The software will automatically generate the internal name, which removes all spaces: “GraylogStackTemplate”.
3. Cryptography tab:
	- Provider is the Key Storage Provider
	- Requests can use any provider available on the subject’s computer is true
	- Algorithm is RSA 2048
	- Request hash is SHA256
	- Use alternate signature hash must be set to false.
4. Extensions tab:
	- Application policies is set to both server auth as well as client auth.
5. Request handling tab:
	>If you are going to be generating all the keypairs on your issuing CA or on another management station, then you will need to add the following as well, which will allow you to export the keypair for migration to the Graylog stack servers.
	- Allow the private key to be exported is set to Yes.

## Generating The Keypair and Certificates

### Preparation

The .INF input file for the certreq command would look similar to the following. Note that we are referring to the template by the internal name, which does not have whitespace!:

```
[Version]
signature="$Windows NT$"
[NewRequest]
Subject="CN=hostname5.mydomain.local"
HashAlgorithm=SHA256
Keyalgorithm=RSA
KeyLength=2048
Exportable=True
MachineKeySet=True
[RequestAttributes]
CertificateTemplate="GraylogStackTemplate"
[Extensions]
2.5.29.17="{text}"
_continue_="dns=hostname5&"
_continue_="dns=hostname5.mydomain.local&"
_continue_="dns=graylogreceiveralias.mydomain.local&"
_continue_="dns=graylogreceiveralias&"
_continue_="ipaddress=192.168.100.105&"
```

### Execution

Assuming that you’re generating the keypairs on your Windows administration station. If you’re generating the keypairs on the Graylog Linux hosts, then you will need to use different instructions.

For each of the .INF files that we built, we will run commands like the following (assuming that the files are all in D:secretsgraylog):

```cmd
> certreq -new D:\secrets\graylog\hostname5-graylogreceiver.inf D:\secrets\graylog\hostname5-graylogreceiver.req
> certreq -submit D:\secrets\graylog\hostname5-graylogreceiver.req
```

This gives you a request ID, for example “531”. Ask one of your PKI administrators to approve the request, for example:

```cmd
> certutil -resubmit 531
```

Afterwards you can continue:

```cmd
> certreq -retrieve 531 D:\secrets\graylog\hostname5-graylogreceiver.cer
> certreq -accept D:\secrets\graylog\hostname5-graylogreceiver.cer
```

What all of this does is:

- Generate a keypair by your specifications.
- Generate a CSR for the keypair.
- Submit the CSR to the issuing CA.
- Approve the CSR on the issuing CA.
- Export the signed certificate from the issuing CA.
- Import the signed certificate into your current server’s certificate store.

### Conversion

Need to convert everything we have right now, in order to make them usable.

**Warning: Once you have finished the setup of all keys and certificates on the Graylog stack, you must delete all the files we’ve put into D:secretsgraylog**

Use strong passwords on all PFX and PKCS files! Store these passwords safely, in a password vaulting application.

## CA Chain

Each application requires that you provide the CA chain of your PKI, for inclusion in its trust store. The following assumes that you have one root CA and one issuing CA and that you’ve put their respective certificates in D:secretsgraylog:

```cmd
> openssl x509 -in rootca.crt -outform pem -out D:\secrets\graylog\rootca.pem
> openssl x509 -in ca.crt -outform pem -out D:\secrets\graylog\ca.pem
> type D:\secrets\graylog\rootca.pem > D:\secrets\graylog\cachain.pem
> type D:\secrets\graylog\rootca.pem >> D:\secrets\graylog\cachain.pem
```

## MongoDB

For each of the keypairs we made we will need to repeat the following in Powershell (adjust all names accordingly):

	Get-ChildItem -Path cert:\\LocalMachine\My | Select-String hostname3
This will return metadata of the certificate for MongoDB on hostname3. You will need the thumbprint string, which will look similar to “5F98EBBFE735CDDAE00E33E0FD69050EF9220254”. Moving on:

```cmd
> $mypass = ConvertTo-SecureString -String "yoursafepassword" -Force -AsPlainText
> Get-ChildItem -Path cert:\\LocalMachine\My\5F98EBBFE735CDDAE00E33E0FD69050EF9220254 | Export-PfxCertificate -FilePath D:\secrets\graylog\hostname3-mongodb.pfx -Password $mypass
> openssl x509 -in D:\secrets\graylog\hostname3-mongodb.cer -outform pem -out D:\secrets\graylog\hostname3-mongodb.crt
> openssl pkcs12 -in D:\secrets\graylog\hostname3-mongodb.pfx -nocerts -out D:\secrets\graylog\hostname3-mongodb.key
> type D:\secrets\graylog\hostname3-mongodb.crt > D:\secrets\graylog\hostname3-mongodb.pem
> D:\secrets\graylog\hostname3-mongodb.key >> D:\secrets\graylog\hostname3-mongodb.pem
```

## Graylog and ElasticSearch

For each of the keypairs we made we will need to repeat the following in Powershell (adjust all names accordingly):

```cmd
> Get-ChildItem -Path cert:\\LocalMachine\My | Select-String hostname5
```

This will return metadata of the certificate for MongoDB on hostname5. You will need the thumbprint string, which will look similar to “5F98EBBFE735CDDAE00E33E0FD69050EF9220254”. Moving on:

```cmd
> $mypass = ConvertTo-SecureString -String "yoursafepassword" -Force -AsPlainText
> Get-ChildItem -Path cert:\\LocalMachine\My\5F98EBBFE735CDDAE00E33E0FD69050EF9220254 | Export-PfxCertificate -FilePath D:\secrets\graylog\hostname5-receiver.pfx -Password $mypass
> openssl x509 -in D:\secrets\graylog\hostname5-receiver.cer -outform pem -out D:\secrets\graylog\hostname5-receiver.crt
> openssl pkcs12 -in D:\secrets\graylog\hostname5-receiver.pfx -nocerts -out D:\secrets\graylog\hostname5-receiver.key
> openssl pkcs8 -in D:\secrets\graylog\hostname5-receiver.key -topk8 -out D:\secrets\graylog\hostname5-receiver.pem
> Finally, edit the CRT and PEM files to remove all extraneous metadata and whitespaces. There should be nothing before or after the === BEGIN and END === tags.
```

You may upload the PEM and CRT files to the relevant ElasticSearch or Graylog server, where you will need to do one final conversion: use dos2unix to convert the line endings from Windows-type to Linux-type.
