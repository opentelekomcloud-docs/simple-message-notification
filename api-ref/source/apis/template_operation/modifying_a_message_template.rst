:original_name: smn_api_53002.html

.. _smn_api_53002:

Modifying a Message Template
============================

Description
-----------

-  API name

   UpdateMessageTemplate

-  Function

   Modify the message template content.

URI
---

-  URI format

   PUT /v2/{project_id}/notifications/message_template/{message_template_id}

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

-  Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                      |
   +=================+=================+=================+==================================================================+
   | content         | Yes             | String          | Template content, which currently supports plain text only       |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | The template content cannot be left blank or larger than 256 KB. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      PUT https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template/b3ffa2cdda574168826316f0628f774f

   .. code-block::

      {
          "content": "(1/22)You are invited to subscribe to topic({topic_id_id1}). Click the following URL to confirm subscription:(If you do not want to subscribe to this topic, ignore this message.)"
      }

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
          "request_id": "5fcba32bd2814ea39431829c22bda94b"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
