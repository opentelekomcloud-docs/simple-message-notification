:original_name: smn_api_51006.html

.. _smn_api_51006:

Querying a Topic Policy
=======================

Description
-----------

-  API name

   ListTopicAttributes

-  Function

   Query a topic policy.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/topics/{topic_urn}/attributes

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
   | name            | No              | String          | Specifies the policy name.                                                                                        |
   |                 |                 |                 |                                                                                                                   |
   |                 |                 |                 | Only specified policy names are supported. For details, see :ref:`Topic Attribute List <smn_api_a1000>`.          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

   .. note::

      If **name** is not specified, all attribute values of the topic are queried. The supported attribute values are provided in :ref:`Topic Attribute List <smn_api_a1000>`.

Request
-------

Example request

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:8bad8a40e0f7462f8c1676e3f93a8183:test_create_topic_v2/attributes?name=access_policy

Response
--------

-  Parameter description

   +-----------------------+-----------------------+------------------------------------------+
   | Parameter             | Type                  | Description                              |
   +=======================+=======================+==========================================+
   | request_id            | String                | Request ID, which is unique              |
   +-----------------------+-----------------------+------------------------------------------+
   | attributes            | Map                   | Attribute key-value pair                 |
   |                       |                       |                                          |
   |                       |                       | **access_policy**: topic access policy   |
   |                       |                       |                                          |
   |                       |                       | **introduction**: description of a topic |
   +-----------------------+-----------------------+------------------------------------------+

-  Example response

   .. code-block::

      {
         "request_id": "6837531fd3f54550927b930180a706bf",
         "attributes": {
         "access_policy": "{
               "Version": "2016-09-07",
               "Id": "__default_policy_ID",
               "Statement": [
                  {
                    "Sid": "__user_pub_0",
                    "Effect": "Allow",
                    "Principal": {
                      "CSP": [
                               "urn:csp:iam::93dc1b4697ac493d9b7d089569f86b32:root"
                             ]
                       },
                    "Action": ["SMN:Publish","SMN:QueryTopicDetail"],
                    "Resource": "urn:smn:regionId:8bad8a40e0f7462f8c1676e3f93a8183:aaa"
                    },
                    {
                    "Sid": "__service_pub_0",
                    "Effect": "Allow",
                    "Principal": {
                       "Service": ["obs"]
                       },
                    "Action": ["SMN:Publish","SMN:QueryTopicDetail"],
                    "Resource": "urn:smn:regionId:8bad8a40e0f7462f8c1676e3f93a8183:aaa"
                    }
                   ]
                }"
             }
        }

   .. note::

      The value of **access_policy** is a JSON character string, which requires escape characters. While in the preceding example, the characters are not escaped. Escape them before using the policy.

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
