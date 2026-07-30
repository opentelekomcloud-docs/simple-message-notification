:original_name: smn_api_56006.html

.. _smn_api_56006:

Querying Tags in a Specified Project
====================================

Function
--------

Query all tags of a resource type in a specified project.

URI
---

GET /v2/{project_id}/{resource_type}/tags

For details, see :ref:`Table 1 <smn_api_56006__table1710612152111>`.

.. _smn_api_56006__table1710612152111:

.. table:: **Table 1** URI parameters

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

None

Response
--------

:ref:`Table 2 <smn_api_56006__table1226141212116>` describes the response parameters.

.. _smn_api_56006__table1226141212116:

.. table:: **Table 2** Response parameters

   +-----------+----------------------+--------------------------------------------------------------------------------+
   | Parameter | Type                 | Description                                                                    |
   +===========+======================+================================================================================+
   | tags      | Tags structure array | Tag list. For details, see :ref:`Table 3 <smn_api_56006__table7893236124418>`. |
   +-----------+----------------------+--------------------------------------------------------------------------------+

.. _smn_api_56006__table7893236124418:

.. table:: **Table 3** Tags structure

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                       |
   +=======================+=======================+===================================================================================+
   | key                   | String                | The tag key.                                                                      |
   |                       |                       |                                                                                   |
   |                       |                       | -  A tag key can contain a maximum of 128 Unicode characters.                     |
   |                       |                       |                                                                                   |
   |                       |                       | -  **key** cannot be left blank.                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------+
   | values                | String list           | The list of tag values.                                                           |
   |                       |                       |                                                                                   |
   |                       |                       | -  Each tag contains a maximum of 10 values.                                      |
   |                       |                       |                                                                                   |
   |                       |                       | -  Each value must be unique.                                                     |
   |                       |                       |                                                                                   |
   |                       |                       | -  Each value contains a maximum of 255 Unicode characters.                       |
   |                       |                       |                                                                                   |
   |                       |                       | -  If **values** is left blank, it defaults to **any_value**.                     |
   |                       |                       |                                                                                   |
   |                       |                       | -  Multiple values are linked by an OR operator, meaning only one needs to match. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/{resource_type}/tags

Example Response
----------------

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
