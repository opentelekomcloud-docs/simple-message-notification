:original_name: smn_api_55001.html

.. _smn_api_55001:

Sending a Transactional SMS Message to a Phone Number
=====================================================

Description
-----------

.. note::

   Direct SMS messaging is not available to new users. If you want to use these APIs, go to **Cloud Communications** > **Message&SMS**.

-  API name

   SmsPublish

-  Function

   Send a transactional SMS message to a specified phone number, usually used for verification code or notification.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/sms

-  Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================+
   | endpoint        | Yes             | String          | Phone number                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                    |
   |                 |                 |                 | The phone number must be preceded by a plus sign (+) and a country code.                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | message         | Yes             | String          | SMS message content                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                    |
   |                 |                 |                 | If the content exceeds 256 bytes, the system will divide it into multiple messages, each containing 256 bytes at most and send only the first two. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/sms
      {
         "endpoint": "+00111****1990",
         "message": "SMS message test"
      }

Response
--------

-  Parameter description

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   message_id String Message ID, which is unique
   ========== ====== ===========================

-  Example response

   .. code-block::

      {
         "message_id": "bf94b63a5dfb475994d3ac34664e24f2",
         "request_id": "9974c07f6d554a6d827956acbeb4be5f"
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
