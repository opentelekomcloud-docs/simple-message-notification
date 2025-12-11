:original_name: smn_api_63001.html

.. _smn_api_63001:

Exception Response
==================

-  Parameter description

   ========== ====== ====================================================
   Parameter  Type   Description
   ========== ====== ====================================================
   request_id String Request ID
   code       String For details, see :ref:`Error Codes <smn_api_64000>`.
   message    String For details, see :ref:`Error Codes <smn_api_64000>`.
   ========== ====== ====================================================

-  Example

   .. code-block::

      {
          "request_id": "aad0860d089c482b943971f802a6718e",
          "code": "SMN.0006",
          "message": "Topic not found."
      }
