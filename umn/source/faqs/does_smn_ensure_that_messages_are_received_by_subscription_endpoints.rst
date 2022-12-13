:original_name: smn_faq_0014.html

.. _smn_faq_0014:

Does SMN Ensure That Messages Are Received by Subscription Endpoints?
=====================================================================

If a subscription endpoint is reachable, it will receive all messages delivered by SMN.

If an endpoint is unreachable, SMN saves the undelivered message in a message queue and tries to deliver it six more times. If the message still fails to be delivered, SMN discards it and does not inform the publisher that the message delivery has failed.

The interval for re-sending an undelivered message varies depending on the length of the message queue. Usually, an undelivered message is processed within several hours. If a queue has too many undelivered messages, those messages will be processed within a day.
