:original_name: smn_api_53003.html

.. _smn_api_53003:

Deleting a Message Template
===========================

Description
-----------

-  API name

   DeleteMessageTemplate

-  Function

   Delete a message template. After you delete the template, you cannot use it to publish messages any more.

URI
---

-  URI format

   DELETE /v2/{project_id}/notifications/message_template/{message_template_id}

-  Parameter description

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                      |
   +=====================+=================+=================+==================================================================================================================+
   | project_id          | Yes             | String          | Project ID                                                                                                       |
   |                     |                 |                 |                                                                                                                  |
   |                     |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                               |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | message_template_id | Yes             | String          | Unique resource ID of a topic. You can obtain it according to :ref:`Querying Message Templates <smn_api_53004>`. |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+

Request
-------

Request example

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template/b3ffa2cdda574168826316f0628f774e

Response
--------

-  Parameter description

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

-  Response example

   .. code-block::

      {
          "request_id": " 5fcba32bd2814ea39431829c22bda94b"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
