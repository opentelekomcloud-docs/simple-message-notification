:original_name: smn_ug_0004.html

.. _smn_ug_0004:

Publishing a Message
====================

After you learn the basic concepts in SMN, you can start to create a topic, add subscriptions to the topic, and publish messages on the SMN console or by calling RESTful APIs provided by SMN. For details about SMN APIs, see the *Simple Message Notification API Reference*.

:ref:`Figure 1 <smn_ug_0004__fig208091627152213>` shows the process to publish a message to a topic.

.. _smn_ug_0004__fig208091627152213:

.. figure:: /_static/images/en-us_image_0000001366065828.png
   :alt: **Figure 1** Process to publish a message

   **Figure 1** Process to publish a message

Scenario
--------

If you need to send similar messages repeatedly, you can create a message template which contains fixed and changeable content. Every time you send messages using the template, you only have to replace changeable content. For example, your organization holds expositions regularly and needs to notify relevant people of the dates, you can create a message template containing date variables and other fixed content.

Step 1. Create a Topic
----------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Click **Create Topic**.

   The **Create Topic** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001416865373.png
      :alt: **Figure 2** Create Topic

      **Figure 2** Create Topic

#. Enter a topic name and display name.

   .. table:: **Table 1** Information required for creating a topic

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================+
      | Topic Name                        | Topic name, which:                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                    |
      |                                   | -  Contains only letters, numerals, hyphens (-), and underscores (_) and starts with a letter or numeral.                                                                                          |
      |                                   | -  Is a string of 1 to 255 characters.                                                                                                                                                             |
      |                                   | -  Must be unique and cannot be modified once the topic is created.                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Display Name                      | Message sender name, which must be less than 192 bytes.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                    |
      |                                   |    After you specify a display name, the sender in email messages will be presented as *Display name*\ **<username@example.com>**. Otherwise, the sender will be **username@example.com**.         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | Tags consist of keys and values. They identify cloud resources so that you can easily categorize and search for your resources.                                                                    |
      |                                   |                                                                                                                                                                                                    |
      |                                   | -  A key or value is composed of letters, numerals, special characters -_@ and cannot start or end with a space. A key contains 36 characters at most, and a value contains 43 characters at most. |
      |                                   | -  You can add up to 10 tags for each topic.                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK.**

   The topic you created is displayed in the topic list. The system generates a topic URN, which is the unique resource identifier of the topic and cannot be changed.

#. Click the name of the topic to view its details, including the subscriptions, URN, and display name.

Step 2. Add a Subscription
--------------------------

#. Log in to the management console.

#. Click |image2| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Subscriptions**.

#. Click **Add Subscription**.

   The **Add Subscription** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001416865385.png
      :alt: **Figure 3** Add Subscription

      **Figure 3** Add Subscription

