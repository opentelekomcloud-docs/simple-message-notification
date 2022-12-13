:original_name: smn_ug_0009.html

.. _smn_ug_0009:

Requesting Subscription Confirmation
====================================

Scenarios
---------

If a subscriber does not receive the confirmation message, request confirmation again. You can send a subscription confirmation message to one or more subscription endpoints at a time. For details about how many confirmation messages you can send to one subscriber, see :ref:`Control over Subscription Confirmation Traffic <smn_ug_a4000>`.

To Request Subscription Confirmation
------------------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Subscriptions**.

#. In the subscription list, select one or more subscriptions whose status is **Unconfirmed**.

#. Click **Request Confirmation** above the subscription list to send confirmation messages.

#. The subscribers confirm their subscriptions.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see :ref:`Control over Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  After you add a subscription, SMN sends a confirmation message to the subscription endpoint. The message contains a link for confirming the subscription. The subscription confirmation link is valid within 48 hours. Confirm the subscription on your mobile phone, mailbox, or other endpoints in time.

.. |image1| image:: /_static/images/en-us_image_0259222476.png
