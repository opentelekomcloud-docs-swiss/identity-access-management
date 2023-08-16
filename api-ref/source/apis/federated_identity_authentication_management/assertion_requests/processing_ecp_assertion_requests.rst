:original_name: en-us_topic_0057845614.html

.. _en-us_topic_0057845614:

Processing ECP Assertion Requests
=================================

Function
--------

This API is used to receive the response to AuthnRequest when an IAM service (functioning as a service provider specified in the SAM L2.0 specification) performs SSO login in an identity provider. AuthnRequest refers to the assertion request sent from the ECP to the service provider.

For the SAML 2.0 specification, see https://en.wikipedia.org/wiki/SAML_2.0.

.. note::

   You are not advised to obtain a token by directly calling this API. You are advised to obtain a token using OpenStackClient.

URI
---

POST /v3-ext/auth/OS-FEDERATION/SSO/SAML2/ECP
