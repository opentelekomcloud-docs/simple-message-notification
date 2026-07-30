:original_name: smn_api_51003.html

.. _smn_api_51003:

Deleting a Topic
================

Function
--------

Delete a topic and its subscribers. If a topic is deleted, a pending message will fail to deliver to the topic subscribers.

URI
---

DELETE /v2/{project_id}/notifications/topics/{topic_urn}

For details, see :ref:`Table 1 <smn_api_51003__table36893359>`.

.. _smn_api_51003__table36893359:

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

None

Response
--------

:ref:`Table 2 <smn_api_51003__table9967070>` describes the response parameters.

.. _smn_api_51003__table9967070:

.. table:: **Table 2** Response parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

Example Request
---------------

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:test_topic_v2

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
