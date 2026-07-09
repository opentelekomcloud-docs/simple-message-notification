:original_name: smn_api_93000.html

.. _smn_api_93000:

Deleting Message Filter Policies for Subscriptions
==================================================

Function
--------

This API is used to delete message filter policies for subscriptions.

URI
---

DELETE /v2/{project_id}/notifications/subscriptions/filter_polices

For details, see :ref:`Table 1 <smn_api_93000__topic1391000051>`.

.. _smn_api_93000__topic1391000051:

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | It can be obtained by calling the IAM API that is used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameter

   +-------------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type             | Description                                                                                                         |
   +===================+===========+==================+=====================================================================================================================+
   | subscription_urns | Yes       | Array of strings | Unique subscription identifiers. You can obtain them by referring to :ref:`Querying Subscriptions <smn_api_52001>`. |
   +-------------------+-----------+------------------+---------------------------------------------------------------------------------------------------------------------+

Response
--------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------+---------------------------------------------------------------------------+-------------------------+
   | Parameter    | Type                                                                      | Description             |
   +==============+===========================================================================+=========================+
   | request_id   | String                                                                    | Unique request ID       |
   +--------------+---------------------------------------------------------------------------+-------------------------+
   | batch_result | Array of :ref:`BatchResult <smn_api_93000__response_batchresult>` objects | Batch processing result |
   +--------------+---------------------------------------------------------------------------+-------------------------+

.. _smn_api_93000__response_batchresult:

.. table:: **Table 5** BatchResult

   ================ ====== ================
   Parameter        Type   Description
   ================ ====== ================
   code             String Returned code
   message          String Returned message
   subscription_urn String Subscription URN
   ================ ====== ================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

Example Request
---------------

Delete message filter policies for subscriptions.

.. code-block:: text

   DELETE https://{SMN_Endpoint}/v2/{project_id}/notifications/subscriptions/filter_polices

   {
     "subscription_urns" : [ "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:2e778e84408e44058e6cbc6d3c377837" ]
   }

Example Response
----------------

**Status code: 200**

OK

.. code-block::

   {
     "request_id" : "6a63a18b8bab40ffb71ebd9cb80d0085"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
400         Bad Request
403         Unauthorized
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
