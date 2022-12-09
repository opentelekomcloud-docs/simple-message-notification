:original_name: smn_api_56001.html

.. _smn_api_56001:

Querying Resources by Tag
=========================

Description
-----------

-  API name

   GetResourceInstances

-  Function

   Query SMN resources by tag.

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
   |                 |                 |                 | The value can be the following:                    |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | **smn_topic**: topic                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                            | Description                                                                                                                                                                                                                                                                                                                        |
   +=================+=================+=================================+====================================================================================================================================================================================================================================================================================================================================+
   | tags            | No              | Tags structure array            | Includes specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                                     |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 10 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 10 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in AND relationship.   |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | No              | Tags structure array            | Includes any of the specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 10 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 10 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in OR relationship.    |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Tags structure array            | Excludes specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                                     |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 10 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 10 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in NAND relationship.  |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | No              | Tags structure array            | Excludes any of the specified tags. For details, see :ref:`Table 1 <smn_api_56001__table12385184281216>`.                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | .. note::                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 |    The structure body is mandatory. A maximum of 10 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. Each tag key can have up to 10 tag values. Each tag key and tag values of one key must be unique. Resources identified by different keys are in NOR relationship.   |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String                          | Maximum number of resources to be queried                                                                                                                                                                                                                                                                                          |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | -  If **action** is set to **count**, this parameter does not take effect.                                                                                                                                                                                                                                                         |
   |                 |                 |                                 | -  If **action** is set to **filter**, this parameter takes effect. Its value ranges from 1 to 1000 (default).                                                                                                                                                                                                                     |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String                          | Start location of pagination query. The query starts from the next resource of the specified location. You do not need to specify this parameter when querying resources on the first page. When you query resources on subsequent pages, set this parameter to the location returned in the response body for the previous query. |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | -  If **action** is set to **count**, this parameter does not take effect.                                                                                                                                                                                                                                                         |
   |                 |                 |                                 | -  If **action** is set to **filter**, this parameter takes effect. Its value can be 0 (default) or a positive integer.                                                                                                                                                                                                            |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String                          | Operation to be performed. The value can be **filter** or **count** (case-sensitive).                                                                                                                                                                                                                                              |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | **filter**: queries resources in pages based on filter conditions.                                                                                                                                                                                                                                                                 |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | **count**: queries the total number of resources meeting filter conditions.                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Match condition structure array | Key-value pair to be matched                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | The key can only be **resource_name**.                                                                                                                                                                                                                                                                                             |
   |                 |                 |                                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                                 | The value will be exactly matched.                                                                                                                                                                                                                                                                                                 |
   +-----------------+-----------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_56001__table12385184281216:

   .. table:: **Table 1** Tags structure

      +-----------+-----------+-------------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type        | Description | Constraint                                                                                                                                                                                                                                                                                                       |
      +===========+===========+=============+=============+==================================================================================================================================================================================================================================================================================================================+
      | key       | Yes       | String      | Tag key     | A key contains 127 Unicode characters and cannot be blank.                                                                                                                                                                                                                                                       |
      +-----------+-----------+-------------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | Yes       | String list | Value list  | Each value contains a maximum of 255 Unicode characters. If the value starts with an asterisk (*), the character string following the asterisk is fuzzy-matched. The **values** field cannot be missing, but can be an empty list. If it is empty, any value will be matched. The values are in OR relationship. |
      +-----------+-----------+-------------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

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
                 "value": "resouurce"
            }
           ]
         }

Response
--------

-  Parameter description

   +-------------+-----------+--------------------------+--------------------------------------------------------------------+
   | Parameter   | Mandatory | Type                     | Description                                                        |
   +=============+===========+==========================+====================================================================+
   | resources   | Yes       | Resource structure array | For details, see :ref:`Table 2 <smn_api_56001__table97917514177>`. |
   +-------------+-----------+--------------------------+--------------------------------------------------------------------+
   | total_count | Yes       | Integer                  | Total number of resources                                          |
   +-------------+-----------+--------------------------+--------------------------------------------------------------------+

   .. _smn_api_56001__table97917514177:

   .. table:: **Table 2** Resource structure

      +-----------------+-----------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type                         | Description                                                                                                                                    |
      +=================+=================+==============================+================================================================================================================================================+
      | resource_id     | Yes             | String                       | Resource ID                                                                                                                                    |
      +-----------------+-----------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_detail | Yes             | Object                       | Resource details. Resource object used for extension. The value is left blank by default.                                                      |
      |                 |                 |                              |                                                                                                                                                |
      |                 |                 |                              | For topic resources, the value of this field is **{"topic_urn":"${TopicUrn}","display_name":"display name"}**.                                 |
      |                 |                 |                              |                                                                                                                                                |
      |                 |                 |                              | For other resources, the value is **null**.                                                                                                    |
      +-----------------+-----------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | Yes             | Resource_tag structure array | List of queried tags. If no tag is matched, an empty array is returned. For details, see :ref:`Table 3 <smn_api_56001__table178221351151717>`. |
      +-----------------+-----------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_name   | Yes             | String                       | Resource name                                                                                                                                  |
      +-----------------+-----------------+------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_56001__table178221351151717:

   .. table:: **Table 3** Resource_tag structure

      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description | Constraint                                                                                                                                                                                           |
      +===========+===========+========+=============+======================================================================================================================================================================================================+
      | key       | Yes       | String | Tag key     | The key contains 36 Unicode characters at most and cannot be blank or an empty string. It can contain only digits, letters, hyphens (-), and underscores (_) and must not start or end with a space. |
      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value     | Yes       | String | Tag value   | Each value contains 43 Unicode characters at most and can be an empty string. It can contain only digits, letters, hyphens (-), and underscores (_) and must not start or end with a space.          |
      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   Response body when **action** is set to **filter**

   .. code-block::

      {
            "resources": [
               {
                  "resource_detail": {
                       "topic_urn":"urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:resouece1",
                       "display_name":"testtest"
                   },
                  "resource_id": "cffe4fc4c9a54219b60dbaf7b586e132",
                  "resource_name": "resouece1",
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

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
