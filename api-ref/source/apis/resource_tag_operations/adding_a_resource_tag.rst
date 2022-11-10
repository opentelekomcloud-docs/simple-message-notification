:original_name: smn_api_56003.html

.. _smn_api_56003:

Adding a Resource Tag
=====================

Description
-----------

-  API name

   CreateResourceTag

-  Function

   You can add a maximum of 10 tags to a resource.

   The API is idempotent. If a to-be-created tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

URI
---

-  URI format

   POST /v2/{project_id}/{resource_type}/{resource_id}/tags

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

   +-----------+-----------+------------------------+------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                   | Description                                                                                    |
   +===========+===========+========================+================================================================================================+
   | tag       | Yes       | Resource tag structure | Resource tag to be added. For details, see :ref:`Table 1 <smn_api_56003__table1127111434346>`. |
   +-----------+-----------+------------------------+------------------------------------------------------------------------------------------------+

   .. _smn_api_56003__table1127111434346:

   .. table:: **Table 1** Resource_tag structure

      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description | Constraint                                                                                                                                                                                           |
      +===========+===========+========+=============+======================================================================================================================================================================================================+
      | key       | Yes       | String | Tag key     | The key contains 36 Unicode characters at most and cannot be blank or an empty string. It can contain only digits, letters, hyphens (-), and underscores (_) and must not start or end with a space. |
      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value     | Yes       | String | Tag value   | Each value contains 43 Unicode characters at most and can be an empty string. It can contain only digits, letters, hyphens (-), and underscores (_) and must not start or end with a space.          |
      +-----------+-----------+--------+-------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/{resource_id}/tags

-  Example request

   .. code-block::

      {
           "tag":
           {
              "key":"DEV",
              "value":"DEV1"
           }
      }

Response
--------

None

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
