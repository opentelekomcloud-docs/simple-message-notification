:original_name: smn_api_56004.html

.. _smn_api_56004:

Deleting a Tag
==============

Description
-----------

-  API name

   DeleteResourceTag

-  Function

   The API is idempotent. When deleting a tag, the system does not check its character set. The tag key cannot be left blank or be an empty string. If the key of the tag to be deleted does not exist, 404 will be returned.

URI
---

-  URI format

   DELETE /v2/{project_id}/{resource_type}/{resource_id}/tags/{key}

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

-  Example request

   .. code-block:: text

      DELETE https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/{resource_id}/tags/{key}

Response
--------

None

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
