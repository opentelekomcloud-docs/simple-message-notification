:original_name: smn_ug_0008.html

.. _smn_ug_0008:

Adding a Subscription
=====================

Scenarios
---------

To deliver messages published to a topic to endpoints, you must add the subscription endpoints to the topic. Endpoints can be email addresses, phone numbers, message queues, and HTTP/HTTPS URLs. After you add endpoints to the topic and the subscribers confirm the subscription, they are able to receive messages published to the topic.

You can add multiple subscriptions to each topic. This section describes how to add subscriptions to a topic you created or a topic that you have been granted permissions to and how to delete subscriptions.

To Add a Subscription
---------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Subscriptions**.

#. In the upper right corner, click **Add Subscription**.

   The **Add Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0152880872.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the required subscription information.

   a. Click |image2| beside the **Topic Name** box to select a topic.
   b. Specify the subscription protocol and endpoints.

      .. table:: **Table 1** Parameter descriptions

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                              |
         +===================================+==========================================================================================================================================================================================================================================+
         | Topic Name                        | Name of the topic to be subscribed to                                                                                                                                                                                                    |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Protocol                          | Protocol that the subscription endpoints support. The available protocols are **SMS**, **Email**, **HTTP**, and **HTTPS**.                                                                                                               |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Endpoint                          | Subscription endpoint. You can enter up to 10 SMS, email, HTTP, or HTTPS endpoints, one in each line.                                                                                                                                    |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   | -  **SMS**: Enter one or more valid phone numbers.                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    The phone number is preceded by a plus sign (+) and a country code.                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    Example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **+4900000000**                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **+4900000001**                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **+4900000002**                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **+4900000003**                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   | -  **Email**: Enter one or more valid email addresses.                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    Example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **username@example.com**                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **username2@example.com**                                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   | -  **HTTP**: Enter one or more public network URLs.                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    Example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **http://example.com/notification/action**                                                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   | -  **HTTPS**: Enter one or more public network URLs.                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    Example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   |    **https://example.com/notification/action**                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                          |
         |                                   | -  **DMS**: Click |image3| to select a message queue. Ensure that the queue policy grants the **ProduceMessages** permission to SMN. For details, see section "Managing Queue Policies" in the *Distributed Message Service User Guide*. |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see :ref:`Control over Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  After you add a subscription, SMN sends a confirmation message to the subscription endpoint. The message contains a link for confirming the subscription. The subscription confirmation link is valid within 48 hours. Confirm the subscription on your mobile phone, mailbox, or other endpoints in time.

.. |image1| image:: /_static/images/en-us_image_0259222477.png
.. |image2| image:: /_static/images/en-us_image_0148410841.png
.. |image3| image:: /_static/images/en-us_image_0148410841.png
