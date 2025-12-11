:original_name: smn_api_56005.html

.. _smn_api_56005:

Querying Tags of a Topic
========================

Description
-----------

-  API name

   ListResourceTags

-  Function

   Query tags of a topic.

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

   None

-  Example request

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

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
