:original_name: smn_api_56001.html

.. _smn_api_56001:

Querying Topics by Tag
======================

Description
-----------

-  API name

   GetResourceInstances

-  Function

   Query topics by tag.

URI
---

-  URI format

   POST /v2/{project_id}/{resource_type}/resource_instances/action

-  Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | resource_type   | Yes             | String          | Resource type                                      |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | Only **smn_topic** (topic) is supported.           |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                            | Description                                                                                                                                                                                                                                                                                                                         |
   +=================+=================+=================================+=====================================================================================================================================================================================================================================================================================================================================+
   | tags            | No              | Tags structure array            | Includes specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                                      |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 20 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in AND relationship.    |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | No              | Tags structure array            | Includes any of the specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 20 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in OR relationship.     |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Tags structure array            | Excludes specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                                      |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 20 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in NAND relationship.   |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | No              | Tags structure array            | Excludes any of the specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 20 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in NOR relationship.    |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String                          | The maximum number of resources to be queried                                                                                                                                                                                                                                                                                       |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | -  If **action** is set to **count**, this parameter does not take effect.                                                                                                                                                                                                                                                          |
   |                 |                 |                                 | -  If **action** is set to **filter**, this parameter takes effect. Its value ranges from 1 to 1000 (default).                                                                                                                                                                                                                      |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String                          | Start location of pagination query. The query starts from the next resource of the specified location. You do not need to specify this parameter when you query resources on the first page. When you query resources on subsequent pages, set this parameter to the location returned in the response body for the previous query. |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | -  If **action** is set to **count**, this parameter does not take effect.                                                                                                                                                                                                                                                          |
   |                 |                 |                                 | -  If **action** is set to **filter**, this parameter takes effect. Its value can be 0 (default) or a positive integer.                                                                                                                                                                                                             |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String                          | Operation to be performed. The operation can be **filter** or **count** (case-sensitive).                                                                                                                                                                                                                                           |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | **filter**: queries resources in pages based on filter conditions.                                                                                                                                                                                                                                                                  |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | **count**: queries the total number of resources meeting filter conditions.                                                                                                                                                                                                                                                         |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Match condition structure array | Key-value pair to be matched                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | The only supported key is **resource_name**.                                                                                                                                                                                                                                                                                        |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                                 | The value will be exactly matched.                                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+---------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_56001__table12385184281216:

   .. table:: **Table 1** Tags structure

      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                       |
      +=================+=================+==================+===================================================================================+
      | key             | Yes             | String           | The tag key.                                                                      |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  A tag key can contain a maximum of 127 Unicode characters.                     |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  **key** cannot be left blank.                                                  |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------+
      | values          | Yes             | Array of strings | The list of tag values.                                                           |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  Each tag contains a maximum of 10 values.                                      |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  Each value must be unique.                                                     |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  Each value contains a maximum of 255 Unicode characters.                       |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  If **values** is left blank, it defaults to **any_value**.                     |
      |                 |                 |                  |                                                                                   |
      |                 |                 |                  | -  Multiple values are linked by an OR operator, meaning only one needs to match. |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/resource_instances/action

   -  Request body when **action** is set to **filter**

      .. code-block::

         {
           "offset": "100",
           "limit": "100",
           "action": "filter",
           "matches":[
                {
                 "key": "resource_name",
                 "value": "resource1"
                }
            ],
            "not_tags": [
                {
                 "key": "key1",
                 "values": ["*value1","value2"]
                },
                {
                 "key": "key2",
                 "values": ["*value21","value22"]
                }
            ],
            "tags": [
             {
               "key": "key1",
               "values": ["*value1","value2"]
               }
              ],
            "tags_any": [
             {
               "key": "key1",
               "values": ["value1", "value2"]
             }
           ],
            "not_tags_any": [
             {
               "key": "key1",
               "values": ["value1", "value2"]
             }
           ]
         }

   -  Request body when **action** is set to **count**

      .. code-block::

         {
           "action": "count",
           "not_tags": [
             {
               "key": "key1",
               "values": ["value1", "*value2"]
             }
           ],
           "tags": [
             {
               "key": "key1",
               "values": ["value1", "value2"]
             }
           ],
           "tags_any": [
             {
               "key": "key1",
               "values": [ "value1", "value2"]
             }
           ],
           "not_tags_any": [
             {
               "key": "key1",
               "values": ["value1", "value2"]
             }
            ],
            "matches":[
            {
                 "key": "resource_name",
                 "value": "resource"
            }
           ]
         }

Response
--------

-  Parameter description

   +-------------+--------------------------+--------------------------------------------------------------------+
   | Parameter   | Type                     | Description                                                        |
   +=============+==========================+====================================================================+
   | resources   | Resource structure array | For details, see :ref:`Table 2 <smn_api_56001__table97917514177>`. |
   +-------------+--------------------------+--------------------------------------------------------------------+
   | total_count | Integer                  | Total number of resources.                                         |
   +-------------+--------------------------+--------------------------------------------------------------------+

   .. _smn_api_56001__table97917514177:

   .. table:: **Table 2** Resource structure

      +-----------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                         | Description                                                                                                                                    |
      +=======================+==============================+================================================================================================================================================+
      | resource_id           | String                       | Resource ID                                                                                                                                    |
      +-----------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_detail       | Object                       | Resource details Resource object used for extension. **resource_detail** is left blank by default.                                             |
      |                       |                              |                                                                                                                                                |
      |                       |                              | For topic resources, the value of this field is **{"topic_urn":"${TopicUrn}","display_name":"display name"}**.                                 |
      |                       |                              |                                                                                                                                                |
      |                       |                              | For other resources, the value is **null**.                                                                                                    |
      +-----------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | Resource_tag structure array | List of queried tags. If no tag is matched, an empty array is returned. For details, see :ref:`Table 3 <smn_api_56001__table178221351151717>`. |
      +-----------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_name         | String                       | Resource name                                                                                                                                  |
      +-----------------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_56001__table178221351151717:

   .. table:: **Table 3** Resource_tag structure

      +-----------------------+-----------------------+---------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                   |
      +=======================+=======================+===============================================================+
      | key                   | String                | The tag key.                                                  |
      |                       |                       |                                                               |
      |                       |                       | -  A tag key can contain a maximum of 127 Unicode characters. |
      |                       |                       |                                                               |
      |                       |                       | -  **key** cannot be left blank.                              |
      +-----------------------+-----------------------+---------------------------------------------------------------+
      | value                 | String                | The tag value.                                                |
      |                       |                       |                                                               |
      |                       |                       | -  Each value contains a maximum of 255 Unicode characters.   |
      +-----------------------+-----------------------+---------------------------------------------------------------+

-  Example response

   Response body when **action** is set to **filter**

   .. code-block::

      {
            "resources": [
               {
                  "resource_detail": {
                       "topic_urn":"urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:resource1",
                       "display_name":"testtest"
                   },
                  "resource_id": "cffe4fc4c9a54219b60dbaf7b586e132",
                  "resource_name": "resource1",
                  "tags": [
                      {
                         "key": "key1",
                         "value": "value1"
                      }
                   ]
               }
             ],
            "total_count": 1000
      }

   Response body when **action** is set to **count**

   .. code-block::

      {
             "total_count": 1000
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
