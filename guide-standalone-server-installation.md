# Signata MFA Server Installation Guide

## Minimum Requirements

At a minimum, you will need:

1. A server that you can install the Signata Standalone service on to.
2. A service account with read-only rights for your Active Directory.
3. An ADCS Enterprise-type PKI available in your network.

## Firewall Rules

The Signata Standalone server only requires a few rules to be configured to operate.

Purpose | Source | Destination | Port | Protocol
------- | ------ | ----------- | ---- | --------
LDAPS | Signata Server | Domain Controller | 636 | TCP
HTTPS | Signata Client(s) | Signata Server | 443 | TCP

Traffic from the Signata Server to the Enterprise Certificate Authority is via standard DCOM services, which are assumed to be open and available for connectivity within the same domain. Running Signata Standalone on a server in a different domain to the certificate authority is not recommended.

## Standalone Service Installation

1. Download and run the __Signata Enterprise Standalone.exe__ installer.

2. The installation wizard will appear. Click __Next__.

3. Click __Next__.

4. Click __Install__.

5. Click __Finish__.

6. Once the package has installed, the _Signata Enterprise Service_ will be running. Stop the service for now, as additional configuration is required before you can start it again.

## Service Account Creation

Signata Standalone requires a domain service account to operate. This account can simply be a member of Domain Users, just so it has enough privileges to be able to read user objects in your directory and to run the Signata Enterprise Service, but nothing more.

The name of the account is not important, but it can be useful to name it specifically to identify that it is for Signata Standalone (e.g. svc_signata@yourdomain.com).

Please ensure that the password for this service account does not contain any reserved JSON characters. This includes single quotes (‘), quotes (”), and backslashes (\).

(If you are forced to use a password containing these reserved characters, you will need to escape the characters when you edit the appsettings.json file in later steps. Contact Signata Support if you need assistance with escaping these characters correctly.)

Once you have created this service account, modify the _Signata Enterprise Service_ to Log On as the service account.

And finally modify the __C:\ProgramData\Signata\signata-enterprise.sqlite__ database file to allow Full control to the service account.

## IIS & Reverse Proxy Configuration

In it’s default configuration the Signata Standalone service runs on http://localhost:5000 – that is, it is only listening on the local network adapter on port 5000, and it is not TLS-enabled. It will not respond to any connection requests from other computers in your network.

It is recommended to configure a Reverse Proxy to sit in front of the Signata Standalone service, and this Reverse Proxy should be configured to allow in-bound connections from other servers, and have TLS enabled and enforced. It is not recommended to use the Signata Standalone service as the service that your clients will directly connect to, as it is using a Microsoft Kestrel web server [which is not recommended for direct connections by outside services](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel?view=aspnetcore-3.1#when-to-use-kestrel-with-a-reverse-proxy).

As Signata Standalone only works on Windows, it is easiest to use IIS as a reverse proxy as it can be enabled as a role on the server and configured as a reverse proxy with the addition of 2 modules provided by Microsoft.

### Enabling IIS

1. First, to enable IIS, open Server Manager and use the __Add Roles and Features Wizard__. Click __Next__.

### Installing Reverse Proxy Modules

### Configuring the Reverse Proxy

## Certificate Template Configuration

### Enrollment Agent Configuration

### End User Certificate Templates

#### 9A Authentication Key

#### 9C Signing Key

#### 9D Encryption Key

#### 9E Card Authentication Key

## Signata Standalone Service Configuration

### Directory Configuration

### Certificate Authority Configuration

### API Key Configuration

### Product Licence

## Post Configuration
