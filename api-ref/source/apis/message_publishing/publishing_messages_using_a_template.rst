:original_name: smn_api_54003.html

.. _smn_api_54003:

Publishing Messages Using a Template
====================================

Description
-----------

-  API name

   Publish

-  Function

   Use the message template to publish a message to a topic. After the message ID is returned, the message has been saved and is to be pushed to the subscribers of the topic. This API allows you to send messages to different types of subscribers using the same template name but different protocols.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/topics/{topic_urn}/publish

-  Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                         |
   +=================+=================+=================+=====================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                          |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of the topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type               | Description                                                                                                                                                                                                                                                                                                                                                                                  |
   +=======================+=================+====================+==============================================================================================================================================================================================================================================================================================================================================================================================+
   | subject               | No              | String             | Message subject, which is presented as the email subject when SMN sends messages to email subscribers                                                                                                                                                                                                                                                                                        |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    | The message subject cannot exceed 512 bytes.                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_template_name | Yes             | String             | Message template name, which can be obtained by referring to :ref:`Querying Message Templates <smn_api_53004>`                                                                                                                                                                                                                                                                               |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    | .. note::                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    |    Three message formats are supported:                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    |    -  message                                                                                                                                                                                                                                                                                                                                                                                |
   |                       |                 |                    |    -  message_structure                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                 |                    |    -  message_template_name                                                                                                                                                                                                                                                                                                                                                                  |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    |    If the three formats are specified at the same time, they take effect in the following sequence:                                                                                                                                                                                                                                                                                          |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    |    message_structure>message_template_name>message                                                                                                                                                                                                                                                                                                                                           |
   +-----------------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | Map<String,String> | Variable parameters and values **Tags** cannot be left blank. This parameter is mandatory when you use a message template to publish messages. The key in the dictionary is the parameter name in the message template and can contain a maximum of 21 characters. The value in the dictionary is the value after the key in the message template is replaced. The value cannot exceed 1 KB. |
   +-----------------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_to_live          | No              | String             | The maximum retention period of a message in SMN                                                                                                                                                                                                                                                                                                                                             |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    | After the retention period expires, SMN does not send this message.                                                                                                                                                                                                                                                                                                                          |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    | Unit: second                                                                                                                                                                                                                                                                                                                                                                                 |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    | Default retention period: **3600** (one hour)                                                                                                                                                                                                                                                                                                                                                |
   |                       |                 |                    |                                                                                                                                                                                                                                                                                                                                                                                              |
   |                       |                 |                    | The retention period must be a positive integer less than or equal to 604,800 (3600 x 24 x 7).                                                                                                                                                                                                                                                                                               |
   +-----------------------+-----------------+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId: f96188c7ccaf4ffba0c9aa149ab2bd57:test_create_topic_v2/publish

   .. code-block::

      {
          "subject": "test message template v2",
          "message_template_name": "confirm_message",
          "time_to_live": "3600",
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

-  Example response

   .. code-block::

      {
          "message_id": "bf94b63a5dfb475994d3ac34664e24f2",
          "request_id": "9974c07f6d554a6d827956acbeb4be5f"
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
