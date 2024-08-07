:original_name: smn_api_51005.html

.. _smn_api_51005:

Querying Details of a Topic
===========================

Description
-----------

-  API name

   QueryTopicDetail

-  Function

   Query the detailed information about a topic.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/topics/{topic_urn}

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

Example request

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:8bad8a40e0f7462f8c1676e3f93a8183:test_create_topic_v2

Response
--------

-  Parameter description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================+
   | request_id            | String                | Request ID, which is unique                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Name of the topic                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn             | String                | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`.                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name          | String                | Topic display name, which is presented as the name of the email sender in email messages                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | push_policy           | Integer               | Message pushing policy                                                                                                                       |
   |                       |                       |                                                                                                                                              |
   |                       |                       | **0** indicates that the message sending fails and the message is cached in the queue. **1** indicates that the failed message is discarded. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Time when the topic was created                                                                                                              |
   |                       |                       |                                                                                                                                              |
   |                       |                       | The UTC time is in *YYYY-MM-DDTHH:MM:SSZ* format.                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Time when the topic was updated                                                                                                              |
   |                       |                       |                                                                                                                                              |
   |                       |                       | The UTC time is in *YYYY-MM-DDTHH:MM:SSZ* format.                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                | Enterprise project ID                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "update_time": "2016-08-01T02:16:38Z",
          "push_policy": 0,
          "create_time": "2016-08-01T02:16:38Z",
          "name": "test_create_topic_v2",
          "topic_urn": "urn:smn:regionId:8bad8a40e0f7462f8c1676e3f93a8183:test_create_topic_v2",
          "display_name": "test create topic v2",
          "request_id": "6837531fd3f54550927b930180a706bf",
          "enterprise_project_id" : "0"
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
