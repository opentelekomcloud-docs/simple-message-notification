:original_name: smn_ug_0004.html

.. _smn_ug_0004:

Publishing a Message
====================

After you learn the basic concepts in SMN, you can start to create a topic, add subscriptions to the topic, and publish messages on the SMN console or by calling RESTful APIs provided by SMN.

:ref:`Figure 1 <smn_ug_0004__fig208091627152213>` shows the process to publish a message to a topic.

.. _smn_ug_0004__fig208091627152213:

.. figure:: /_static/images/en-us_image_0160895146.png
   :alt: **Figure 1** Process to publish a message

   **Figure 1** Process to publish a message

Scenarios
---------

To send similar messages repeatedly, create a message template which contains fixed and changeable content. Every time you send messages using the template, you only have to replace changeable content. For example, your organization holds expositions regularly and needs to notify relevant people of the dates, you can create a message template containing date variables and other fixed content.

Step 1. Create a Topic
----------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the upper right corner, click **Create Topic**.


   .. figure:: /_static/images/en-us_image_0152909747.png
      :alt: **Figure 2** Create Topic

      **Figure 2** Create Topic

#. Enter a topic name and display name.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================================+
      | Topic Name                        | Topic name, which:                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  Contains only letters, digits, hyphens (-), and underscores (_), and must start with a letter or digit.                                                                                      |
      |                                   | -  Contain 1 to 255 characters.                                                                                                                                                                 |
      |                                   | -  Must be unique and cannot be modified once the topic is created.                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Display Name                      | Message sender name, which must be fewer than 192 characters.                                                                                                                                   |
      |                                   |                                                                                                                                                                                                 |
      |                                   | .. note::                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                 |
      |                                   |    After you specify a display name, the sender in email messages will be presented as *Display name*\ **<username@example.com>**. Otherwise, the sender will be **username@example.com**.      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | A tag is a key-value pair. Tags identify cloud resources so that you can easily categorize and search for your resources.                                                                       |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  A key can contain up to 36 characters. A value can contain up to 43 characters. Both **Key** and **Value** can contain only digits, letters, hyphens (-), at signs (@), and underscores (_). |
      |                                   | -  You can add up to 10 tags for each topic.                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK.**

   The topic you created is displayed in the topic list. The system generates a topic URN, which is the unique resource identifier of the topic and cannot be changed.

#. Click the name of the topic to view its details, including the URN, display name, and subscriptions.

Step 2. Add a Subscription
--------------------------

#. Log in to the management console.

#. Click |image2| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Subscriptions**.

#. In the upper right corner, click **Add Subscription**.

   The **Add Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0152880872.png
      :alt: **Figure 3** Add Subscription

      **Figure 3** Add Subscription