#. Specify the required subscription information.

   a. Click |image3| beside the **Topic Name** box to select a topic.
   b. Specify the subscription protocol and endpoints.

      .. table:: **Table 2** Required subscription information

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
         |                                   | -  **DMS**: Click |image4| to select a message queue. Ensure that the queue policy grants the **DMS:ProduceMessages** permission to SMN. For details, see section "Managing Queue Policies" in the *Distributed Message Service User Guide*. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period of time. For details, see section :ref:`A.4 Control on Subscription Confirmation Traffic <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions. However, subscribers will not receive notification messages until they confirm their subscriptions.
      -  The token is valid only for 48 hours. Therefore, subscribers must confirm subscriptions within that time.

Step 3. Create a Message Template
---------------------------------

#. Log in to the management console.

#. Click |image5| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Message Templates**.

#. Click **Create Message Template**.

   The **Create Message Template** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001416865433.png
      :alt: **Figure 4** Create Message Template

      **Figure 4** Create Message Template

#. Specify the template name, protocol, and content.

   .. table:: **Table 3** Parameters required for creating a message template

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================================================================+
      | Template Name                     | Template name, which:                                                                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  Contains letters, numerals, underscores (_), and hyphens (-) and starts with a letter or numeral.                                                                                                                                                                                                                                              |
      |                                   | -  Is a character string 1 to 64 bytes long.                                                                                                                                                                                                                                                                                                      |
      |                                   | -  Cannot be modified once the template is created.                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | Endpoint protocol of the template, which cannot be changed once the template is created                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | The value can be **Default**, **SMS**, **HTTP**, **HTTPS**, **DMS**, or **Email**.                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | If you do not specify a protocol, the **Default** protocol is used.                                                                                                                                                                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Content                           | Template content                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | You can use variables as placeholders. Before you send messages using the template, SMN replaces the variables with the message content you specify. A variable is a string of up to 21 characters. It may contain upper- or lower-case letters, numerals, hyphens (-), underscores (_), and periods (.) and must start with a letter or numeral. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | The message template must meet the following requirements:                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  The template supports plain text only.                                                                                                                                                                                                                                                                                                         |
      |                                   | -  The template content cannot be left blank and cannot exceed 256 KB.                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                   |
      |                                   | -  A template can contain up to 90 non-repeating variables or 256 variables counting the repeated ones.                                                                                                                                                                                                                                           |
      |                                   | -  When you send messages using a template, the message content you specify for each variable cannot exceed 1 KB.                                                                                                                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, the template information is as follows:

   -  **Template Name**: **tem_001**

   -  **Protocol**: **Default**

   -  **Content**: **The Arts and Crafts Exposition will be held from {startdate} through {enddate}. We sincerely invite you to join us.**


      .. figure:: /_static/images/en-us_image_0000001366385432.png
         :alt: **Figure 5** Create Message Template

         **Figure 5** Create Message Template

#. Click **OK**.

   The template you created is displayed in the template list.

Step 4. Publish a Template Message
----------------------------------

#. Log in to the management console.

#. Click |image6| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic to which you need to publish a message and click **Publish Message** under **Operation**.

#. Configure the required parameters. The topic name is provided by default and cannot be changed.

   Select **Template** for **Message Format**. Then, manually type the template content in the **Message** box or click **Generate Template Message** to generate it automatically. The template message content cannot exceed 256 KB.

   -  If you choose to manually type the template message, see :ref:`A.2 Template Message Format <smn_ug_a2000>` for detailed requirements.
   -  If you choose to automatically generate the template message, proceed with steps :ref:`7 <smn_ug_0004__en-us_topic_0044170770_li37303092212221>` through :ref:`10 <smn_ug_0004__en-us_topic_0044170770_li3929025721230>`.

#. .. _smn_ug_0004__en-us_topic_0044170770_li37303092212221:

   Click **Generate Template Message**.

#. Select a template name, for example, **tem_001**, and enter values for the variables.

   The system replaces the variables with the message content you specified. The protocols configured in the template are displayed after each variable. In the example shown in the following figure, only the default protocol is specified in tem_001. Therefore, all confirmed subscribers in the topic will receive the message content in the default template.


   .. figure:: /_static/images/en-us_image_0000001366545400.png
      :alt: **Figure 6** Generate Template Message

      **Figure 6** Generate Template Message

#. Click the **Preview** tab to preview the message.

   In this example, the message generated is "The Arts and Crafts Exposition will be held from February 10 through February 21. We sincerely invite you to join us."


   .. figure:: /_static/images/en-us_image_0000001366065760.png
      :alt: **Figure 7** Previewing the template message

      **Figure 7** Previewing the template message

#. .. _smn_ug_0004__en-us_topic_0044170770_li3929025721230:

   Click **OK**.

   The message that is generated contains the template name and variables.


   .. figure:: /_static/images/en-us_image_0000001366065752.png
      :alt: **Figure 8** Template message example

      **Figure 8** Template message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about messages for different protocols, see :ref:`A.3 Messages of Different Protocols <smn_ug_a3000>`.

Step 5. Receive the Message
---------------------------

Subscription endpoints of different protocols receive different messages.

-  Email protocol

   Subscription endpoints are email addresses.

   Email messages contain the message subject, content, and a link to unsubscribe.


   .. figure:: /_static/images/en-us_image_0000001417026857.png
      :alt: **Figure 9** Email message

      **Figure 9** Email message

-  HTTP/HTTPS protocol

   Subscription endpoints are public network URLs. For details, see section "HTTP/HTTPS Messages" in the *Simple Message Notification User Guide*.

-  SMS protocol

   Subscription endpoints are phone numbers.

   SMS messages contain only the message content.

-  DMS protocol

   Subscription endpoints are message queues.

   Message content is not displayed in message queues. You can access the DMS console and check the number of messages in a queue. After you publish a message to a message queue, the number in that queue will increase.

.. |image1| image:: /_static/images/en-us_image_0000001366545396.png
.. |image2| image:: /_static/images/en-us_image_0000001366065784.png
.. |image3| image:: /_static/images/en-us_image_0000001366065744.png
.. |image4| image:: /_static/images/en-us_image_0000001418973281.png
.. |image5| image:: /_static/images/en-us_image_0000001366225560.png
.. |image6| image:: /_static/images/en-us_image_0000001416865365.png
