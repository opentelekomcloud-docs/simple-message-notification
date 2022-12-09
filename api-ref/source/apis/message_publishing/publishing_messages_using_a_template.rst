:original_name: smn_api_54003.html

.. _smn_api_54003:

Publishing Messages Using a Template
====================================

Description
-----------

-  API name

   Publish

-  Function

   Use the message template to publish a message to a topic. After the message ID is returned, the message has been saved and is to be pushed to the subscribers of the topic. This API allows you to send messages to different types of subscribers using different template protocols with the same name.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/topics/{topic_urn}/publish

-  Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                           |
   +=================+=================+=================+=======================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                            |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it according to :ref:`Querying Topics <smn_api_51004>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------------+-----------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                | Description                                                                                                                                      |
   +=======================+=================+=====================+==================================================================================================================================================+
   | subject               | Yes             | String              | Message subject, which is presented as the email subject when SMN sends massages to email subscribers                                            |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     | The message subject cannot exceed 512 bytes.                                                                                                     |
   +-----------------------+-----------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_template_name | Yes             | String              | Message template name, which can be obtained according to :ref:`Querying Message Templates <smn_api_53004>`                                      |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     | .. note::                                                                                                                                        |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     |    Three message formats are supported:                                                                                                          |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     |    -  message                                                                                                                                    |
   |                       |                 |                     |    -  message_structure                                                                                                                          |
   |                       |                 |                     |    -  message_template_name                                                                                                                      |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     |    If the three formats are specified at the same time, they take effect in the following sequence:                                              |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     |    message_structure>message_template_name>message                                                                                               |
   +-----------------------+-----------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Yes             | JSON key-value pair | Variable parameters and values                                                                                                                   |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     | The value cannot be left blank.                                                                                                                  |
   +-----------------------+-----------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_to_live          | No              | String              | TTL of a message, specifically, the maximum time period for retaining the message in the system                                                  |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     | If the period expires, the system will discard the message. The time period is measured in seconds, and the default TTL is **3600s** (one hour). |
   |                       |                 |                     |                                                                                                                                                  |
   |                       |                 |                     | The value must be a positive integer less than or equal to 604,800 (3600 x 24 x 7).                                                              |
   +-----------------------+-----------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId: f96188c7ccaf4ffba0c9aa149ab2bd57:test_create_topic_v2/publish

   .. code-block::

      {
          "subject": "test message template v2",
          "message_template_name": "confirm_message",
          "time_to_live":"3600",
          "tags": {
              "topic_urn": "topic_urn3331",
              "topic_id": "topic_id3332"
          }
      }

Response
--------

-  Parameter description

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   message_id String Message ID, which is unique
   ========== ====== ===========================

-  Response example

   .. code-block::

      {
          "message_id": "bf94b63a5dfb475994d3ac34664e24f2",
          "request_id": "9974c07f6d554a6d827956acbeb4be5f"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