#. Specify the required subscription information.

   a. Click |image3| beside the **Topic Name** box to select a topic.
   b. Specify the subscription protocol and endpoints.

      .. table:: **Table 2** Parameter descriptions

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
         |                                   | -  **DMS**: Click |image4| to select a message queue. Ensure that the queue policy grants the **ProduceMessages** permission to SMN. For details, see section "Managing Queue Policies" in the *Distributed Message Service User Guide*. |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see :ref:`Control over Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  After you add a subscription, SMN sends a confirmation message to the subscription endpoint. The message contains a link for confirming the subscription. The subscription confirmation link is valid within 48 hours. Confirm the subscription on your mobile phone, mailbox, or other endpoints in time.

Step 3. Create a Message Template
---------------------------------

#. Log in to the management console.

#. Click |image5| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Message Templates**.

#. In the upper right corner, click **Create Message Template**.

   The **Create Message Template** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0095667221.png
      :alt: **Figure 4** Create Message Template

      **Figure 4** Create Message Template

#. Specify the template name, protocol, and content.

   .. table:: **Table 3** Parameters required for creating a message template

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================================================================================================================+
      | Template Name                     | Template name, which:                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Contains only letters, digits, hyphens (-), and underscores (_), and must start with a letter or digit.                                                                                                                                                                                                            |
      |                                   | -  Can contain 1 to 64 bytes.                                                                                                                                                                                                                                                                                         |
      |                                   | -  Cannot be modified once the template is created.                                                                                                                                                                                                                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | Endpoint protocol of the template, which cannot be changed once the template is created                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | The protocol can be **Default**, **SMS**, **HTTP**, **HTTPS**, **DMS**, or **Email**.                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | If you do not specify a protocol, **Default** is used.                                                                                                                                                                                                                                                                |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Content                           | Template content                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | You can use variables as placeholders. Before you send messages using the template, SMN replaces the variables with the message content you specify. A variable can contain up to 21 characters and must start with a letter or digit. It can contain letters, digits, hyphens (-), underscores (_), and periods (.). |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | The message template must meet the following requirements:                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  The template supports plain text only.                                                                                                                                                                                                                                                                             |
      |                                   | -  The template content cannot be left blank and cannot exceed 256 KB.                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                       |
      |                                   | -  The template can contain up to 256 variables in total, but that includes redundant variables. For unique variables, there can be no more than 90.                                                                                                                                                                  |
      |                                   | -  When you send messages using a template, the message content you specify for each variable cannot exceed 1 KB.                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, the template information is as follows:

   -  **Template Name**: **tem_001**

   -  **Protocol**: **Default**

   -  **Content**: **The Arts and Crafts Exposition will be held from {startdate} through {enddate}. We sincerely invite you to join us.**


      .. figure:: /_static/images/en-us_image_0095665587.png
         :alt: **Figure 5** Create Message Template

         **Figure 5** Create Message Template

#. Click **OK**.

   The template you created is displayed in the template list.

Step 4. Publish a Template Message
----------------------------------

#. Log in to the management console.

#. Click |image6| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic that you need to publish a message to and click **Publish Message** under **Operation**.

#. Configure the required parameters.

   The topic name is provided by default and cannot be changed.

   Select **Template** for **Message Format**. Then, manually type the template content in the **Message** box or click **Generate Template Message** to generate it automatically. The template message content cannot exceed 256 KB.

   -  If you choose to manually type the template message, see :ref:`Template Message Format <smn_ug_a2000>` for detailed requirements.
   -  If you choose to automatically generate the template message, proceed with :ref:`7 <smn_ug_0004__en-us_topic_0044170770_li37303092212221>` through :ref:`10 <smn_ug_0004__en-us_topic_0044170770_li3929025721230>`.

#. .. _smn_ug_0004__en-us_topic_0044170770_li37303092212221:

   Click **Generate Template Message**.

#. Select a template name, for example, **tem_001**, and enter values for the variables.

   The system replaces the variables with the message content you specified. The protocols configured in the template are displayed after each variable. Only the **Default** protocol is specified in **tem_001**, as shown in :ref:`Figure 6 <smn_ug_0004__en-us_topic_0044170770_fig365979611560>`. Therefore, all confirmed subscribers in the topic will receive the message content in the default template.

   .. _smn_ug_0004__en-us_topic_0044170770_fig365979611560:

   .. figure:: /_static/images/en-us_image_0095665660.png
      :alt: **Figure 6** Generate Template Message

      **Figure 6** Generate Template Message

#. Click the **Preview** tab to preview the message.

   In this example, the message generated is "The Arts and Crafts Exposition will be held from February 10 through February 21. We sincerely invite you to join us."


   .. figure:: /_static/images/en-us_image_0095665678.png
      :alt: **Figure 7** Previewing the template message

      **Figure 7** Previewing the template message

#. .. _smn_ug_0004__en-us_topic_0044170770_li3929025721230:

   Click **OK**.

   The message that is generated contains the template name and variables.


   .. figure:: /_static/images/en-us_image_0095665722.png
      :alt: **Figure 8** Template message example

      **Figure 8** Template message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about messages for different protocols, see :ref:`Messages of Different Protocols <smn_ug_a3000>`.

Step 5. Receive the Message
---------------------------

Subscription endpoints of different protocols receive different messages.

-  Email

   Subscription endpoints are email addresses.

   Email messages contain the message subject, content, and a link to unsubscribe.


   .. figure:: /_static/images/en-us_image_0114842271.png
      :alt: **Figure 9** Email message

      **Figure 9** Email message

-  HTTP/HTTPS

   Subscription endpoints are public network URLs. For details, see section "HTTP/HTTPS Messages" in *Simple Message Notification User Guide*.

-  SMS

   Subscription endpoints are phone numbers.

   SMS messages contain only the message content.

-  DMS

   Subscription endpoints are message queues.

   Message content is not displayed in message queues. You can access the DMS console and check the number of messages in a queue. After you publish a message to the message queue, the number in that queue will increase.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0259222477.png
.. |image3| image:: /_static/images/en-us_image_0148410841.png
.. |image4| image:: /_static/images/en-us_image_0148410841.png
.. |image5| image:: /_static/images/en-us_image_0259222474.png
.. |image6| image:: /_static/images/en-us_image_0259222478.png
