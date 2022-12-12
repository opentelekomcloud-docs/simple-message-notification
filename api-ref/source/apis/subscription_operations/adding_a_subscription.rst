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

   By default, 10000 subscriptions can be added to a topic. However, in a high-concurrency scenario, which is rare, extra subscriptions may be added successfully.

   The API is idempotent. If the added subscription already exists, a successful result and status code 200 are returned. Otherwise, the status code is 201.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/topics/{topic_urn}/subscriptions

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                            |
   +=================+=================+=================+========================================================================================================+
   | endpoint        | Yes             | String          | Message endpoint                                                                                       |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | .. note::                                                                                              |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 |    For an HTTP subscription, the endpoint starts with **http://**.                                     |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 |    For an HTTPS subscription, the endpoint starts with **https://**.                                   |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 |    For an email subscription, the endpoint is an email address.                                        |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 |    For an SMS subscription, the endpoint is a phone number.                                            |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 |    For a DMS subscription, the endpoint is a message queue.                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | protocol        | Yes             | String          | Subscription protocol (Different protocols indicate different types of endpoints to receive messages.) |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Currently, the following protocols are supported:                                                      |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | -  **email**: The endpoints are email address.                                                         |
   |                 |                 |                 | -  **sms**: The endpoints are phone numbers.                                                           |
   |                 |                 |                 | -  **http** and **https**: The endpoints are URLs.                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | remark          | No              | String          | Description of the subscription                                                                        |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | The remarks must be a UTF-8-coded character string containing 128 bytes at most.                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

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

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
