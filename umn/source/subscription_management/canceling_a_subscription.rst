:original_name: smn_ug_0010.html

.. _smn_ug_0010:

Canceling a Subscription
========================

Scenarios
---------

After you add subscriptions to a topic, the subscribers receive a confirmation message and need to confirm their subscriptions to receive notification messages published to the topic. If the subscribers no longer want to receive notifications from a topic, they can choose to cancel subscriptions.

.. caution::

   The subscription management capability of SMN is open to subscribers. You must keep your subscription links secure to avoid being unable to receiving notifications or receiving unexpected notifications.


Canceling a Subscription
------------------------

A subscriber can choose to cancel the subscription based on the protocol of the subscription endpoint:

-  SMS: SMN does not provide a link to unsubscribe in an SMS notification message because of the message length limit. To cancel an SMS subscription, the subscriber needs to access the link provided in the subscription confirmation message and cancels the subscription on the web page.
-  Email: SMN encloses a link to unsubscribe in an email notification. The subscriber can cancel the subscription by clicking the link. After the subscriber cancels the subscription, SMN re-sends a subscription confirmation email which is valid for 48 hours, so that the subscriber can re-subscribe to the topic if they clicked the link by mistake.
-  HTTP/HTTPS: SMN sends a message that contains a link to cancel the subscription to a specified URL. The subscriber can cancel the subscription by accessing the link. After that, the system returns **200** over HTTPS and re-sends a subscription confirmation message which is valid for 48 hours to the URL, in case the subscriber has canceled the subscription by mistake. For details about the HTTP/HTTPS message header and body, see :ref:`Introduction <smn_ug_a9001>`.
