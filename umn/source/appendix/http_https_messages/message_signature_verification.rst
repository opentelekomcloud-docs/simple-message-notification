:original_name: smn_ug_a9003.html

.. _smn_ug_a9003:

Message Signature Verification
==============================

Scenarios
---------

To ensure message security, SMN provides signature authentication for HTTP/HTTPS subscription confirmation messages, subscription cancellation messages, and notification messages. After you receive HTTP/HTTPS messages, check them based on the signatures.

Procedure
---------

After receiving an HTTP/HTTPS message, check it with the following procedure:

#. Verify the key-value pairs (which vary depending on the message type) contained in the message signature. For details, see :ref:`Signature Strings for Different Message Types <smn_ug_a9003__section39070097101940>`.
#. Download the X509 certificate from the certificate URL (**signing_cert_url**) contained in the message.

   .. note::

      The request to download the certificate is always sent over HTTPS. When you download a certificate, verify the identity of the certificate server.

#. Extract the public key from the X509 certificate for verifying the message reliability and integrity.
#. Determine which method will be used to verify the signature based on the message type (the **type** field in the message).
#. Create signature strings. Obtain the signature parameters from the message and sort them in alphabetical order. Each parameter occupies a line, with its value following in the next line.

.. _smn_ug_a9003__section39070097101940:

**Signature Strings for Different Message Types**
-------------------------------------------------

#. Notification messages

   -  A notification message signature must contain the following parameters (If the value of **subject** is empty, do not include it in the signature):

      .. code-block::

         message
         message_id
         subject
         timestamp
         topic_urn
         type

   -  For example, the signature information for a notification message is as follows:

      .. note::

         Each parameter occupies a line, with its value following in the next line.

      .. code-block::

         message
         My test message
         message_id
         88c726942175432bac921eafd0036163
         subject
         demo
         timestamp
         2016-08-15T07:29:16Z
         topic_urn
         urn:smn:regionId:74dc9e44d0cc4573adfce91cdfdd3ba9:xxxx
         type
         Notification

#. Subscription confirmation and subscription cancellation messages

   -  A subscription confirmation or subscription cancellation message signature must contain the following parameters:

      .. code-block::

         message
         message_id
         subscribe_url
         timestamp
         topic_urn
         type

   -  For example, the signature information for a subscription confirmation message is as follows:

      .. note::

         Each parameter occupies a line, with its value following in the next line.

      .. code-block::

         message
         You are invited to subscribe to topic: urn:smn:regionId:d91989905b8449b896f3a4f0ad57222d:demo. To confirm this subscription, Please visit the following SubscribeURL in this message.
         message_id
         def5c309cbff44d5a870787ed937edf8
         subscribe_url
         https://IP address/smn/subscription/confirm?Region ID&Token&Topic URN:demo
         timestamp
         2016-08-15T07:29:16Z
         topic_urn
         urn:smn:regionId:d91989905b8449b896f3a4f0ad57222d:demo
         type
         SubscriptionConfirmation
