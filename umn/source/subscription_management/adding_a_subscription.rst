:original_name: smn_ug_0008.html

.. _smn_ug_0008:

Adding a Subscription
=====================

Scenarios
---------

A subscription is how you add endpoints to a topic. To deliver messages published to a topic to endpoints, you must add the subscription endpoints to the topic. The endpoint can be a phone number, email address, function, or an HTTP/HTTPS URL. After you add endpoints to the topic and the subscribers confirm the subscription, they are able to receive messages published to the topic.

You can add multiple subscriptions to each topic.

This section describes how to add a subscription to a topic you created or a topic that you have permissions for.

Procedure
---------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console appears.

#. In the navigation pane on the left, choose **Subscriptions**.

#. In the upper right corner, click **Add Subscription**.

   The **Add Subscription** dialog box appears.


   .. figure:: /_static/images/en-us_image_0000002655065061.png
      :alt: **Figure 1** Add Subscription

      **Figure 1** Add Subscription

#. Specify the required subscription information.

   a. On the right of **Topic Name**, click **Select Topic**.

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
         |                                   |    The phone number must be in the following format: [+][*Country code*][*Mobile number*]                                                                                                                                                               |
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
         |                                   | -  **FunctionGraph (function)**: Click **Add Endpoint** to select a function and specify its version.                                                                                                                                                   |
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

   c. (Optional) Configure a subscription filter policy to specify the scope of message publishing.

      A subscription filter policy applies to message attributes. If you have set a filter policy and message attributes when publishing a message, the system determines whether to push the message to subscribers based on the filter policy you set. For details about the configuration example, see :ref:`Using a Subscription Filter Policy <smn_ug_a9005>`.

      Subscription filter policies are configured in JSON. The following is an example.

      .. code-block::

         {
             "filter_polices": [
                 {
                     "name": "policy_name",
                     "string_equals": [
                         "policy_value"
                     ]
                 }
             ]
         }

      For details about how to configure subscription filter policies, see `Creating Message Filter Policies for a Subscriber <https://docs.otc.t-systems.com/en-us/api/smn/smn_api_91000.html>`__ in the *Simple Message Notification API Reference*.

      For details about how to configure message attributes, see :ref:`Table 2 <en-us_topic_0043961403__table17341132634914>`.

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   To search for a subscription, set the filter criteria in the search box above the subscription list. You can search for subscriptions by protocol, endpoint, status, and description.

   After the search is complete, click |image2| in the search box. The **Save as Quick Filter Set** dialog box is displayed. Enter a filter set name and click **OK** to save the current filter criteria as a quick filter set.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period. For details, see :ref:`Traffic Control over Subscription Confirmation <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions.
      -  After you add a subscription or request subscription confirmation, SMN will send a confirmation message to the endpoints, and the link in the confirmation message will be valid for 48 hours.
      -  Subscription confirmation messages will be counted as messages sent and will be billed.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0000002659278785.png
