:original_name: smn_ug_0008.html

.. _smn_ug_0008:

Adding a Subscription
=====================

Scenario
--------

To deliver messages published to a topic to endpoints, you must add the subscription endpoints to the topic. Endpoints can be email addresses, phone numbers, message queues, and HTTP/HTTPS URLs. After you add endpoints to the topic and the subscribers confirm the subscription, they are able to receive messages published to the topic.

You can add multiple subscriptions to each topic. This section describes how to add subscriptions to a topic you created or one to which you have been granted permissions and how to delete subscriptions.

To Add a Subscription
---------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Subscriptions**.

#. Click **Add Subscription**.

   The **Add Subscription** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001416865385.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the required subscription information.

   a. Click |image2| beside the **Topic Name** box to select a topic.
   b. Specify the subscription protocol and endpoints.

      .. table:: **Table 1** Required subscription information

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                  |
         +===================================+==============================================================================================================================================================================================================================================+
         | Topic Name                        | Name of the topic to subscribe to                                                                                                                                                                                                            |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Protocol                          | Protocol the subscription endpoints support. The available options include **SMS**, **DMS**, **Email**, **HTTP**, and **HTTPS**.                                                                                                             |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Endpoint                          | Subscription endpoint. You can enter up to 10 SMS, email, HTTP, or HTTPS endpoints, one in each line.                                                                                                                                        |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   | -  **SMS**: Enter one or more valid phone numbers.                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    The phone number is preceded by a plus sign (+) and a country code.                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    For example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **+4900000000**                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **+4900000001**                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **+4900000002**                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **+4900000003**                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   | -  **Email**: Enter one or more valid email addresses.                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    For example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **username1@example.com**                                                                                                                                                                                                                 |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **username2@example.com**                                                                                                                                                                                                                 |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   | -  **HTTP** or **HTTPS**: Enter one or more public network URLs.                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    For example:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **http://example1.com/notification/action**                                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   |    **http://example2.com/notification/action**                                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                              |
         |                                   | -  **DMS**: Click |image3| to select a message queue. Ensure that the queue policy grants the **DMS:ProduceMessages** permission to SMN. For details, see section "Managing Queue Policies" in the *Distributed Message Service User Guide*. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see section :ref:`A.4 Control on Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  The token is valid only for 48 hours. Therefore, subscribers must confirm subscriptions within that time.

.. |image1| image:: /_static/images/en-us_image_0000001366065784.png
.. |image2| image:: /_static/images/en-us_image_0000001366065744.png
.. |image3| image:: /_static/images/en-us_image_0148410841.png
