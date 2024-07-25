:original_name: en-us_topic_0036017301.html

.. _en-us_topic_0036017301:

Updating a Topic
================

Description
-----------

-  API name

   UpdateTopic

-  Function

   Update the topic display name.

URI
---

-  URI format

   PUT /v2/{project_id}/notifications/topics/{topic_urn}

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

-  Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                              |
   +=================+=================+=================+==========================================================================================+
   | display_name    | Yes             | String          | Topic display name, which is presented as the name of the email sender in email messages |
   |                 |                 |                 |                                                                                          |
   |                 |                 |                 | The display name cannot exceed 192 bytes.                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      PUT https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:test_topic_v2
      {
          "display_name": "testtest222"
      }

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
          "request_id": "6a63a18b8bab40ffb71ebd9cb80d0085"
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
