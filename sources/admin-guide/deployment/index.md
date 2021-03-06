# Supported Operating Systems
We currently publish packages for the following **64-bit** operating
systems:

### Community Edition (CE) 
The Gluu Server CE is the full stack of Gluu components distributed in a
`chroot` container. CE is suitable for single server deployments of the
Gluu Server where high availability and elastic scalability are not core
requirements.

- [Centos](./centos.md)
- [Ubuntu](./ubuntu.md)
- [RHEL](./rhel.md)

### Enterprise Edition (EE)
The Gluu Server EE is functionally equivalent to CE, but each component
is packaged in its own `docker` container. EE includes a [web
application](http://www.gluu.org/docs-cluster/admin-guide/webui/) that
enables an organization to deploy a highly available and elastic
infrastructure of Gluu Servers across multiple cloud providers. EE is
divided into two packages identified as "master" and "consumer". The
"master" package is offered free and the "consumer" package requires a
commercial license. If you'd like to discuss our enterprise offerings,
please [schedule a meeting with us](http://gluu.org/booking).

- [Ubuntu](http://www.gluu.org/docs-cluster/admin-guide/installation/)

*Note:* 32-bit operating systems are **not supported** for any Gluu
Server distributions.

# Hardware Requirements

The Gluu Server is very flexible, and can be used for a wide array of
access management requirements. Depending on the size of your data, and
the number of concurrent transactions you want to support, you may need
more or less memory or CPU capacity.

### Community Edition

If you are running all the Gluu Server services on the same server (i.e.
SAML, OAuth2, LDAP), you will need at least:

- 2 CPU units
- 4GB of RAM
- 40GB of disk space

Not enough memory may produce some really weird bugs. From there, you
may need to adjust the resources based on your specific requirements.

### Enterprise Edition

- 2 CPU Units
- 8 GB of RAM
- 40 GB of disk space

# Java
The Gluu Server components have been tested with OpenJDK version 1.7 or
later.

# LDAP
The Gluu Server uses LDAP for persistence to store oxTrust and oxAuth
data, and to cache user entries.  The Gluu Server packages include "Gluu
OpenDJ", which is our
[fork](https://github.com/GluuFederation/gluu-opendj) of OpenDJ 2.6.0,
the last open source release by Forgerock. It is possible to use any
LDAP server, as long as you have the schema and security under control.

We publish the [latest
schema](https://github.com/GluuFederation/community-edition-setup/tree/master/static)
in our community-edition-setup project. The schema that we publish for
Gluu OpenDJ should also work for Forgerock OpenDJ, UnboundID LDAP
server, and Oracle Directory Server Enterprise Edition (ODSEE).

# Licenses
All software used in the Gluu Server is free to use in production. All
software developed by Gluu, including oxTrust and oxAuth, are held under
an MIT License. Visit
[licenses](../../admin-guide/introduction/index.md#licenses) to learn
more about the various licenses in use.

# Available Components

When you deploy the Gluu Server, you will have the opportunity to
specify which of the following software you want to use on your
server:

- __oxAuth:*__ oxAuth provides endpoints for an OpenID Connect Identity
  Provider (IdP) and an UMA Authorization Server (AS). Both OpenID
  Connect and UMA are standard profiles of OAuth 2.0, used for single
  sign-on (SSO) and web and API access management, respectively.
- __oxTrust:*__ oxTrust is the graphical user interface that is used for
  server management.
  __LDAP:*__ The Gluu Server ships with a fork of the OpenDJ LDAP server.
  It is used to store attributes and server configurations locally.
- __Apache 2 web server:*__ Apache 2 serves the web server for the Gluu
  Server. Without Apache 2, it is not possible to see the hostname from 
  a browser.
- **Shibboleth 2 SAML IDP:** The Shibboleth server provides endpoints
  for a SAML Identity Provider (IdP). If you want to create single
  sign-on (SSO) to a SAML SP, you will need a SAML IdP.
- **Asimba SAML Proxy:** The Asimba SAML proxy should be deployed on if
  your organization needs to consolidate inbound SAML authentication
  from the IdPs of partners to a single website or app.
- **CAS:** CAS is legacy at this point and should only be deployed if
  your organization has existing apps that can only support CAS for
  single sign-on.
- **oxAuth RP:** The oxAuth RP is a web UI to enable OpenID Connect
  discovery, dynamic client registration, and authentication testing.
  For more information, please check our [OpenID Connect
  docs](../openid-connect/index.md).

*__Note:__* * implies that the software should *always* be deployed.

# Troubleshooting
Please see our [Cloud Deployment FAQ](../../faq/cloud-faq.md) for cloud
specific notes and our [Troubleshooting
FAQ](../../faq/troubleshooting.md) for solutions to common issues.

# Support
Gluu offers both community and VIP support. Anyone can browse and open
tickets on our [support portal](http://support.gluu.org). For private
support, expedited assistance, and strategic consultations, please view
[our pricing](http://gluu.org/pricing) and [schedule a meeting with
us](http://gluu.org/booking) to discuss VIP support options.

