:original_name: smn_api_53001.html

.. _smn_api_53001:

Creating a Message Template
===========================

Function
--------

Create a message template for quick message sending to reduce the request data volumes.

By default, a user can create a maximum of 100 message templates. However, in a high-concurrency scenario, which is rare, extra templates may be successfully created.

Message templates are grouped by message name. You can create templates of different protocols using the same template name. You must create a **Default** template with the same name as each custom template. The **Default** template is used when no specific template has been set for a given protocol. If a template is configured for a specific protocol, any subscriber who chose that protocol during subscription will receive messages using that specific template. If you create a custom template but do not create a default template with the same name, you cannot use the custom template to publish messages.

URI
---

POST /v2/{project_id}/notifications/message_template

For details, see :ref:`Table 1 <smn_api_53001__table66376860193738>`.

.. _smn_api_53001__table66376860193738:

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID.                                        |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

:ref:`Table 2 <smn_api_53001__table14955048193738>` describes the request parameters.

.. _smn_api_53001__table14955048193738:

.. table:: **Table 2** Request parameters

   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                     |
   +=======================+=================+=================+=================================================================================================================================+
   | message_template_name | Yes             | String          | Template name.                                                                                                                  |
   |                       |                 |                 |                                                                                                                                 |
   |                       |                 |                 | Enter 1 to 64 characters, and start with a letter or digit. Only letters, digits, hyphens (-), and underscores (_) are allowed. |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | content               | Yes             | String          | Template content, which currently supports plain text only.                                                                     |
   |                       |                 |                 |                                                                                                                                 |
   |                       |                 |                 | The template content cannot be left blank or larger than 256 KB.                                                                |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | No              | String          | Protocol supported by the template.                                                                                             |
   |                       |                 |                 |                                                                                                                                 |
   |                       |                 |                 | Currently, the following protocols are supported:                                                                               |
   |                       |                 |                 |                                                                                                                                 |
   |                       |                 |                 | -  **email**                                                                                                                    |
   |                       |                 |                 | -  **default**                                                                                                                  |
   |                       |                 |                 | -  **sms**                                                                                                                      |
   |                       |                 |                 | -  **http** and **https**                                                                                                       |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 3 <smn_api_53001__table59861740193738>` describes the response parameters.

.. _smn_api_53001__table59861740193738:

.. table:: **Table 3** Response parameters

   +---------------------+--------+-------------------------------------------------+
   | Parameter           | Type   | Description                                     |
   +=====================+========+=================================================+
   | request_id          | String | The unique request ID.                          |
   +---------------------+--------+-------------------------------------------------+
   | message_template_id | String | The unique resource identifier of the template. |
   +---------------------+--------+-------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template

.. code-block::

   {
       "message_template_name": "confirm_message",
       "protocol": "https",
       "content": "(1/2)You are invited to subscribe to topic({topic_id}). Click the following URL to confirm subscription:(If you do not want to subscribe to this topic, ignore this message.)"
   }

Example Response
----------------

.. code-block::

   {
       "request_id": "ca03efa691624d8eb2dfeba01a1bcf6e",
       "message_template_id": "57ba8dcecda844878c5dd5815b65d10f"
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
