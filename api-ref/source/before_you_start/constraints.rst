:original_name: iam_01_0005.html

.. _iam_01_0005:

Constraints
===========

All APIs of IAM can be called using the global region endpoint. Some APIs can be called using endpoints of both the global region and other regions (see :ref:`Table 1 <iam_01_0005__table299045612116>`), and other APIs can be called using only the global region endpoint.

.. note::

   Tokens or temporary AKs/SKs obtained using domain names of all regions except the global region can only be used to access services in the same region.

.. _iam_01_0005__table299045612116:

.. table:: **Table 1** Global and region-specific APIs

   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Category                                     | API URI                                                                        | Link                                                                                        |
   +==============================================+================================================================================+=============================================================================================+
   | Token Management                             | POST /v3/auth/tokens                                                           | :ref:`Obtaining a User Token <en-us_topic_0057845583>`                                      |
   |                                              |                                                                                |                                                                                             |
   |                                              |                                                                                | :ref:`Obtaining an Agency Token <en-us_topic_0064274720>`                                   |
   |                                              |                                                                                |                                                                                             |
   |                                              |                                                                                | :ref:`Obtaining a Scoped Token <iam_13_0604>`                                               |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | GET /v3/auth/tokens                                                            | :ref:`Verifying a Token and Returning a Valid Token <en-us_topic_0057845585>`               |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Access Key Management                        | POST /v3.0/OS-CREDENTIAL/securitytokens                                        | :ref:`Obtaining a Temporary AK/SK <en-us_topic_0097949518>`                                 |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Services and Endpoints                       | GET /v3/services{?type}                                                        | :ref:`Querying Services <en-us_topic_0057845587>`                                           |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | GET /v3/endpoints{? interface, service_id}                                     | :ref:`Querying Endpoints <en-us_topic_0057845562>`                                          |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Version Information Management               | GET /                                                                          | :ref:`Querying Keystone API Version Information <en-us_topic_0057845569>`                   |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | GET /v3                                                                        | :ref:`Querying Information About Keystone API Version 3.0 <en-us_topic_0057845613>`         |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Project Management                           | GET /v3/auth/projects                                                          | :ref:`Querying the List of Projects Accessible to Users <en-us_topic_0057845558>`           |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Tenant Management                            | GET /v3/auth/domains                                                           | :ref:`Querying the List of Domains Accessible to Users <en-us_topic_0057845574>`            |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Federated Identity Authentication Management | GET /v3/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}/auth | :ref:`Obtaining an Unscoped Token (SP Initiated) <en-us_topic_0057845629>`                  |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | POST /v3.0/OS-FEDERATION/tokens                                                | :ref:`IdP Initiated <iam_02_0002>`                                                          |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | GET /v3/OS-FEDERATION/projects                                                 | :ref:`Querying the List of Projects Accessible to Federated Users <en-us_topic_0057845595>` |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | GET /v3/OS-FEDERATION/domains                                                  | :ref:`Querying the List of Domains Accessible to Federated Users <en-us_topic_0057845596>`  |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   |                                              | GET /v3-ext/auth/OS-FEDERATION/SSO/metadata                                    | :ref:`Querying the Metadata File of Keystone <en-us_topic_0057845577>`                      |
   +----------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
