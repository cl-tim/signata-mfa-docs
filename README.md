# Signata MFA Documentation

This repository will store all documentation for the Signata MFA product.

You can access Signata MFA here: [https://mfa.signata.net/](https://mfa.signata.net/)

You can also access support here: [https://congruentlabs.atlassian.net/servicedesk/customer/portal/2](https://congruentlabs.atlassian.net/servicedesk/customer/portal/2)

## Signata MFA: Standalone

Signata MFA: Standalone Edition is a product that allows the issuance of PKI certificates onto YubiKeys for users within your network. Because Signata Standalone leverages existing services within your network, additional steps are required to be completed to ensure your network is ready for integration. This document details these steps, and it is recommended that this entire document is reviewed before attempting to integrate Signata Standalone, as you may be delayed in getting some pre-requisites configured first.

Some of the pre-requisites include:

* Access to an Active Directory Domain Services (ADDS) server that Signata can connect to read identity information for your users.
* Access to an Active Directory Certificate Services (ADCS) server that Signata can connect to for requesting certificates.
* Modification/Configuration of Certificate Templates for Signata to be able to request certificates for users.
* A server within your network that the Signata service can be installed on to, and IIS also enabled for use as a reverse proxy.

This documentation aims to provide guidance for configuration of the services in the most simple and optimal manner.
