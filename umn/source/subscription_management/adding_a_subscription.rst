:original_name: smn_ug_0008.html

.. _smn_ug_0008:

Adding a Subscription
=====================

Scenarios
---------

To enable an endpoint to receive messages published to a topic, you must subscribe the endpoint to the topic. The endpoint can be a phone number, email address, function, or an HTTP/HTTPS URL. After you subscribe an endpoint to a topic and the subscription is confirmed, the endpoint can receive messages published to the topic.

You can add multiple subscriptions to a topic. This section describes how to add a subscription to a topic you created or a topic that you have permissions for.


Adding a Subscription
---------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane on the left, choose **Subscriptions**.

#. In the upper right corner, click **Add Subscription**.

   The **Add Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000002194988730.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the required subscription information.

   a. Beside **Topic Name**, click **Select Topic**.
   b. Specify the subscription protocol and endpoints.

      .. table:: **Table 1** Parameters for adding a subscription

         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                             |
         +===================================+=========================================================================================================================================================================================================================================================+
         | Topic Name                        | Specifies the name of the topic to which messages are published.                                                                                                                                                                                        |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Protocol                          | Specifies the protocol over which messages are sent. Possible values are **SMS**, **FunctionGraph (function)**, **Email**, **HTTP**, and **HTTPS**.                                                                                                     |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Endpoint                          | Specifies the subscription endpoint. You can add up to 10 SMS, email, HTTP, or HTTPS endpoints, one in each line.                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | -  **SMS**: Enter one or more valid phone numbers.                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    A phone number must be preceded by a plus sign (+) and a country code.                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    Examples:                                                                                                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **+4900000000**                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **+4900000001**                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **+4900000002**                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **+4900000003**                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | -  **Email**: Enter one or more valid email addresses.                                                                                                                                                                                                  |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    Examples:                                                                                                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **username@example.com**                                                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **username2@example.com**                                                                                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | -  **HTTP**: Enter one or more public network URLs.                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    Example:                                                                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **http://example.com/notification/action**                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | -  **HTTPS**: Enter one or more public network URLs.                                                                                                                                                                                                    |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    Example:                                                                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   |    **https://example.com/notification/action**                                                                                                                                                                                                          |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | -  **FunctionGraph (function)**: Click |image2| to select a function and specify its version.                                                                                                                                                           |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Request Header                    | This parameter is only available if **HTTP** or **HTTPS** is selected for **Protocol**. It indicates whether to configure the request header now. If you select **Configure now**, specify **Key** and **Value**. You can add up to 10 request headers. |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | The value of **Key** must:                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                                         |
         |                                   | -  Be case insensitive and unique.                                                                                                                                                                                                                      |
         |                                   | -  Start with **x-** but cannot start with **x-smn**.                                                                                                                                                                                                   |
         |                                   | -  Contain only digits, letters, and hyphens (-), but not end with a hyphen nor contain consecutive hyphens.                                                                                                                                            |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Version                           | This parameter is only available if **FunctionGraph (function)** is selected for **Protocol**. Select the version for the function.                                                                                                                     |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Enter the remarks for the subscription. The remarks can contain a maximum of 128 characters.                                                                                                                                                            |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   To search for a subscription, you can filter subscriptions by protocol or subscription status in the upper right corner of the subscription list. You can also enter a subscription endpoint and click |image3| or press **Enter**.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period. For details, see :ref:`Traffic Control over Subscription Confirmation <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions.
      -  After you add a subscription or request subscription confirmation, SMN will send a confirmation message to the endpoints, and the link in the confirmation message will be valid for 48 hours.
      -  Subscription confirmation messages will be counted as messages sent and will be billed.

.. |image1| image:: /_static/images/en-us_image_0259222477.png
.. |image2| image:: /_static/images/en-us_image_0000001495292001.png
.. |image3| image:: /_static/images/en-us_image_0000002009609645.png
