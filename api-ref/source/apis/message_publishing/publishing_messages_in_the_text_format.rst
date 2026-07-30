:original_name: smn_api_54001.html

.. _smn_api_54001:

Publishing Messages in the Text Format
======================================

Function
--------

Publish messages in the text format to a topic. After the message ID is returned, the message has been saved and is to be pushed to the subscribers of the topic.

URI
---

POST /v2/{project_id}/notifications/topics/{topic_urn}/publish

For details, see :ref:`Table 1 <smn_api_54001__table59928756194741>`.

.. _smn_api_54001__table59928756194741:

.. table:: **Table 1** URI parameters

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

:ref:`Table 2 <smn_api_54001__table49296942194741>` describes the request parameters.

.. _smn_api_54001__table49296942194741:

.. table:: **Table 2** Request parameters

   +--------------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type                                                                               | Description                                                                                                                                                                                                                 |
   +====================+=================+====================================================================================+=============================================================================================================================================================================================================================+
   | subject            | No              | String                                                                             | Message subject, which is used as the email subject when you publish email messages. The subject cannot exceed 512 characters.                                                                                              |
   +--------------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message            | Yes             | String                                                                             | Message content                                                                                                                                                                                                             |
   |                    |                 |                                                                                    |                                                                                                                                                                                                                             |
   |                    |                 |                                                                                    | The message content must be UTF-8-coded and can be no more than 256 KB.                                                                                                                                                     |
   |                    |                 |                                                                                    |                                                                                                                                                                                                                             |
   |                    |                 |                                                                                    | If the subscription endpoint is a mobile number, each SMS message can contain up to 256 bytes. If you publish a message that exceeds the size limit, SMN sends it as multiple messages, each fitting within the size limit. |
   +--------------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_to_live       | No              | String                                                                             | The maximum retention period of a message in SMN                                                                                                                                                                            |
   |                    |                 |                                                                                    |                                                                                                                                                                                                                             |
   |                    |                 |                                                                                    | After the retention period expires, SMN does not send this message. The time period is measured in seconds, and the default retention period is **3600** (one hour).                                                        |
   |                    |                 |                                                                                    |                                                                                                                                                                                                                             |
   |                    |                 |                                                                                    | The retention period must be a positive integer less than or equal to 604,800 (3600 x 24 x 7).                                                                                                                              |
   +--------------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_attributes | No              | Array of :ref:`MessageAttribute <smn_api_54001__request_messageattribute>` objects | Message attributes                                                                                                                                                                                                          |
   +--------------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _smn_api_54001__request_messageattribute:

.. table:: **Table 3** MessageAttribute

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================================================================+
   | name            | Yes             | String          | Attribute name. It can be 1 to 32 characters long, containing only lowercase letters, digits, and underscores (_). It cannot start or end with an underscore (_) or consecutively contain underscores (_).                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Attribute type                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  **STRING**: string                                                                                                                                                                                                                                                |
   |                 |                 |                 | -  **STRING_ARRAY**: string array (String.Array)                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **PROTOCOL**: protocol                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | Object          | Attribute value                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | -  If **type** is set to **STRING**, **value** can be 1 to 32 characters long, containing only letters, digits, and underscores (_).                                                                                                                                 |
   |                 |                 |                 | -  If **type** is set to **STRING_ARRAY**, **value** is an array of strings. The array can contain 1 to 10 elements, and each element must be unique. Each string in the array can be 1 to 32 characters long, containing only letters, digits, and underscores (_). |
   |                 |                 |                 | -  If **type** is set to **PROTOCOL**, **value** is an array of strings representing supported protocol types.                                                                                                                                                       |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 4 <smn_api_54001__table48990005194741>` describes the response parameters.

.. _smn_api_54001__table48990005194741:

.. table:: **Table 4** Response parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   message_id String Message ID, which is unique
   ========== ====== ===========================

Example Request
---------------

.. code-block:: text

   POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId: f96188c7ccaf4ffba0c9aa149ab2bd57:test_create_topic_v2/publish

.. code-block::

   {
       "subject": "test message v2",
       "message": "Message test message v2",
       "time_to_live": "3600"
   }

Example Response
----------------

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
