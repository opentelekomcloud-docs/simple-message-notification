:original_name: smn_ug_a9002.html

.. _smn_ug_a9002:

HTTP or HTTPS Message Format
============================

Scenarios
---------

.. caution::

   #. When receiving HTTP or HTTPS messages sent by SMN, refer to the industry standards for the common name (CN) of the terminal certificate. Some special characters may cause HTTPS message sending failures.
   #. Unencrypted HTTP messages transmitted on the Internet may cause information leakage. Therefore, select the HTTPS protocol when you add subscriptions.

This section describes the format of messages sent to HTTP or HTTPS endpoints. You can identify messages based on message types in the headers. HTTP/HTTPS message types include: subscription confirmation messages, notification messages, and subscription cancellation messages. POST is used for HTTP/HTTPS messages.

The header of an SMN HTTP/HTTPS message contains the following parameters: **X-SMN-MESSAGE-TYPE**, **X-SMN-MESSAGE-ID**, and **X-SMN-TOPIC-URN**.

.. table:: **Table 1** HTTP/HTTPS header fields

   +-----------------------------------+--------------------------------------------------------+
   | Parameter                         | Description                                            |
   +===================================+========================================================+
   | X-SMN-MESSAGE-TYPE                | Indicates the message type, which can be:              |
   |                                   |                                                        |
   |                                   | -  **SubscriptionConfirmation**                        |
   |                                   | -  **Notification**                                    |
   |                                   | -  **UnsubscribeConfirmation**                         |
   +-----------------------------------+--------------------------------------------------------+
   | X-SMN-MESSAGE-ID                  | Indicates the unique message ID.                       |
   +-----------------------------------+--------------------------------------------------------+
   | X-SMN-TOPIC-URN                   | Indicates the URN of the topic the message belongs to. |
   +-----------------------------------+--------------------------------------------------------+

.. note::

   The HTTP/HTTPS header fields must be in lowercase.

HTTP/HTTPS Subscription Confirmation Message Format
---------------------------------------------------

After you add an HTTP/HTTPS endpoint, SMN sends a subscription confirmation message to the subscriber. The message body is composed of JSON character strings. The subscriber must obtain the subscription URL (**subscribe_url**) to confirm the subscription. :ref:`Table 2 <smn_ug_a9002__table52870937144241>` describes the JSON field in detail.

.. _smn_ug_a9002__table52870937144241:

