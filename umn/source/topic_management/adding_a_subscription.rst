:original_name: en-us_topic_0043961402.html

.. _en-us_topic_0043961402:

Adding a Subscription
=====================

Scenario
--------

To deliver messages published to a topic to subscription endpoints, you must add the endpoints to the topic.

To Add a Subscription
---------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Locate the topic to which you want to add a subscription, click **More** under **Operation**, and select **Add Subscription**.

   The **Add Subscription** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001417026805.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the subscription protocol and endpoints. You can enter 10 endpoints at most, each on a separate line.

   -  Email

      Enter a valid email address, for example, **username@example.com**.

      Subscribers will receive a subscription confirmation email valid in 48 hours and must confirm the subscription to receive messages published to the topic.

   -  HTTP/HTTPS

      Enter a public network URL, for example, **http://example.com/notification/action**. HTTP/HTTPS subscribers must confirm their subscriptions. For details about HTTP/HTTPS messages, see section :ref:`A.6.1 Introduction <smn_ug_a9001>`.

   -  SMS

      Enter a valid mobile number preceded by a plus sign (+) and a country code, for example, +4900000000.

      Subscribers will receive a subscription confirmation message valid in 48 hours and must confirm the subscription to receive messages published to the topic.

   -  DMS

      Subscription endpoints are message queues. This type of subscriptions does not need confirmation. Click |image2| to select subscription endpoints. Ensure that the queue policy grants the **DMS:ProduceMessages** permission to SMN. For details, see "Managing Queue Policies" in the *Distributed Message Service User Guide*.

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see section :ref:`A.4 Control on Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  The token is valid only for 48 hours. Therefore, subscribers must confirm subscriptions within that time.

.. |image1| image:: /_static/images/en-us_image_0000001366545396.png
.. |image2| image:: /_static/images/en-us_image_0148410841.png
