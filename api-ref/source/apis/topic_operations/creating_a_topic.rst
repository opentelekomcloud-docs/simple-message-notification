:original_name: en-us_topic_0036017300.html

.. _en-us_topic_0036017300:

Creating a Topic
================

Function
--------

Create a topic. Each user can create 3,000 topics at most. In the high-concurrent scenario, a user may create a few topics more than 3,000.

The API is idempotent. It returns a successful result after creating a topic. If a topic of the same name already exists, the status code is 200. Otherwise, the status code is 201.

URI
---

POST /v2/{project_id}/notifications/topics

For details, see :ref:`Table 1 <en-us_topic_0036017300__table29213141184157>`.

.. _en-us_topic_0036017300__table29213141184157:

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

:ref:`Table 2 <en-us_topic_0036017300__table65343646184157>` describes the request parameters.

.. _en-us_topic_0036017300__table65343646184157:

.. table:: **Table 2** Request parameters

   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                      |
   +=======================+=================+=================+==================================================================================================================================================+
   | name                  | Yes             | String          | Name of the topic                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                  |
   |                       |                 |                 | Enter 1 to 255 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed. The topic name must start with a letter or digit. |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name          | Yes             | String          | Topic display name, which is presented as the name of the email sender in email messages                                                         |
   |                       |                 |                 |                                                                                                                                                  |
   |                       |                 |                 | The display name cannot exceed 192 bytes.                                                                                                        |
   |                       |                 |                 |                                                                                                                                                  |
   |                       |                 |                 | **display_name** is left blank by default.                                                                                                       |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String          | (Optional) Enterprise project ID. It is required when the enterprise project function is enabled.                                                |
   |                       |                 |                 |                                                                                                                                                  |
   |                       |                 |                 | Default value: **0**                                                                                                                             |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 3 <en-us_topic_0036017300__table741793184157>` describes the response parameters.

.. _en-us_topic_0036017300__table741793184157:

.. table:: **Table 3** Response parameters

   +------------+--------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                                       |
   +============+========+===================================================================================================================+
   | request_id | String | Request ID, which is unique                                                                                       |
   +------------+--------+-------------------------------------------------------------------------------------------------------------------+
   | topic_urn  | String | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`. |
   +------------+--------+-------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics

.. code-block::

   {
       "name": "test_topic_v2",
       "display_name": "testtest"
   }

Example Response
----------------

.. code-block::

   {
       "request_id": "6a63a18b8bab40ffb71ebd9cb80d0085",
       "topic_urn": "urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:test_topic_v2"
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
