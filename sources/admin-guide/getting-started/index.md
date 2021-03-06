# Getting Started

This document will show you how to get up and running with the Gluu
Server. It is broken down into the following sections:

- [Overview](#overview)
- [Deployment](#deployment)
- [Identity Management](#identity-management)
- [Single Sign-on](#single-sign-on-sso)
- [Person Authentication](#person-authentication)
- [Web & API Access Management](#web--api-access-management)

## Overview
The Gluu Server is an identity and access management suite comprised of
free open source software (FOSS) components. Some of the software was
written by Gluu (everything with an "ox" prefix, like "oxAuth"), and
some of the software we forked from existing open source projects like
the Shibboleth SAML identity provider, Forgerock community release of
OpenDJ, the Asimba SAML proxy, the CAS authentication server and many
more components that are part of the Linux distributions. Learn more
about each of the open source licenses in use
[here](../introduction/index.md#licenses).

The full suite of software is distributed as Linux packages that support
either single server or clustered deployments. In order to achieve a
highly available, clustered Gluu Server infrastructure, you'll need a
commercial license for the Gluu Server Enterprise Edition (EE). More
information about that is covered below in the [Deployment
Models](#deployment-models).

## Deployment
The Gluu Server can be deployed on any physical or virtual server. Both
distributions of the Gluu Server--Community Edition and Enterprise
Edition--are distributed as containers. The Community Edition uses
`chroot` containers, while the Enterprise Edition uses `docker`
containers. Container distribution enables Gluu to make sure that all
the pieces are working together. If you actually had to integrate all
the components of the Gluu Server together, it would take you a long
time.

[View the Gluu Server deployment guide](../deployment/index.md)

#### Deployment Models:
**Community Edition (CE):** All single server deployments of the Gluu
Server can be deployed in production with an unlimited number of users
for free. Community support is available on our [public
forum](http://support.gluu.org), or you can purchase [Basic
Support](http://gluu.org/pricing) to open private tickets and enlist
security and support consultations with Gluu engineers.

**Enterprise Edition (EE):** Gluu Enterprise Edition promises scalability,
reliability and a fail-over mechanism through its innovative design
implemented using Docker. The cluster server can also call a DOS
service, like DOSarrest, enabling protection from distributed denial of
service attacks. Because the Enteprise Edition introduces new
operational complexities, we recommend getting familiar with [Community
Edition](../deployment/index.md) before making the leap to Enterprise
Edition.

The Gluu Server Enterprise Edition is divided into two packages
identified as "master" and "consumer". The "master" package is offered
for free, and the "consumer" package requires a commercial license.
Learn more in our [EE docs](http://gluu.org/docs-cluster).

## Identity Management

To keep the Gluu Server up-to-date with the latest user information
(a.k.a. attributes or claims), your organization can either "push" or
"pull" identity data. In the "pull" mode, otherwise known as [LDAP
Synchronization or Cache
Refresh](../../admin-guide/cache-refresh/index.md), the Gluu Server can
use an existing LDAP identity source like Microsoft Active Directory as
the authoritative source of identity information. If you "push"
identities to the Gluu Server, you can use the JSON/REST SCIM 1.1 or 2.0
API.

[Local user management](../user-management/index.md#local-user-management) 
can also be performed inside the Gluu Server management interface.

## Single Sign-On (SSO)
Now it is time to connect your endpoints, portals or websites with your
Gluu Server. The Gluu Server stack includes both a
[SAML](../saml/index.md) and an [OpenID Connect Identity
Provider](../openid-connect/index.md) which can be configured for single
sign-on to any SAML 2.0 or OpenID Connect protected application.

Here are a couple of how-to's for creating SSO to popular applications:

- [Using SAML to get SSO with Google Apps](../../articles/google-saml.md)
- [Using SAML to get SSO with Salesforce.com](../../articles/salesforce-sso.md)

## Person Authentication
Correctly identifying people--authentication--is fundamental to web and
mobile security. Using the oxTrust web User Interface (UI), you can
configure built-in or custom business logic for authentication.

#### Basic Authentication
Passwords do not mitigate a lot of risk, but for many organizations, it
is still the place to start. With the Gluu Server you can use either an
existing LDAP V3 repository like Active Directory, or you can use the
embedded Gluu Server OpenDJ server to store passwords. `Basic` is the
[default](../configuration/index.md#manage-authentication)
authentication mechanism shipped with every Gluu Server.

#### Custom Authentication
`Custom Authentication` enables an organization to utilize [interception
scripts](../../reference/interception-scripts/index.md#overview) to
achieve advanced levels of authentication. Using authentication
interception scripts, your organization can call third-party APIs to
enable multi-factor authentication (MFA), intrusion detection systems,
or make use of multiple backend servers for authentication.

The Gluu Server currently ships with support for the FIDO U2F standard.
Instructions for adding additional strong authentication mechanisms can
be found
[here](../../reference/interception-scripts/index.md#authentication).

## Web & API Access Management
The Gluu Server includes an [UMA Authorization Server
(AS)](../uma/index.md) that can be used to enforce policies for access
to any API or web resource. UMA is a profile of OAuth2 that is
complimentary to OpenID Connect. UMA defines RESTful, JSON-based,
standardized flows and constructs for access management.
