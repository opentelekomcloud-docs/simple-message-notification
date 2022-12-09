:original_name: smn_api_54001.html

.. _smn_api_54001:

Publishing Messages in the Text Format
======================================

Description
-----------

-  API name

   Publish

-  Function

   Publish messages in the text format to a topic. After the message ID is returned, the message has been saved and is to be pushed to the subscribers of the topic.

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================+
   | subject         | Yes             | String          | Message subject, which is used as the email subject when you publish email messages. The value cannot exceed 512 characters.                                                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message         | Yes             | String          | Message content                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                    |
   |                 |                 |                 | The message content is a UTF-8-coded character string of no more than 256 KB. For SMS subscribers, if the content exceeds 256 bytes, the system will divide it into multiple messages and send only the first two. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_to_live    | No              | String          | Time-to-live (TTL) of a message, specifically, the maximum time period for retaining the message in the system                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                    |
   |                 |                 |                 | If the period expires, the system will discard the message. The time period is measured in seconds, and the default TTL is **3600s** (one hour).                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                    |
   |                 |                 |                 | The value must be a positive integer less than or equal to 604,800 (3600 x 24 x 7).                                                                                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId: f96188c7ccaf4ffba0c9aa149ab2bd57:test_create_topic_v2/publish

   .. code-block::

      {
          "subject": "test message v2",
          "message": "Message test message v2",
          "time_to_live":"3600"
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

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
