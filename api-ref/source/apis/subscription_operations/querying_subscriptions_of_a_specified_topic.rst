:original_name: smn_api_52002.html

.. _smn_api_52002:

Querying Subscriptions of a Specified Topic
===========================================

Description
-----------

-  API name

   ListSubscriptionsByTopic

-  Function

   Query the list of subscriptions of a specified topic by page. The list is sorted by the subscription adding time in ascending order. You can specify **offset** and **limit**. If no subscription has been added to the topic, an empty list is returned.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/topics/{topic_urn}/subscriptions

-  Parameter description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                                                              |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`.                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Offset                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | If the offset is an integer greater than 0 but less than the number of resources, all resources after this offset will be queried. The default offset is **0**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | -  Number of resources returned on each page                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | -  Value range: 1-100                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 |    Commonly used numbers are **10**, **20**, and **50**.                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 |    The default number is **100**.                                                                                                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

Example request

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1/subscriptions?offset=0&limit=100

Response
--------

-  Parameter description

   +--------------------+----------------------------------------------------------------------+-----------------------------+
   | Parameter          | Type                                                                 | Description                 |
   +====================+======================================================================+=============================+
   | request_id         | String                                                               | Request ID, which is unique |
   +--------------------+----------------------------------------------------------------------+-----------------------------+
   | subscription_count | Integer                                                              | Number of subscriptions     |
   +--------------------+----------------------------------------------------------------------+-----------------------------+
   | subscriptions      | Array of :ref:`Table 1 <smn_api_52002__table62621618105717>` objects | Subscription structure      |
   +--------------------+----------------------------------------------------------------------+-----------------------------+

   .. _smn_api_52002__table62621618105717:

   .. table:: **Table 1** Subscription structure

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                            |
      +=======================+=======================+========================================================================================================+
      | topic_urn             | String                | Resource identifier of a topic, which is unique                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | protocol              | String                | Subscription protocol (Different protocols indicate different types of endpoints to receive messages.) |
      |                       |                       |                                                                                                        |
      |                       |                       | The following protocols are supported:                                                                 |
      |                       |                       |                                                                                                        |
      |                       |                       | -  **email**: The endpoints are email address.                                                         |
      |                       |                       | -  **sms**: The endpoints are phone numbers.                                                           |
      |                       |                       | -  **http** and **https**: The endpoints are URLs.                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | subscription_urn      | String                | Resource identifier of a subscription, which is unique                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | owner                 | String                | Project ID of the topic creator                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | endpoint              | String                | Message receiving endpoint                                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | remark                | String                | Remarks                                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+
      | status                | Integer               | Subscription status                                                                                    |
      |                       |                       |                                                                                                        |
      |                       |                       | -  **0**: unconfirmed                                                                                  |
      |                       |                       | -  **1**: confirmed                                                                                    |
      |                       |                       | -  **3**: canceled                                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "request_id": "4650b14bf221492fb819c231d167e6fe",
          "subscription_count": 2,
          "subscriptions": [
              {
                  "topic_urn": "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1",
                  "protocol": "sms",
                  "subscription_urn": "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:2e778e84408e44058e6cbc6d3c377837",
                  "owner": "762bdb3251034f268af0e395c53ea09b",
                  "endpoint": "xxxxxxxxxx",
                  "remark": "",
                  "status": 0
              },
              {
                  "topic_urn": "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1",
                  "protocol": "email",
                  "subscription_urn": "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:a2d52a9f5c3b47f48c3fafb177a58796",
                  "owner": "762bdb3251034f268af0e395c53ea09b",
                  "endpoint": "xx@xx.com",
                  "remark": "",
                  "status": 0
              }
      ]
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