.. table:: **Table 2** HTTP/HTTPS subscription confirmation message body

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                       |
   +===================================+===================================================================================================================================================================================================================================+
   | type                              | Indicates the message type, which is **SubscriptionConfirmation**.                                                                                                                                                                |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature                         | Indicates the signature information.                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                   |
   |                                   | The signature includes the **message**, **message_id**, **subscribe_url**, **timestamp**, **topic_urn**, and **type** fields. For details about signature verification, see :ref:`Message Signature Verification <smn_ug_a9003>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn                         | Indicates the URN of the topic the message belongs to.                                                                                                                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_id                        | Indicates the unique message ID.                                                                                                                                                                                                  |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature_version                 | Indicates the signature version, which is **V1**.                                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message                           | Indicates the message content.                                                                                                                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subscribe_url                     | Indicates the URL to be accessed for subscription confirmation.                                                                                                                                                                   |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_cert_url                  | Indicates the certificate URL for a message signature. It can be directly accessed without authentication.                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                         | Indicates the time stamp when the message was initially sent.                                                                                                                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example HTTP/HTTPS subscription confirmation message:

.. code-block::

   {
       "subscribe_url": "https://console.******.com/smn/subscription/confirm?token=0a419ac94f80f2c62f14c01e34ae5dfcf6b0b92ef46241218eaae5b4cb90d5d423cf104593284665a1f98691b1576976785114fb4408450e8de153b9f1******&topic_urn=urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******&region=region01&region_id=region01",
       "signature": "W/DQSiqpRkY6En0jNaFtCYOpmUjMhzoJIdMPLhnRv37iPzNhH+SxlievFoUIyS29z7Ig4hL/ECWNfGrRhTqoasiAeOaXOjoRNoQ73YfyqWm7x7OdX+2c202zxaOS5GcsUHohxAS+wCYd6W6aVhx6eQpWzpzLwrGgE+iPmsd5I00HXIBeZEeBx/VuoqkPyBDnSvGNNDTJ2gw+fL7XuKqf/DUUjjI8dkPsp3gAcETe/XMgf3UTMFDvLLrq2fAZVhr/jMR/9m81PwuDs1k9i3iBxT67afzmQ1AhY/a/ayQX7Fmwf/FBpehG1o8e98lXAZFS2nzhvTpttawUFG8Z82******",
       "topic_urn": "urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******",
       "message_id": "54bb04eddfc842e9b44ca36393f77cd3",
       "signature_version": "v1",
       "type": "SubscriptionConfirmation",
       "message": "You are invited to subscribe to topic: urn:smn:regionid:0a419ac94f80f2c62f14c01e34******:test_******. To confirm this subscription, please visit the subscribe_url included in this message. The subscribe_url is valid only within 48 hours.",
       "signing_cert_url": "https://smn.region01.******.com/smn/SMN_region01_3190c26a56fb435f9882e3435b******.pem",
       "timestamp": "2024-07-10T09:43:44Z"
   }

HTTP/HTTPS Notification Message Format
--------------------------------------

After an HTTP/HTTPS subscriber confirms the subscription, the subscriber can receive notification messages published to the topic. The notification message body is composed of JSON character strings, which are described in :ref:`Table 3 <smn_ug_a9002__table37962339144241>`.

.. _smn_ug_a9002__table37962339144241:

.. table:: **Table 3** HTTP/HTTPS notification message body

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                   |
   +===================================+===============================================================================================================================================================================================================================================================================================+
   | type                              | Indicates the message type, which is **Notification**.                                                                                                                                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature                         | Indicates the signature information.                                                                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                                                                               |
   |                                   | The signature includes the **message**, **message_id**, **subject**, **timestamp**, **topic_urn**, and **type** fields. If the **subject** field is empty, the signature is not verified. For details about signature verification, see :ref:`Message Signature Verification <smn_ug_a9003>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subject                           | Indicates the message subject.                                                                                                                                                                                                                                                                |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn                         | Indicates the URN of the topic the message belongs to.                                                                                                                                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_id                        | Indicates the unique message ID.                                                                                                                                                                                                                                                              |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature_version                 | Indicates the signature version, which is **V1**.                                                                                                                                                                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message                           | Indicates the message content.                                                                                                                                                                                                                                                                |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | unsubscribe_url                   | Indicates the URL for canceling a subscription.                                                                                                                                                                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_cert_url                  | Indicates the certificate URL for generating the message signature.                                                                                                                                                                                                                           |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                         | Indicates the time stamp when the message was initially sent.                                                                                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example HTTP/HTTPS notification message:

.. code-block::

   {
       "signature": "WmSQ2/0kp2v2u2T33lMqKYrrLxnJoW2NHqIy5QowDuHH3y+HvhCNlCgHDUiAGpb3suCXJm16hWF+EJAYR+tPaTY1q0N3p0p+oBbhlD30fOTxRNsEWRAg73k4qArmQajhdDZOtd57xelQiNhzl2r6iCs0en4kR2iY78zZM/9caZQGBTlNcjkd2lyXYP6aSc7MOgxTsYrRus0A6yipD3zsUA7TvTdfsauAe2hZLR5W0l+um+S3ytT7sA1CMlIJPBXHP5WlqS4iMAeivmufZv7T+G43DbwWfw/seKnK6uFKWd214oqsY2/oLY3C4dcyLdvsy0/7/W8zvxXbgHeSL4******",
       "subject": "SMN",
       "topic_urn": "urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******",
       "message_id": "d84bd6629ef04513ad2e37bffd6e17cb",
       "signature_version": "v1",
       "type": "Notification",
       "message": "{\"enterpriseProjectId\": \"0\", \"eventTime\": \"2019-08-12 22:40:55.040632\", \"chargingMode\": \"postPaid\", \"cloudserviceType\": \"xxx.service.type.bandwidth\", \"eventType\": 1, \"regionId\": \"region01\", \"tenantId\": \"057eefe55400d2742f8cc00178******\", \"resourceType\": \"xxx.resource.type.bandwidth\", \"resourceSpecCode\": \"19_bgp\", \"resourceSize\": 10, \"resourceId\": \"e091f1b1-08ef-4e2b-a27e-f85e4c******\", \"resouceSizeMeasureId\": 15, \"resourceName\": \"elbauto_2019_08_13_06_40_46\"}",
       "unsubscribe_url": "https://console.******.com/smn/subscription/unsubscribe?region=region01&region_id=region01&subscription_urn=urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******:23cf104593284665a1f98691b1******",
       "signing_cert_url": "https://smn.region01.******.com/smn/SMN_region01_3190c26a56fb435f9882e3435b******.pem",
       "timestamp": "2024-07-10T09:45:00Z"
   }

