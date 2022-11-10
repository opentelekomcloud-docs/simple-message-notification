:original_name: smn_ug_0010.html

.. _smn_ug_0010:

Canceling a Subscription
========================

Scenario
--------

After you add subscriptions to a topic, the subscribers receive a confirmation message and need to confirm their subscriptions to receive notification messages published to the topic. If the subscribers do not want to receive notifications from a topic any more, they can choose to cancel subscriptions.

To Cancel a Subscription
------------------------

A subscriber can choose to cancel the subscription based on the protocol of the subscription endpoint:

-  SMS: SMN does not provide a link to unsubscribe in SMS notification messages because of the message length limit. To cancel an SMS subscription, the subscriber needs to access the link provided in the subscription confirmation message and cancels the subscription on the web page.
-  Email: SMN encloses a link to unsubscribe in email notifications. The subscriber can cancel the subscription by clicking the link. After the subscriber has canceled the subscription, SMN re-sends a subscription confirmation email which is valid for 48 hours, so that the subscriber can re-subscribe to the topic if they clicked the link by mistake.
-  HTTP/HTTPS: SMN provides a link to unsubscribe in the HTTP/HTTPS message body. The subscriber can cancel the subscription by clicking the link. After the subscriber has canceled the subscription, the system returns **200** over HTTP and re-sends a subscription confirmation message which is valid for 48 hours, in case the subscriber has clicked the link by mistake. For details about the HTTP/HTTPS message header and body, see section :ref:`A.6.1 Introduction <smn_ug_a9001>`.
