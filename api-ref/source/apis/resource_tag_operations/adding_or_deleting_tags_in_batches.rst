:original_name: smn_api_56002.html

.. _smn_api_56002:

Adding or Deleting Tags in Batches
==================================

Description
-----------

-  API name

   BatchCreateOrDeleteResourceTags

-  Function

   Add or delete tags for a specified topic in batches.

   You can add a maximum of 20 tags to a resource.

   .. note::

      The API is idempotent. When you are to create tags, if there are duplicate keys in the request body, an error is reported.

      If a to-be-created tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

      When tags are being deleted and some tags do not exist, the operation is considered successful by default. The character set of the tags will not be checked.

URI
---

-  URI format

   POST /v2/{project_id}/{resource_type}/{resource_id}/tags/action

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

   +-----------------+-----------------+------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                         | Description                                                                                                                                                                         |
   +=================+=================+==============================+=====================================================================================================================================================================================+
   | tags            | Yes             | Resource_tag structure array | Tag list. For details, see :ref:`Table 1 <smn_api_56002__table1127111434346>`.                                                                                                      |
   |                 |                 |                              |                                                                                                                                                                                     |
   |                 |                 |                              | When you delete tags, the tag structure cannot be missing, and the key cannot be left blank or be an empty string. The system does not check the character set when deleting a tag. |
   +-----------------+-----------------+------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String                       | Operation to be performed, which can be **create** or **delete**                                                                                                                    |
   +-----------------+-----------------+------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_56002__table1127111434346:

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

      POST https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/{resource_id}/tags/action

-  Request body

   Request body when **action** is set to **create**

   .. code-block::

      {
          "action": "create",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key",
                  "value": "value3"
              }
          ]
      }

   Request body when **action** is set to **delete**

   .. code-block::

      {
          "action": "delete",
          "tags": [
              {
                   "key": "key1"
               },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
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
