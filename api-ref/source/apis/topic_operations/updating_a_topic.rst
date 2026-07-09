:original_name: en-us_topic_0036017301.html

.. _en-us_topic_0036017301:

Updating a Topic
================

Function
--------

Update the topic display name.

URI
---

PUT /v2/{project_id}/notifications/topics/{topic_urn}

For details, see :ref:`Table 1 <en-us_topic_0036017301__table20000134185146>`.

.. _en-us_topic_0036017301__table20000134185146:

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                       |
   +=================+=================+=================+===================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                        |
   |                 |                 |                 |                                                                                                                   |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

Request
-------

:ref:`Table 2 <en-us_topic_0036017301__table16833793185146>` describes the request parameters.

.. _en-us_topic_0036017301__table16833793185146:

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                              |
   +=================+=================+=================+==========================================================================================+
   | display_name    | Yes             | String          | Topic display name, which is presented as the name of the email sender in email messages |
   |                 |                 |                 |                                                                                          |
   |                 |                 |                 | The display name cannot exceed 192 bytes.                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+

Response
--------

:ref:`Table 3 <en-us_topic_0036017301__table11342130185146>` describes the response parameters.

.. _en-us_topic_0036017301__table11342130185146:

.. table:: **Table 3** Response parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

Example Request
---------------

.. code-block:: text

   PUT https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:test_topic_v2

.. code-block::

   {
       "display_name": "testtest222"
   }

Example Response
----------------

.. code-block::

   {
       "request_id": "6a63a18b8bab40ffb71ebd9cb80d0085"
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
