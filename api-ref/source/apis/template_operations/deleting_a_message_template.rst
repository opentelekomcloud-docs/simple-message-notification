:original_name: smn_api_53003.html

.. _smn_api_53003:

Deleting a Message Template
===========================

Function
--------

Delete a message template. After you delete the template, you can no longer use it to publish messages.

URI
---

DELETE /v2/{project_id}/notifications/message_template/{message_template_id}

For details, see :ref:`Table 1 <smn_api_53003__table28042199>`.

.. _smn_api_53003__table28042199:

.. table:: **Table 1** URI parameters

   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                         |
   +=====================+=================+=================+=====================================================================================================================+
   | project_id          | Yes             | String          | Project ID                                                                                                          |
   |                     |                 |                 |                                                                                                                     |
   |                     |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                  |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | message_template_id | Yes             | String          | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Message Templates <smn_api_53004>`. |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <smn_api_53003__table29623765>` describes the response parameters.

.. _smn_api_53003__table29623765:

.. table:: **Table 2** Response parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

Example Request
---------------

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template/b3ffa2cdda574168826316f0628f774e

Example Response
----------------

.. code-block::

   {
       "request_id": "5fcba32bd2814ea39431829c22bda94b"
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
