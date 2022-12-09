:original_name: smn_api_53005.html

.. _smn_api_53005:

Querying the Message Template Details
=====================================

Description
-----------

-  API name

   QueryMessageTemplateDetail

-  Function

   Query the template details, including the template content.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/message_template/{message_template_id}

-  Parameter description

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                      |
   +=====================+=================+=================+==================================================================================================================+
   | project_id          | Yes             | String          | Project ID                                                                                                       |
   |                     |                 |                 |                                                                                                                  |
   |                     |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                               |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | message_template_id | Yes             | String          | Unique resource ID of a topic. You can obtain it according to :ref:`Querying Message Templates <smn_api_53004>`. |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+

Request
-------

Example request

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template/57ba8dcecda844878c5dd5815b65d10f

Response
--------

-  Parameter description

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================+
   | message_template_id   | String                | Template ID                                                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_template_name | String                | Template name                                                                                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | String                | Protocol supported by the template                                                                                                                        |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | Currently, the following protocols are supported:                                                                                                         |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | -  **email**                                                                                                                                              |
   |                       |                       | -  **default**                                                                                                                                            |
   |                       |                       | -  **sms**                                                                                                                                                |
   |                       |                       | -  **dms**                                                                                                                                                |
   |                       |                       | -  **http** and **https**                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag_names             | String                | Variable list                                                                                                                                             |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | The variable name will be quoted in braces ({}) in the template. When you use a template to send messages, you can replace the variable with any content. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Time when the template was created                                                                                                                        |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | The UTC time is in *YYYY-MM-DDTHH:MM:SSZ* format.                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Last time when the template was updated                                                                                                                   |
   |                       |                       |                                                                                                                                                           |
   |                       |                       | The UTC time is in *YYYY-MM-DDTHH:MM:SSZ* format.                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content               | String                | Template content                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | request_id            | String                | Request ID, which is unique                                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "message_template_name": "confirm_message",
          "protocol": "https",
          "update_time": "2016-08-02T08:22:25Z",
          "create_time": "2016-08-02T08:22:20Z",
          "request_id":"ba79ca8f794f4f50985ce7b98a401b47",
          "tag_names": [
              "topic_id_id4"
          ],
          "content": "(1/24)You are invited to subscribe to topic({topic_id_id4}). Click the following URL to confirm subscription:(If you do not want to subscribe to this topic, ignore this message.)",
          "message_template_id": "57ba8dcecda844878c5dd5815b65d10f"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
