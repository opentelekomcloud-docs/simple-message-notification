:original_name: smn_api_91000.html

.. _smn_api_91000:

Creating Message Filter Policies for Subscriptions
==================================================

Function
--------

This API is used to create message filter policies for subscriptions.

URI
---

POST /v2/{project_id}/notifications/subscriptions/filter_polices

For details, see :ref:`Table 1 <smn_api_91000__topic1371000051>`.

.. _smn_api_91000__topic1371000051:

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

   +-----------+-----------+------------------------------------------------------------------+------------------------+
   | Parameter | Mandatory | Type                                                             | Description            |
   +===========+===========+==================================================================+========================+
   | polices   | Yes       | Array of :ref:`polices <smn_api_91000__request_polices>` objects | Policies to be created |
   +-----------+-----------+------------------------------------------------------------------+------------------------+

.. _smn_api_91000__request_polices:

.. table:: **Table 4** polices

   +------------------+-----------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type                                                                                                 | Description                                                                                                           |
   +==================+===========+======================================================================================================+=======================================================================================================================+
   | subscription_urn | Yes       | String                                                                                               | Unique identifier of a subscription. You can obtain it by referring to :ref:`Querying Subscriptions <smn_api_52001>`. |
   +------------------+-----------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | filter_polices   | Yes       | Array of :ref:`SubscriptionsFilterPolicy <smn_api_91000__request_subscriptionsfilterpolicy>` objects | Filter policies. Policy names must be unique.                                                                         |
   +------------------+-----------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+

.. _smn_api_91000__request_subscriptionsfilterpolicy:

.. table:: **Table 5** SubscriptionsFilterPolicy

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                                        |
   +=================+=================+==================+====================================================================================================================================================================================================================================================================+
   | name            | Yes             | String           | Filter policy name                                                                                                                                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | The name can contain 1 to 32 characters, including lowercase letters, digits, and underscores (_). It cannot start with **smn\_** or an underscore, cannot end with an underscore, and cannot contain consecutive underscores.                                     |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | string_equals   | Yes             | Array of strings | An array of strings for exact matching. The array can contain 1 to 10 strings. The array must contain 1 to 10 unique elements. Each element must be non-null, non-empty, and have 1 to 32 characters. Allowed characters are letters, digits, and underscores (_). |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +--------------+---------------------------------------------------------------------------+-------------------------+
   | Parameter    | Type                                                                      | Description             |
   +==============+===========================================================================+=========================+
   | request_id   | String                                                                    | Unique request ID       |
   +--------------+---------------------------------------------------------------------------+-------------------------+
   | batch_result | Array of :ref:`BatchResult <smn_api_91000__response_batchresult>` objects | Batch processing result |
   +--------------+---------------------------------------------------------------------------+-------------------------+

.. _smn_api_91000__response_batchresult:

.. table:: **Table 7** BatchResult

   ================ ====== ================
   Parameter        Type   Description
   ================ ====== ================
   code             String Returned code
   message          String Returned message
   subscription_urn String Subscription URN
   ================ ====== ================

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== =====================
   Parameter  Type   Description
   ========== ====== =====================
   request_id String Unique request ID
   code       String Service error code
   message    String Service error message
   ========== ====== =====================

Example Request
---------------

Create message filter policies for subscriptions.

.. code-block:: text

   POST https://{SMN_Endpoint}/v2/{project_id}/notifications/subscriptions/filter_polices

   {
     "polices" : [ {
       "subscription_urn" : "urn:smn:regionId:762bdb3251034f268af0e395c53ea09b:test_topic_v1:2e778e84408e44058e6cbc6d3c377837",
       "filter_polices" : [ {
         "name" : "alarm",
         "string_equals" : [ "os", "process" ]
       }, {
         "name" : "service",
         "string_equals" : [ "api", "db" ]
       } ]
     } ]
   }

Example Response
----------------

**Status code: 200**

OK

.. code-block::

   {
     "request_id" : "be368401641b406d8c28a79915ba3589",
     "batch_result" : [ {
       "code" : "SMN.00011027",
       "message" : "Parameter: subscription_urn is invalid.",
       "subscription_urn" : "urn:smn:regionId:98386b0630aa41d990d4729497fcd7ba:test:90b22be1efab4cd6924703c5b228e59f"
     }, {
       "code" : "SMN.00011027",
       "message" : "Parameter: subscription_urn is invalid.",
       "subscription_urn" : "urn:smn:regionId:98386b0630aa41d990d4729497fcd7ba:test:c872b769e60d45f682f1da44eb4dbee3"
     } ]
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
