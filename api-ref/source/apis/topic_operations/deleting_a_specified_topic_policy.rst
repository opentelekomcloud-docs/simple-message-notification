:original_name: smn_api_51008.html

.. _smn_api_51008:

Deleting a Specified Topic Policy
=================================

Function
--------

Delete a specified topic policy.

URI
---

DELETE /v2/{project_id}/notifications/topics/{topic_urn}/attributes/{name}

For details, see :ref:`Table 1 <smn_api_51008__table60453091>`.

.. _smn_api_51008__table60453091:

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
   | name            | Yes             | String          | Attribute name                                                                                                    |
   |                 |                 |                 |                                                                                                                   |
   |                 |                 |                 | Only specified attribute names are supported. For details, see :ref:`Topic Attribute List <smn_api_a1000>`.       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <smn_api_51008__table38552084>` describes the response parameters.

.. _smn_api_51008__table38552084:

.. table:: **Table 2** Response parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

Example Request
---------------

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/{topic_urn}/attributes/access_policy

Example Response
----------------

.. code-block::

   {
       "request_id": "6837531fd3f54550927b930180a706bf"
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
