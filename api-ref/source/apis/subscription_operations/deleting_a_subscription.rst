:original_name: smn_api_52004.html

.. _smn_api_52004:

Deleting a Subscription
=======================

Function
--------

Delete a specified subscription.

URI
---

DELETE /v2/{project_id}/notifications/subscriptions/{subscription_urn}

For details, see :ref:`Table 1 <smn_api_52004__table28631516>`.

.. _smn_api_52004__table28631516:

.. table:: **Table 1** URI parameters

   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                     |
   +==================+=================+=================+=================================================================================================================+
   | project_id       | Yes             | String          | Project ID                                                                                                      |
   |                  |                 |                 |                                                                                                                 |
   |                  |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                              |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+
   | subscription_urn | Yes             | String          | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Subscriptions <smn_api_52001>`. |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <smn_api_52004__table20831783>` describes the response parameters.

.. _smn_api_52004__table20831783:

.. table:: **Table 2** Response parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

Example Request
---------------

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/subscriptions/urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:2e778e84408e44058e6cbc6d3c377837

Example Response
----------------

.. code-block::

   {
       "request_id": "f3197b274a6b473a8007eed79e716c30"
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
