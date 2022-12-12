:original_name: smn_api_56005.html

.. _smn_api_56005:

Querying Resource Tags
======================

Description
-----------

-  API name

   ListResourceTags

-  Function

   Query tags of a specified resource.

URI
---

-  URI format

   GET /v2/{project_id}/{resource_type}/{resource_id}/tags

-  Parameter description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                            |
   +=================+=================+=================+========================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                             |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | resource_type   | Yes             | String          | Resource type                                                                                          |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | The value can be the following:                                                                        |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | **smn_topic**: topic                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | resource_id     | Yes             | String          | Resource ID                                                                                            |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Obtain a resource ID:                                                                                  |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | -  Add **X-SMN-RESOURCEID-TYPE=name** in the request header and set the resource ID to the topic name. |
   |                 |                 |                 | -  Call the **GetResourceInstances** API to obtain the resource ID.                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Request example

   .. code-block:: text

      GET https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/{resource_id}/tags

Response
--------

-  Parameter description

   +-----------+------------------------------+--------------------------------------------------------------------------------+
   | Parameter | Type                         | Description                                                                    |
   +===========+==============================+================================================================================+
   | tags      | Resource_tag structure array | Tag list. For details, see :ref:`Table 1 <smn_api_56005__table1127111434346>`. |
   +-----------+------------------------------+--------------------------------------------------------------------------------+

   .. _smn_api_56005__table1127111434346:

   .. table:: **Table 1** Resource_tag structure

      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description | Constraint                                                                                                                                                                                           |
      +===========+===========+========+=============+======================================================================================================================================================================================================+
      | key       | Yes       | String | Tag key     | The key contains 36 Unicode characters at most and cannot be blank or an empty string. It can contain only digits, letters, hyphens (-), and underscores (_) and must not start or end with a space. |
      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value     | Yes       | String | Tag value   | Each value contains 43 Unicode characters at most and can be an empty string. It can contain only digits, letters, hyphens (-), and underscores (_) and must not start or end with a space.          |
      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block::

      {
             "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
