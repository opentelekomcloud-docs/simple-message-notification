:original_name: smn_api_52004.html

.. _smn_api_52004:

Deleting a Subscription
=======================

Description
-----------

-  API name

   Unsubscribe

-  Function

   Delete a specified subscription.

URI
---

-  URI format

   DELETE /v2/{project_id}/notifications/subscriptions/{subscription_urn}

-  Parameter description

   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                  |
   +==================+=================+=================+==============================================================================================================+
   | project_id       | Yes             | String          | Project ID                                                                                                   |
   |                  |                 |                 |                                                                                                              |
   |                  |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                           |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | subscription_urn | Yes             | String          | Unique resource ID of a topic. You can obtain it according to :ref:`Querying Subscriptions <smn_api_52001>`. |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

Request
-------

Request example

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/subscriptions/urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:2e778e84408e44058e6cbc6d3c377837

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
          "request_id":"f3197b274a6b473a8007eed79e716c30"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
