:original_name: smn_ug_a9002.html

.. _smn_ug_a9002:

HTTP/HTTPS Message Format
=========================

Scenario
--------

This section describes the format of messages sent to HTTP or HTTPS endpoints. You can identify messages based on message types in the headers. HTTP/HTTPS message types include: subscription confirmation messages, notification messages, and subscription cancellation messages.

The header of an SMN HTTP/HTTPS message contains the following parameters: **X-SMN-TOPIC-URN**, **X-SMN-MESSAGE-ID**, **X-SMN-MESSAGE-TYPE**, and **X-SMN-SUBSCRIPTION-URN**.

.. table:: **Table 1** HTTP/HTTPS header parameters

   +-----------------------------------+--------------------------------------------------------------+
   | Parameter                         | Description                                                  |
   +===================================+==============================================================+
   | X-SMN-MESSAGE-TYPE                | Indicates the message type, which can be:                    |
   |                                   |                                                              |
   |                                   | -  SubscriptionConfirmation                                  |
   |                                   | -  Notification                                              |
   |                                   | -  UnsubscribeConfirmation                                   |
   +-----------------------------------+--------------------------------------------------------------+
   | X-SMN-MESSAGE-ID                  | Indicates the unique message ID.                             |
   +-----------------------------------+--------------------------------------------------------------+
   | X-SMN-TOPIC-URN                   | Indicates the URN of the topic to which the message belongs. |
   +-----------------------------------+--------------------------------------------------------------+
   | X-SMN-SUBSCRIPTION-URN            | Identifies the subscription endpoint.                        |
   +-----------------------------------+--------------------------------------------------------------+

HTTP/HTTPS Subscription Confirmation Message Format
---------------------------------------------------

After you add an HTTP/HTTPS endpoint, SMN sends a subscription confirmation message to the subscriber. The message body is composed of JSON character strings. The subscriber must obtain the subscription URL (**subscribe_url**) to confirm the subscription. :ref:`Table 2 <smn_ug_a9002__table52870937144241>` describes the JSON strings in detail.

.. _smn_ug_a9002__table52870937144241:

