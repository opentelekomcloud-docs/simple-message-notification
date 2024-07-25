:original_name: smn_api_56006.html

.. _smn_api_56006:

Querying Tags in a Specified Project
====================================

Description
-----------

-  API name

   GetProjectTags

-  Function

   Query all tags of a resource type in a specified project.

URI
---

-  URI format

   GET /v2/{project_id}/{resource_type}/tags

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

   None

-  Example request

   .. code-block:: text

      GET https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/tags

Response
--------

-  Parameter description

   +-----------+----------------------+--------------------------------------------------------------------------------+
   | Parameter | Type                 | Description                                                                    |
   +===========+======================+================================================================================+
   | tags      | Tags structure array | Tag list. For details, see :ref:`Table 1 <smn_api_56006__table7893236124418>`. |
   +-----------+----------------------+--------------------------------------------------------------------------------+

   .. _smn_api_56006__table7893236124418:

   .. table:: **Table 1** Tags structure

      +-----------+-------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Type        | Description | Constraint                                                                                                                                                                                                                                                                                          |
      +===========+=============+=============+=====================================================================================================================================================================================================================================================================================================+
      | key       | String      | Tag key     | A key can contain up to 36 Unicode characters. A key cannot be left blank.                                                                                                                                                                                                                          |
      +-----------+-------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | String list | Value list  | Each value can contain up to 43 Unicode characters. If a value starts with an asterisk (``*``), the string following the asterisk is fuzzy-matched. The **values** field cannot be missing, but can be an empty list. If it is empty, any value will be matched. Values are in the OR relationship. |
      +-----------+-------------+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
            "tags": [
              {
                  "key": "key1",
                  "values": [
                    "value1",
                    "value2"
                    ]
              },
              {
                  "key": "key2",
                  "values": [
                    "value1",
                    "value2"
                    ]
              }
          ]
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
