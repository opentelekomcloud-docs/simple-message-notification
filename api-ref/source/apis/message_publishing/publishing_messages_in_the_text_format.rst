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

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================================+
   | subject         | No              | String          | Message subject, which is used as the email subject when you publish email messages. The subject cannot exceed 512 characters.                                                                                              |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message         | Yes             | String          | Message content                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | The message content must be UTF-8-coded and can be no more than 256 KB.                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | If the subscription endpoint is a mobile number, each SMS message can contain up to 256 bytes. If you publish a message that exceeds the size limit, SMN sends it as multiple messages, each fitting within the size limit. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_to_live    | No              | String          | The maximum retention period of a message in SMN                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | After the retention period expires, SMN does not send this message. The time period is measured in seconds, and the default retention period is **3600** (one hour).                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | The retention period must be a positive integer less than or equal to 604,800 (3600 x 24 x 7).                                                                                                                              |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId: f96188c7ccaf4ffba0c9aa149ab2bd57:test_create_topic_v2/publish

   .. code-block::

      {
          "subject": "test message v2",
          "message": "Message test message v2",
          "time_to_live": "3600"
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
