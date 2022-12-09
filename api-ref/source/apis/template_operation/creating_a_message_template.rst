:original_name: smn_api_53001.html

.. _smn_api_53001:

Creating a Message Template
===========================

Description
-----------

-  API name

   CreateMessageTemplate

-  Function

   Create a message template for quick message sending to reduce the request data volume.

   By default, a user can create a maximum of 100 message templates. However, in a high-concurrency scenario, which is rare, extra templates may be successfully created.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/message_template

-  Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                         |
   +=======================+=================+=================+=====================================================================================================================================================================================+
   | message_template_name | Yes             | String          | Template name                                                                                                                                                                       |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | The template name is a string of 1 to 64 characters. It must contain upper- or lower-case letters, digits, hyphens (-), and underscores (_), and must start with a letter or digit. |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content               | Yes             | String          | Template content, which currently supports plain text only                                                                                                                          |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | The template content cannot be left blank or larger than 256 KB.                                                                                                                    |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | No              | String          | Protocol supported by the template                                                                                                                                                  |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | Currently, the following protocols are supported:                                                                                                                                   |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | -  **email**                                                                                                                                                                        |
   |                       |                 |                 | -  **default**                                                                                                                                                                      |
   |                       |                 |                 | -  **sms**                                                                                                                                                                          |
   |                       |                 |                 | -  **dms**                                                                                                                                                                          |
   |                       |                 |                 | -  **http** and **https**                                                                                                                                                           |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template

   .. code-block::

      {
          "message_template_name": "confirm_message",
          "protocol": "https",
          "content": "(1/2)You are invited to subscribe to topic({topic_id}). Click the following URL to confirm subscription:(If you do not want to subscribe to this topic, ignore this message.)"
      }

Response
--------

-  Parameter description

   +---------------------+--------+------------------------------------------------------+
   | Parameter           | Type   | Description                                          |
   +=====================+========+======================================================+
   | request_id          | String | Request ID, which is unique                          |
   +---------------------+--------+------------------------------------------------------+
   | message_template_id | String | Resource identifier of the template, which is unique |
   +---------------------+--------+------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "request_id":"ca03efa691624d8eb2dfeba01a1bcf6e",
          "message_template_id":"57ba8dcecda844878c5dd5815b65d10f"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
