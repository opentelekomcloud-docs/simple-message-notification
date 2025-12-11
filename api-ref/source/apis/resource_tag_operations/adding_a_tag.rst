:original_name: smn_api_56003.html

.. _smn_api_56003:

Adding a Tag
============

Description
-----------

-  API name

   CreateResourceTag

-  Function

   You can add a maximum of 20 tags to a resource.

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
   |                 |                 |                 | Only **smn_topic** (topic) is supported.                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | resource_id     | Yes             | String          | Resource ID                                                                                            |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Obtain a resource ID:                                                                                  |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | -  Add **X-SMN-RESOURCEID-TYPE=name** in the request header and set the resource ID to the topic name. |
   |                 |                 |                 | -  Call the API for :ref:`querying topics by tag <smn_api_56001>` to obtain the resource ID.           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------+-----------+------------------------+---------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                   | Description                                                                           |
   +===========+===========+========================+=======================================================================================+
   | tag       | Yes       | Resource_tag structure | Tag to be added. For details, see :ref:`Table 1 <smn_api_56003__table1127111434346>`. |
   +-----------+-----------+------------------------+---------------------------------------------------------------------------------------+

   .. _smn_api_56003__table1127111434346:

   .. table:: **Table 1** Resource_tag structure

      +-----------------+-----------------+-----------------+---------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                   |
      +=================+=================+=================+===============================================================+
      | key             | Yes             | String          | The tag key.                                                  |
      |                 |                 |                 |                                                               |
      |                 |                 |                 | -  A tag key can contain a maximum of 127 Unicode characters. |
      |                 |                 |                 |                                                               |
      |                 |                 |                 | -  **key** cannot be left blank.                              |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------+
      | value           | Yes             | String          | The tag value.                                                |
      |                 |                 |                 |                                                               |
      |                 |                 |                 | -  Each value contains a maximum of 255 Unicode characters.   |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/{resource_id}/tags

-  Example request

   .. code-block::

      {
           "tag":
           {
              "key": "DEV",
              "value": "DEV1"
           }
      }

Response
--------

None

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
