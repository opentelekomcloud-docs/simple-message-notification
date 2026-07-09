:original_name: smn_api_54002.html

.. _smn_api_54002:

Publishing Messages Using a Message Structure
=============================================

Function
--------

Use the message structure to publish a message to a topic. After the message ID is returned, the message has been saved and is to be pushed to the subscribers of the topic. This API allows you to send different message content to different types of subscribers.

URI
---

POST /v2/{project_id}/notifications/topics/{topic_urn}/publish

For details, see :ref:`Table 1 <smn_api_54002__table5857211319494>`.

.. _smn_api_54002__table5857211319494:

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

:ref:`Table 2 <smn_api_54002__table4393345619494>` describes the request parameters.

.. _smn_api_54002__table4393345619494:

.. table:: **Table 2** Request parameters

   +--------------------+-----------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type                                                                               | Description                                                                                                                                                          |
   +====================+=================+====================================================================================+======================================================================================================================================================================+
   | subject            | No              | String                                                                             | Message subject, which is presented as the email subject when SMN sends messages to email subscribers                                                                |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | The message subject cannot exceed 512 bytes.                                                                                                                         |
   +--------------------+-----------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_structure  | Yes             | String                                                                             | Message structure, which contains JSON strings                                                                                                                       |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | **email**, **sms**, **http**, and **https** are supported.                                                                                                           |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | The **default** protocol is mandatory. If the system fails to match any other protocols, the default message is sent.                                                |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | .. note::                                                                                                                                                            |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    |    Three message formats are supported:                                                                                                                              |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    |    -  message                                                                                                                                                        |
   |                    |                 |                                                                                    |    -  message_structure                                                                                                                                              |
   |                    |                 |                                                                                    |    -  message_template_name                                                                                                                                          |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    |    If the three formats are specified at the same time, they take effect in the following sequence: **message_structure** > **message_template_name** > **message**. |
   +--------------------+-----------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_to_live       | No              | String                                                                             | The maximum retention period of a message in SMN                                                                                                                     |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | After the retention period expires, SMN does not send this message.                                                                                                  |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | Unit: second                                                                                                                                                         |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | Default retention period: **3600** (one hour)                                                                                                                        |
   |                    |                 |                                                                                    |                                                                                                                                                                      |
   |                    |                 |                                                                                    | The retention period must be a positive integer less than or equal to 604,800 (3600 x 24 x 7).                                                                       |
   +--------------------+-----------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_attributes | No              | Array of :ref:`MessageAttribute <smn_api_54002__request_messageattribute>` objects | Message attributes                                                                                                                                                   |
   +--------------------+-----------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _smn_api_54002__request_messageattribute:

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

:ref:`Table 4 <smn_api_54002__table2558106919494>` describes the response parameters.

.. _smn_api_54002__table2558106919494:

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
       "time_to_live": "3600",
       "message_structure": "{\n  \"default\": \"xxx\",\n  \"APNS\": \"{\\\"aps\\\":{\\\"alert\\\":{\\\"title\\\":\\\"xxx\\\",\\\"body\\\":\\\"xxx\\\"}}}\"\n}"
   }

.. note::

   For example, a topic has two types of subscriptions, SMS and email. After the API is called to publish messages, the email subscriber will receive message "abc", and the SMS subscriber will receive the default message "test v2 default".

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