.. table:: **Table 2** HTTP/HTTPS subscription confirmation message body

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                             |
   +===================================+=========================================================================================================================================================================================================================================+
   | type                              | Indicates the message type, the value of which is **SubscriptionConfirmation**.                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature                         | Indicates the signature information.                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                         |
   |                                   | The signature includes the **message**, **message_id**, **subscribe_url**, **timestamp**, **topic_urn**, and **type** fields. For details about signature verification, see :ref:`A.6.3 Message Signature Verification <smn_ug_a9003>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn                         | Indicates the URN of the topic to which the message belongs.                                                                                                                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_id                        | Indicates the unique message ID.                                                                                                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature_version                 | Indicates the signature version, which is currently **V1**.                                                                                                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message                           | Indicates the message content.                                                                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subscribe_url                     | Indicates the URL to be accessed for subscription confirmation.                                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_cert_url                  | Indicates the certificate URL for generating the message signature.                                                                                                                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                         | Indicates the time stamp when the message was initially sent.                                                                                                                                                                           |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example HTTP/HTTPS subscription confirmation message:

.. code-block::

   {
       "signature": "ViE96uGbBkl+S8eWqgebi5KdmRht2U8+Rs88yuyMHq1k4h3jUkcDZ6HCqTqdpJ8nrLcdqETyyEiOQyTszJdU05z+LhfE8jerCCdSbL4zeInVkydHh0kcCRWmORye0/EuQ/gLC1UIXwvUsqbUCPnBRhNFXOeXMOPPCzK+d04xjy4QHd1H/bHxgsY3AlTe0gCFT068Zru7OK6w9aQaY44mXnN3OWGmBmoHyFab5TRXLSQNz/9u/Vj646cQMMaI0PPQ30QzGYD0MtzgDZi12m8jMTHAnMkTEcbLaEgaqmaoEnATSpEcspFKNXv2skwk7rsVakMOISpMH3+qC6RzhETA2A==",
       "topic_urn": "urn:smn:region01:0553db98c800d5192f9bc01232b89622:vpc_status_report_topic",
       "message_id": "d86c201092574e71a3ca85826652c58b",
       "signature_version": "v1",
       "type": "SubscriptionConfirmation",
       "message": "{\"enterpriseProjectId\": \"0\", \"eventTime\": \"2019-08-12 22:40:55.040632\", \"chargingMode\": \"postPaid\", \"cloudserviceType\": \"hws.service.type.bandwidth\", \"eventType\": 1, \"regionId\": \"region01\", \"tenantId\": \"057eefe55400d2742f8cc0017870ceef\", \"resourceType\": \"hws.resource.type.bandwidth\", \"resourceSpecCode\": \"19_bgp\", \"resourceSize\": 10, \"resourceId\": \"e091f1b1-08ef-4e2b-a27e-f85e4c19026a\", \"resouceSizeMeasureId\": 15, \"resourceName\": \"elbauto_2019_08_13_06_40_46\"}",
       "subscribe_url": "https://console.xxx.com/smn/subscription/unsubscribe?subscription_urn=urn:smn:region01:0553db98c800d5192f9bc01232b89622:vpc_status_report_topic:653e212a43884f7188ca656c537e31ce",
       "signing_cert_url": "https://console.xxx.com/smn/SMN_region01_b3974c411807498bb532b3cd6cd65d91.pem",
       "timestamp": "2019-08-12T22:40:56Z"
   }

HTTP/HTTPS Notification Message Format
--------------------------------------

After an HTTP/HTTPS subscriber confirms the subscription, the subscriber can receive notification messages published to the topic. The notification message body is composed of JSON character strings, which are described in :ref:`Table 3 <smn_ug_a9002__table37962339144241>`.

.. _smn_ug_a9002__table37962339144241:

.. table:: **Table 3** HTTP/HTTPS notification message body

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================================================================================================================================+
   | type                              | Indicates the message type, the value of which is **Notification**.                                                                                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature                         | Indicates the signature information.                                                                                                                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                                                     |
   |                                   | The signature includes the **message**, **message_id**, **subject**, **timestamp**, **topic_urn**, and **type** fields. If the **subject** field is empty, the signature is not verified. For details about signature verification, see :ref:`A.6.3 Message Signature Verification <smn_ug_a9003>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subject                           | Message subject                                                                                                                                                                                                                                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn                         | Indicates the URN of the topic to which the message belongs.                                                                                                                                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_id                        | Indicates the unique message ID.                                                                                                                                                                                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature_version                 | Indicates the signature version, which is currently **V1**.                                                                                                                                                                                                                                         |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message                           | Indicates the message content.                                                                                                                                                                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | unsubscribe_url                   | Indicates the URL for canceling a subscription.                                                                                                                                                                                                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_cert_url                  | Indicates the certificate URL for generating the message signature.                                                                                                                                                                                                                                 |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                         | Indicates the time stamp when the message was initially sent.                                                                                                                                                                                                                                       |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example HTTP(S) notification message:

.. code-block::

   {
       "signature": "ViE96uGbBkl+S8eWqgebi5KdmRht2U8+Rs88yuyMHq1k4h3jUkcDZ6HCqTqdpJ8nrLcdqETyyEiOQyTszJdU05z+LhfE8jerCCdSbL4zeInVkydHh0kcCRWmORye0/EuQ/gLC1UIXwvUsqbUCPnBRhNFXOeXMOPPCzK+d04xjy4QHd1H/bHxgsY3AlTe0gCFT068Zru7OK6w9aQaY44mXnN3OWGmBmoHyFab5TRXLSQNz/9u/Vj646cQMMaI0PPQ30QzGYD0MtzgDZi12m8jMTHAnMkTEcbLaEgaqmaoEnATSpEcspFKNXv2skwk7rsVakMOISpMH3+qC6RzhETA2A==",
       "topic_urn": "urn:smn:region01:0553db98c800d5192f9bc01232b89622:vpc_status_report_topic",
       "message_id": "d86c201092574e71a3ca85826652c58b",
       "signature_version": "v1",
       "type": "Notification",
       "message": "{\"enterpriseProjectId\": \"0\", \"eventTime\": \"2019-08-12 22:40:55.040632\", \"chargingMode\": \"postPaid\", \"cloudserviceType\": \"hws.service.type.bandwidth\", \"eventType\": 1, \"regionId\": \"region01\", \"tenantId\": \"057eefe55400d2742f8cc0017870ceef\", \"resourceType\": \"hws.resource.type.bandwidth\", \"resourceSpecCode\": \"19_bgp\", \"resourceSize\": 10, \"resourceId\": \"e091f1b1-08ef-4e2b-a27e-f85e4c19026a\", \"resouceSizeMeasureId\": 15, \"resourceName\": \"elbauto_2019_08_13_06_40_46\"}",
       "unsubscribe_url": "https://console.xxx.com/smn/subscription/unsubscribe?subscription_urn=urn:smn:region01:0553db98c800d5192f9bc01232b89622:vpc_status_report_topic:653e212a43884f7188ca656c537e31ce",
       "signing_cert_url": "https://console.xxx.com/smn/SMN_region01_b3974c411807498bb532b3cd6cd65d91.pem",
       "timestamp": "2019-08-12T22:40:56Z"
   }

