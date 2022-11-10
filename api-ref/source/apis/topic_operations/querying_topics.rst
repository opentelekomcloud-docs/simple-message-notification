:original_name: smn_api_51004.html

.. _smn_api_51004:

Querying Topics
===============

Description
-----------

-  API name

   ListTopics

-  Function

   Query the topic list by page. The list is sorted by the topic creation time in descending order. If no topic has been created, an empty list is returned.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/topics?offset={offset}&limit={limit}

-  Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | int             | Offset                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | If the value is an integer greater than 0 but less than the number of resources, all resources after this offset will be queried. The default value is **0**. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | int             | -  Number of resources returned on each page                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 | -  Value range: 1-100                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 |    Commonly used values are **10**, **20**, and **50**.                                                                                                       |
   |                 |                 |                 |                                                                                                                                                               |
   |                 |                 |                 |    The default value is **100**.                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

Request example

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/notifications/topics?offset=0&limit=100

Response
--------

-  Parameter description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                      |
   +=======================+=======================+==================================================================================================================================+
   | request_id            | String                | Request ID, which is unique                                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | topic_count           | int                   | Number of topics in your account                                                                                                 |
   |                       |                       |                                                                                                                                  |
   |                       |                       | .. note::                                                                                                                        |
   |                       |                       |                                                                                                                                  |
   |                       |                       |    No matter what offset and limit values you have set in the request, this parameter always returns the total number of topics. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | topics                | Topic structure array | Topic details                                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | See :ref:`Table 1 <smn_api_51004__table10636317195533>`.                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_51004__table10636317195533:

   .. table:: **Table 1** Topic structure

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                              |
      +=======================+=======================+==========================================================================================+
      | topic_urn             | String                | Resource identifier of a topic, which is unique                                          |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | name                  | String                | Topic name                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | display_name          | String                | Topic display name, which is presented as the name of the email sender in email messages |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
      | push_policy           | Int                   | Message push policy                                                                      |
      |                       |                       |                                                                                          |
      |                       |                       | -  **0**: Failed messages will be saved in message queues.                               |
      |                       |                       | -  **1**: Failed messages will be discarded.                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

-  Response example

   .. code-block::

      {
          "request_id": "70bb40bef50e4a14b116a5a527fd7432",
          "topic_count": 1,
          "topics": [
              {
                  "topic_urn": "urn:smn:regionId:8bad8a40e0f7462f8c1676e3f93a8183:test_topic_v2",
                  "display_name": "testtest",
                  "name": "test_topic_v1",
                  "push_policy": 0
              }
          ]
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
