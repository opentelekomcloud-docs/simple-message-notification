:original_name: en-us_topic_0043961402.html

.. _en-us_topic_0043961402:

Adding a Subscription to a Topic
================================

Scenarios
---------

To deliver messages published to a topic to subscription endpoints, you must add the endpoints to the topic.

To Add a Subscription
---------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Locate the topic that you want to add a subscription to. In the **Operation** column, choose **More** > **Add Subscription**.

   The **Add Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0095665399.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the subscription protocol and endpoints. You can enter 10 endpoints at most, each on a separate line.

   -  Email

      Enter a valid email address, for example, **username@example.com**.

      Subscribers will receive a subscription confirmation email valid in 48 hours and must confirm the subscription to receive messages published to the topic.

   -  HTTP/HTTPS

      Enter a public network URL, for example, **http://example.com/notification/action**. HTTP/HTTPS subscribers must confirm their subscriptions. For details about HTTP/HTTPS messages, see :ref:`Introduction <smn_ug_a9001>`.

   -  SMS

      Enter a valid mobile number preceded by a plus sign (+) and a country code .Example: +4900000000

      Subscribers will receive a subscription confirmation message valid in 48 hours and must confirm the subscription to receive messages published to the topic.

   -  DMS

      Subscription endpoints are message queues. This type of subscriptions does not require confirmation. Click |image2| to select subscription endpoints. When you select DMS queues, grant the **ProduceMessages** permission to SMN in the queue policy. For details, see section "Managing Queue Policies" in the *Distributed Message Service User Guide*.

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see :ref:`Control over Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  After you add a subscription, SMN sends a confirmation message to the subscription endpoint. The message contains a link for confirming the subscription. The subscription confirmation link is valid within 48 hours. Confirm the subscription on your mobile phone, mailbox, or other endpoints in time.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0148410841.png
