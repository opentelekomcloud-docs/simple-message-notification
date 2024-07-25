:original_name: smn_api_51009.html

.. _smn_api_51009:

Deleting All Topic Policies
===========================

Description
-----------

-  API name

   DeleteTopicAttributes

-  Function

   Delete all topic policies.

URI
---

-  URI format

   DELETE /v2/{project_id}/notifications/topics/{topic_urn}/attributes

-  Parameter description

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

Example request

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/{topic_urn}/attributes

Response
--------

-  Parameter description

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

-  Example response

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
