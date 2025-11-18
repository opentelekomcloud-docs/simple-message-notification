:original_name: en-us_topic_0043961402.html

.. _en-us_topic_0043961402:

Adding a Subscription to a Topic
================================

Scenarios
---------

To deliver messages published to a topic to endpoints, you must add the subscription endpoints to the topic.

Adding a Subscription
---------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Locate the topic that you want to add a subscription to. In the **Operation** column, click **Add Subscription**.

   Alternatively, click a topic name. In the upper right corner of the displayed page, click **Add Subscription**.

   The **Add Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000002195142398.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the subscription protocol and endpoints.

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

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period. For details, see :ref:`Traffic Control over Subscription Confirmation <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions.
      -  After you add a subscription or request subscription confirmation, SMN will send a confirmation message to the endpoints, and the link in the confirmation message will be valid for 48 hours.
      -  Subscription confirmation messages will be counted as messages sent and will be billed.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0000001495292001.png