HTTP/HTTPS Subscription Cancellation Message Format
---------------------------------------------------

After an HTTP/HTTPS subscription is canceled, the subscriber receives a subscription cancellation message sent by SMN. The message body is composed of JSON character strings, which are described in :ref:`Table 4 <smn_ug_a9002__table64442359144241>`.

.. _smn_ug_a9002__table64442359144241:

.. table:: **Table 4** HTTP/HTTPS subscription cancellation message body

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                             |
   +===================================+=========================================================================================================================================================================================================================================+
   | type                              | Indicates the message type, the value of which is **UnsubscribeConfirmation**.                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature                         | Indicates the signature information.                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                         |
   |                                   | The signature includes the **message**, **message_id**, **subscribe_url**, **timestamp**, **topic_urn**, and **type** fields. For details about signature verification, see :ref:`A.6.3 Message Signature Verification <smn_ug_a9003>`. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn                         | Indicates the URN of the topic to which the message belongs.                                                                                                                                                                            |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_id                        | Indicates the unique message ID.                                                                                                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signature_version                 | Indicates the signature version, which is currently **V1**.                                                                                                                                                                             |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message                           | Indicates the message content.                                                                                                                                                                                                          |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subscribe_url                     | Indicates the URL for a re-subscription.                                                                                                                                                                                                |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | signing_cert_url                  | Indicates the certificate URL for generating the message signature.                                                                                                                                                                     |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                         | Indicates the time stamp when the message was initially sent.                                                                                                                                                                           |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example HTTP(S) message for canceling a subscription:

.. code-block::

   {
       "signature": "ViE96uGbBkl+S8eWqgebi5KdmRht2U8+Rs88yuyMHq1k4h3jUkcDZ6HCqTqdpJ8nrLcdqETyyEiOQyTszJdU05z+LhfE8jerCCdSbL4zeInVkydHh0kcCRWmORye0/EuQ/gLC1UIXwvUsqbUCPnBRhNFXOeXMOPPCzK+d04xjy4QHd1H/bHxgsY3AlTe0gCFT068Zru7OK6w9aQaY44mXnN3OWGmBmoHyFab5TRXLSQNz/9u/Vj646cQMMaI0PPQ30QzGYD0MtzgDZi12m8jMTHAnMkTEcbLaEgaqmaoEnATSpEcspFKNXv2skwk7rsVakMOISpMH3+qC6RzhETA2A==",
       "topic_urn": "urn:smn:region01:0553db98c800d5192f9bc01232b89622:vpc_status_report_topic",
       "message_id": "d86c201092574e71a3ca85826652c58b",
       "signature_version": "v1",
       "type": "UnsubscribeConfirmation",
       "message": "{\"enterpriseProjectId\": \"0\", \"eventTime\": \"2019-08-12 22:40:55.040632\", \"chargingMode\": \"postPaid\", \"cloudserviceType\": \"hws.service.type.bandwidth\", \"eventType\": 1, \"regionId\": \"region01\", \"tenantId\": \"057eefe55400d2742f8cc0017870ceef\", \"resourceType\": \"hws.resource.type.bandwidth\", \"resourceSpecCode\": \"19_bgp\", \"resourceSize\": 10, \"resourceId\": \"e091f1b1-08ef-4e2b-a27e-f85e4c19026a\", \"resouceSizeMeasureId\": 15, \"resourceName\": \"elbauto_2019_08_13_06_40_46\"}",
       "subscribe_url": "https://console.xxx.com/smn/subscription/unsubscribe?subscription_urn=urn:smn:region01:0553db98c800d5192f9bc01232b89622:vpc_status_report_topic:653e212a43884f7188ca656c537e31ce",
       "signing_cert_url": "https://console.xxx.com/smn/SMN_region01_b3974c411807498bb532b3cd6cd65d91.pem",
       "timestamp": "2019-08-12T22:40:56Z"
   }
