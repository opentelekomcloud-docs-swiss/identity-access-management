:original_name: en-us_topic_0057845580.html

.. _en-us_topic_0057845580:

Processing WebSSO Assertion Requests
====================================

Function
--------

This API is used to receive the response message (that is, the assertion request sent by the IdP to the SP) of the AuthnRequest request when the IAM service serves as the service provider (SP) in SAML 2.0 specifications and when the SP and Identity Provider (IdP) implement the single sign-on (SSO).

For the SAML 2.0 specification, see https://en.wikipedia.org/wiki/SAML_2.0.

.. note::

   You are not advised to obtain a token by directly calling this API. You are advised to obtain a token using OpenStackClient.

URI
---

POST /v3-ext/auth/OS-FEDERATION/SSO/SAML2/POST
