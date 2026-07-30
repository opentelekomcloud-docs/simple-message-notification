:original_name: smn_api_510002.html

.. _smn_api_510002:

Querying the SMN API v2 Version
===============================

Function
--------

Query the SMN API v2 version information.

URI
---

GET /{api_version}

For details, see :ref:`Table 1 <smn_api_510002__table1952532171110>`.

.. _smn_api_510002__table1952532171110:

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+-----------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                             |
   +=================+=================+=================+=========================================+
   | api_version     | Yes             | String          | Version to be queried                   |
   |                 |                 |                 |                                         |
   |                 |                 |                 | .. note::                               |
   |                 |                 |                 |                                         |
   |                 |                 |                 |    Currently, only **v2** is supported. |
   +-----------------+-----------------+-----------------+-----------------------------------------+

Request
-------

None

Response
--------

:ref:`Table 2 <smn_api_510002__en-us_topic_0118694332_table26328706>` describes the response parameters.

.. _smn_api_510002__en-us_topic_0118694332_table26328706:

.. table:: **Table 2** Response parameters

   ========= ====== ===================
   Parameter Type   Description
   ========= ====== ===================
   version   Object Version information
   ========= ====== ===================

.. table:: **Table 3** Description of the **version** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                |
   +=======================+=======================+============================================================================================================+
   | id                    | String                | Version number, for example, **v2**                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | links                 | Links structure array | URL of an API. For details, see :ref:`Table 4 <smn_api_510002__table864210364409>`.                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | min_version           | String                | Minimum micro-version number. If the APIs do not support micro-versions, no information will be returned.  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | status                | String                | Version status, which can be the following:                                                                |
   |                       |                       |                                                                                                            |
   |                       |                       | -  **CURRENT**: widely used version                                                                        |
   |                       |                       | -  **SUPPORTED**: earlier version that is still supported                                                  |
   |                       |                       | -  **DEPRECATED**: deprecated version that may be deleted later                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Version release time, which must be UTC time. For example, the release time of v2 is 2014-06-28T12:20:21Z. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | version               | String                | Maximum micro-version number. If the APIs do not support micro-versions, no information will be returned.  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

.. _smn_api_510002__table864210364409:

.. table:: **Table 4** Links structure

   ========= ====== =========================
   Parameter Type   Description
   ========= ====== =========================
   href      String Shortcut link
   rel       String Shortcut link marker name
   ========= ====== =========================

Example Request
---------------

.. code-block:: text

   GET https://{SMN_Endpoint}/v2

Example Response
----------------

.. code-block::

   {
       "version":
           {
               "id": "v2",
               "links": [
                   {
                       "href": "https://127.0.0.1/v2",
                       "rel": "self"
                   }
               ],
               "min_version": "",
               "status": "CURRENT",
               "updated": "2018-09-19T00:00:00Z",
               "version": ""
           }
   }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
