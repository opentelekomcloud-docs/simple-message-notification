:original_name: smn_api_510001.html

.. _smn_api_510001:

Listing All SMN API Versions
============================

Description
-----------

-  API name

   QueryApiSupportVersions

-  Function

   List all SMN API versions.

URI
---

-  URI format

   GET /

Request
-------

-  Example request

   .. code-block:: text

      GET https://{SMN_Endpoint}/

Response
--------

-  Parameter description

   +-----------+--------------------+-------------------------------------------------------------------------------------------+
   | Parameter | Type               | Description                                                                               |
   +===========+====================+===========================================================================================+
   | versions  | Versions structure | Version object list. For details, see :ref:`Table 1 <smn_api_510001__table219819244718>`. |
   +-----------+--------------------+-------------------------------------------------------------------------------------------+

   .. _smn_api_510001__table219819244718:

   .. table:: **Table 1** Versions structure

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                |
      +=======================+=======================+============================================================================================================+
      | id                    | String                | Version number, for example, **v2**                                                                        |
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
      | links                 | Links structure array | URL of an API. For details, see :ref:`Table 2 <smn_api_510001__table1259118084015>`.                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

   .. _smn_api_510001__table1259118084015:

   .. table:: **Table 2** Links structure

      ========= ====== =========================
      Parameter Type   Description
      ========= ====== =========================
      href      String Shortcut link
      rel       String Shortcut link marker name
      ========= ====== =========================

-  Example response

   .. code-block::

      {
          "versions": [
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
         ]
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
