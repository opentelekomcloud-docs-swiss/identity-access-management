:original_name: en-us_topic_0057845611.html

.. _en-us_topic_0057845611:

Modifying User Information
==========================

Function
--------

This API is used to modify user information under a domain.

URI
---

-  URI format

   PATCH /v3/users/{user_id}

-  URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   Yes       String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.               |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Parameters in the request body

   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                        |
   +====================+=================+=================+====================================================================================================================================================================================+
   | name               | No              | String          | A username with 5 to 32 characters. The username can contain special characters, but only hyphens (-), underscores (_), and periods (.) are allowed. It cannot start with a digit. |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id          | No              | String          | ID of the domain where a user is located.                                                                                                                                          |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enabled            | No              | Boolean         | Enabling status of the user. **true** indicates that the user is enabled. **false** indicates that the user is disabled. The default value is **true**.                            |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password           | No              | String          | User password after the change. The password must meet the following requirements:                                                                                                 |
   |                    |                 |                 |                                                                                                                                                                                    |
   |                    |                 |                 | -  Can contain 6 to 32 characters. The system default minimum password length is 6 characters, and you can change the minimum password length.                                     |
   |                    |                 |                 | -  Must contain at least two of the following character types: uppercase letters, lowercase letters, digits, and special characters.                                               |
   |                    |                 |                 | -  Cannot be the username or the username spelled backwards.                                                                                                                       |
   |                    |                 |                 | -  Cannot contain the user's mobile phone number or email address.                                                                                                                 |
   |                    |                 |                 | -  Must comply with the password policies under **Account Settings**.                                                                                                              |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_project_id | No              | String          | Default project ID of a user.                                                                                                                                                      |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description        | No              | String          | Description of the user.                                                                                                                                                           |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      1. Create the temporary file ${filename}.json based on the following template. ${filename} indicates the temporary file name, which is user-defined.
      {
          "user": {
              "name": "james1234",
              "default_project_id": "88b16b6440684467b8825d7d96e154d8",
              "enabled": false,
              "password": "********"
          }
      }
      2. Run the following command under the directory storing the ${filename}.json file.
      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X POST -d @${filename}.json https://sample.domain.com/v3/users/2c1c6c54e59141b889c99e6fada5f19f
      3. Run the following command under the directory of the ${filename}.json file to delete the ${filename}.json file.
      rm ${filename}.json

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== ============
   Parameter Mandatory Type        Description
   ========= ========= =========== ============
   user      Yes       JSON object User object.
   ========= ========= =========== ============

-  Description for the user format

   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type        | Description                                                                                                                                                                               |
   +=====================+===========+=============+===========================================================================================================================================================================================+
   | enabled             | Yes       | Boolean     | Whether a user is enabled. The value can be **true** or **false**. **true** indicates the user is enabled and **false** indicates the user is not enabled. The default value is **true**. |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                  | Yes       | String      | User ID.                                                                                                                                                                                  |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id           | Yes       | String      | ID of the domain where a user is located.                                                                                                                                                 |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                | Yes       | String      | Username.                                                                                                                                                                                 |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links               | Yes       | JSON object | User resource link.                                                                                                                                                                       |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description         | Yes       | String      | Description of the user.                                                                                                                                                                  |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_project_id  | No        | String      | Default project ID of a user.                                                                                                                                                             |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password_expires_at | Yes       | String      | UTC when the password will expire. **null** indicates that the password will not expire.                                                                                                  |
   +---------------------+-----------+-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "user": {
              "name": "james1234",
              "links": {
                  "self": "https://sample.domain.com/v3/users/6d8b04e3bf99445b8f76300903e5bf32"
              },
              "description": {
              },
              "domain_id": "88b16b6440684467b8825d7d96e154d8",
              "enabled": false,
              "id": "6d8b04e3bf99445b8f76300903e5bf32",
              "default_project_id": "88b16b6440684467b8825d7d96e154d8",
              "password_expires_at": "2016-12-07T00:00:00.000000Z"
          }
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 200         | The request is successful.                                                     |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                        |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 409         | A resource conflict occurs.                                                    |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
