:original_name: smn_faq_0014.html

.. _smn_faq_0014:

Does SMN Ensure That Messages Are Received by Subscription Endpoints?
=====================================================================

SMN pushes messages to subscription endpoints asynchronously, which does not ensure the timeliness of message delivery. If your service requires quasi-real-time message delivery, exercise caution whether to use SMN.

If a subscription endpoint is accessible, it will receive all messages delivered by SMN.

If an endpoint is inaccessible, SMN saves the undelivered message in a message queue and tries to deliver it six more times. If the message still fails to be delivered, SMN discards it and does not send the information to the publisher that the message delivery failed.

The interval for re-sending an undelivered message varies depending on the length of the message queue.
