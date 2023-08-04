:original_name: iam_08_0010.html

.. _iam_08_0010:

Modifying User Information (Including Email Address and Mobile Number) as an IAM User
=====================================================================================

Function
--------

This API is provided for IAM users to modify their information.

URI
---

PUT /v3.0/OS-USER/users/{user_id}/info

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | User token.                                           |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Parameters in the request body

   .. table:: **Table 1** Parameters in the request body

      +-------------------------------------------------+-----------+--------+-----------------------+
      | Parameter                                       | Mandatory | Type   | Description           |
      +=================================================+===========+========+=======================+
      | :ref:`user <iam_08_0010__table166351821151616>` | Yes       | Object | IAM user information. |
      +-------------------------------------------------+-----------+--------+-----------------------+

   .. _iam_08_0010__table166351821151616:

   .. table:: **Table 2** user

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                     |
      +=================+=================+=================+=================================================================+
      | email           | No              | String          | Email address with a maximum of 255 characters.                 |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
      | phone           | No              | String          | Mobile number with a maximum of 32 digits.                      |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | To change the mobile number, you must specify the country code. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
      | areacode        | No              | String          | Country code.                                                   |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | This parameter is mandatory if the mobile number is changed.    |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+

-  Example request

   -  Create a temporary file named *${filename}*\ **.json** using the following content format:

      .. code-block::

         {
             "user": {
                 "areacode": "0001",
                 "phone": "1234567890",
                 "email": "abcdefg@123.com"
             }
         }

   -  Run the following command under the directory storing the *${filename}*.\ **json** file:

      .. code-block::

         curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X PUT -d @${filename}.json https://sample.domain.com/v3.0/OS-USER/users/0638848aa7801dbe1f01c01e92b95df7/info

   -  Run the following command to delete the *${filename}*\ **.json** file:

      .. code-block::

         rm ${filename}.json

Response Parameters
-------------------

None

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 204         | The user information is modified successfully.                                 |
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
