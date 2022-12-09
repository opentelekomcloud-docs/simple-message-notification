:original_name: smn_api_51006.html

.. _smn_api_51006:

Querying Topic Attributes
=========================

Description
-----------

-  API name

   ListTopicAttributes

-  Function

   Query the topic attribute information.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/topics/{topic_urn}/attributes?name={name}

-  Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                         |
   +=================+=================+=================+=====================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                          |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it according to :ref:`Querying Topics <smn_api_51004>`.               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Attribute name                                                                                                      |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Only specified attribute names are supported. For details, see section :ref:`Topic Attribute List <smn_api_a1000>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

   .. note::

      If the **name** parameter is not specified, all attribute values of the topic are queried. The supported attribute values are provided in section :ref:`Topic Attribute List <smn_api_a1000>`.

Request
-------

Request example

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

-  Response example

   .. code-block::

      {
         "request_id":"6837531fd3f54550927b930180a706bf",
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

      The value of **access_policy** is a JSON character string, which requires escape characters. While in the preceding example, the characters are not escaped. You need to escape them before using the policy.

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