HTTP/HTTPS Subscription Cancellation Message Format
---------------------------------------------------

After an HTTP/HTTPS subscription is canceled, the subscriber receives a subscription cancellation message sent by SMN. The message body is composed of JSON character strings, which are described in :ref:`Table 4 <smn_ug_a9002__table64442359144241>`.

.. _smn_ug_a9002__table64442359144241:

.. table:: **Table 4** Parameters of HTTP/HTTPS subscription cancellation message format

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                       |
   +===================================+===================================================================================================================================================================================================================================+
   | type                              | Indicates the message type. Its value is **UnsubscribeConfirmation**.                                                                                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature                         | Indicates the signature information.                                                                                                                                                                                              |
   |                                   |                                                                                                                                                                                                                                   |
   |                                   | The signature includes the **message**, **message_id**, **subscribe_url**, **timestamp**, **topic_urn**, and **type** fields. For details about signature verification, see :ref:`Message Signature Verification <smn_ug_a9003>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn                         | Indicates the URN of the topic the message belongs to.                                                                                                                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_id                        | Indicates the unique message ID.                                                                                                                                                                                                  |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature_version                 | Indicates the signature version, which is **V1**.                                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message                           | Indicates the message content.                                                                                                                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subscribe_url                     | Indicates the URL for a re-subscription.                                                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_cert_url                  | Indicates the certificate URL for generating the message signature.                                                                                                                                                               |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                         | Indicates the time stamp when the message was initially sent.                                                                                                                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example HTTP/HTTPS message for canceling a subscription:

.. code-block::

   {
       "signature": "ViE96uGbBkl+S8eWqgebi5KdmRht2U8+Rs88yuyMHq1k4h3jUkcDZ6HCqTqdpJ8nrLcdqETyyEiOQyTszJdU05z+LhfE8jerCCdSbL4zeInVkydHh0kcCRWmORye0/EuQ/gLC1UIXwvUsqbUCPnBRhNFXOeXMOPPCzK+d04xjy4QHd1H/bHxgsY3AlTe0gCFT068Zru7OK6w9aQaY44mXnN3OWGmBmoHyFab5TRXLSQNz/9u/Vj646cQMMaI0PPQ30QzGYD0MtzgDZi12m8jMTHAnMkTEcbLaEgaqmaoEnATSpEcspFKNXv2skwk7rsVakMOISpMH3+qC6RzhE******",
       "topic_urn": "urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******",
       "message_id": "d86c201092574e71a3ca85826652c58b",
       "signature_version": "v1",
       "type": "UnsubscribeConfirmation",
       "message": "You are unsubscribed from topic: urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******. To subscribe to this topic again, please visit the subscribe_url included in this message. The subscribe_url is valid only within 48 hours.",
       "subscribe_url": "https://console.******.com/smn/subscription/confirm?token=0a419ac94f80f2c62f14c01e34ae5dfcf6b0b92ef46241218eaae5b4cb90d5d423cf104593284665a1f98691b1576976785114fb4408450e8de153b9f1******&topic_urn=urn:smn:region01:0a419ac94f80f2c62f14c01e34******:test_******&region=region01&region_id=region01",
       "signing_cert_url": "https://smn.region01.******.com/smn/SMN_region01_3190c26a56fb435f9882e3435b******.pem",
       "timestamp": "2024-07-10T11:45:00Z"
   }
