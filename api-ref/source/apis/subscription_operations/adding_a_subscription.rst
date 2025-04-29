:original_name: smn_api_52003.html

.. _smn_api_52003:

Adding a Subscription
=====================

Description
-----------

-  API name

   Subscribe

-  Function

   Add a subscription to a specified topic. If the status of the subscription is unconfirmed, a confirmation message is sent to the subscriber. After confirming the subscription, the subscriber can receive notification messages published to the topic.

   By default, 10,000 subscriptions can be added to a topic. However, in a high-concurrency scenario, which is rare, extra subscriptions may be added successfully.

   The API is idempotent. If the added subscription already exists, a successful result and status code 200 are returned. Otherwise, the status code is 201.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/topics/{topic_urn}/subscriptions

-  Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                       |
   +=================+=================+=================+===================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                        |
   |                 |                 |                 |                                                                                                                   |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                                               | Description                                                                                                                                     |
   +=================+=================+====================================================================================================================+=================================================================================================================================================+
   | endpoint        | Yes             | String                                                                                                             | Message endpoint                                                                                                                                |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    | .. note::                                                                                                                                       |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    |    For an HTTP subscription, the endpoint starts with **http://**.                                                                              |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    |    For an HTTPS subscription, the endpoint starts with **https://**.                                                                            |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    |    For an email subscription, the endpoint is an email address.                                                                                 |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    |    For an SMS subscription, the endpoint is a phone number.                                                                                     |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol        | Yes             | String                                                                                                             | Subscription protocol (Different protocols indicate different types of endpoints to receive messages.)                                          |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    | The following protocols are supported:                                                                                                          |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    | -  **email**: The endpoints are email address.                                                                                                  |
   |                 |                 |                                                                                                                    | -  **sms**: The endpoints are phone numbers.                                                                                                    |
   |                 |                 |                                                                                                                    | -  **http** and **https**: The endpoints are URLs.                                                                                              |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | remark          | No              | String                                                                                                             | Description of the subscription                                                                                                                 |
   |                 |                 |                                                                                                                    |                                                                                                                                                 |
   |                 |                 |                                                                                                                    | The remarks must be UTF-8-coded and can contain up to 128 bytes.                                                                                |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | extension       | No              | :ref:`SubscriptionExtension <smn_api_52003__request_subscriptionextension>` object                                 | Extended information                                                                                                                            |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | subscriptions   | No              | Array of :ref:`BatchAddSubscriptionsRequestBody <smn_api_52003__request_batchaddsubscriptionsrequestbody>` objects | This parameter is mandatory when subscriptions need to be created in batches. SMN allows you to create a maximum of 50 subscriptions at a time. |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_52003__request_batchaddsubscriptionsrequestbody:

   .. table:: **Table 1** BatchAddSubscriptionsRequestBody

      +-----------------+-----------------+------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type                                                                               | Description                                                                                            |
      +=================+=================+====================================================================================+========================================================================================================+
      | endpoint        | Yes             | String                                                                             | Message endpoint                                                                                       |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    | .. note::                                                                                              |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    |    For an HTTP subscription, the endpoint starts with **http://**.                                     |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    |    For an HTTPS subscription, the endpoint starts with **https://**.                                   |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    |    For an email subscription, the endpoint is an email address.                                        |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    |    For an SMS subscription, the endpoint is a phone number.                                            |
      +-----------------+-----------------+------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
      | protocol        | Yes             | String                                                                             | Subscription protocol (Different protocols indicate different types of endpoints to receive messages.) |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    | The following protocols are supported:                                                                 |
      |                 |                 |                                                                                    |                                                                                                        |
      |                 |                 |                                                                                    | -  **email**: The endpoints are email address.                                                         |
      |                 |                 |                                                                                    | -  **sms**: The endpoints are phone numbers.                                                           |
      |                 |                 |                                                                                    | -  **http** and **https**: The endpoints are URLs.                                                     |
      +-----------------+-----------------+------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
      | remark          | No              | String                                                                             | Description of the subscription. The remarks must be UTF-8-coded and can contain up to 128 bytes.      |
      +-----------------+-----------------+------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+
      | extension       | No              | :ref:`SubscriptionExtension <smn_api_52003__request_subscriptionextension>` object | Extended subscription information                                                                      |
      +-----------------+-----------------+------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------+

   .. _smn_api_52003__request_subscriptionextension:

   .. table:: **Table 2** SubscriptionExtension

      +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                       |
      +=================+=================+====================+===================================================================================================================================================================================================================================================+
      | header          | No              | Map<String,String> | This is an HTTP header field, which can be customized within the field range. The field content exists in the form of key/value pairs. When a topic is used to send messages, confirmed subscription messages carry the user-defined HTTP header. |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | Header for subscriptions over HTTP or HTTPS. The header must meet the following requirements:                                                                                                                                                     |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | **key** can contain letters, digits, and hyphens (-). **key** cannot end with a hyphen (-) nor contain consecutive hyphens (-).                                                                                                                   |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | You can specify up to 10 key/value pairs.                                                                                                                                                                                                         |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | **key** must start with **x-** but not **x-smn**. Examples: **x-abc-cba** or **x-abc**.                                                                                                                                                           |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | The total length of all key/value pairs cannot exceed 1,024 characters.                                                                                                                                                                           |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | The value is case insensitive.                                                                                                                                                                                                                    |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | The key value must be unique.                                                                                                                                                                                                                     |
      |                 |                 |                    |                                                                                                                                                                                                                                                   |
      |                 |                 |                    | **value** must be an ASCII code. Unicode characters are not supported. Spaces are allowed.                                                                                                                                                        |
      +-----------------+-----------------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1/subscriptions

   .. code-block::

      {
          "protocol": "email",
          "endpoint": "xxx@xxx.com",
          "remark": "O&M"
      }

Response
--------

-  Parameter description

   +------------------+--------+--------------------------------------------------------+
   | Parameter        | Type   | Description                                            |
   +==================+========+========================================================+
   | request_id       | String | Request ID, which is unique                            |
   +------------------+--------+--------------------------------------------------------+
   | subscription_urn | String | Resource identifier of a subscription, which is unique |
   +------------------+--------+--------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "request_id": "fdbabe38ead6482b8574f82a3d1168e9",
          "subscription_urn": "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:2e778e84408e44058e6cbc6d3c377837"
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
