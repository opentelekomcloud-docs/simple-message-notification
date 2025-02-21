:original_name: smn_qs_30010.html

.. _smn_qs_30010:

Getting Started
===============

After you learn the basic concepts in SMN, you can start to create a topic, add subscriptions to the topic, and publish messages on the SMN console or by calling RESTful APIs provided by SMN.

:ref:`Figure 1 <smn_qs_30010__en-us_topic_0111470019_fig208091627152213>` shows the process to publish a message to a topic.

.. _smn_qs_30010__en-us_topic_0111470019_fig208091627152213:

.. figure:: /_static/images/en-us_image_0000001976318720.png
   :alt: **Figure 1** Process of publishing a message

   **Figure 1** Process of publishing a message

Scenarios
---------

To send similar messages repeatedly, create a message template which contains fixed and changeable content. Every time you send messages using the template, you only have to replace changeable content. For example, your organization holds expositions regularly and needs to notify relevant people of the time, you can create a message template containing date variables and other fixed content.

Step 1. Create a Topic
----------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Simple Message Notification** under **Application**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the upper right corner, click **Create Topic**.


   .. figure:: /_static/images/en-us_image_0152909747.png
      :alt: **Figure 2** Create Topic

      **Figure 2** Create Topic

#. Enter a topic name and display name.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                          |
      +===================================+======================================================================================================================================================================================================+
      | Topic Name                        | Topic name, which:                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Contains only letters, digits, hyphens (-), and underscores (_) and must start with a letter or digit.                                                                                            |
      |                                   | -  Contains 1 to 255 characters.                                                                                                                                                                     |
      |                                   | -  Must be unique and cannot be modified once the topic is created.                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Display Name                      | Message sender name, which can contain up to 192 bytes                                                                                                                                               |
      |                                   |                                                                                                                                                                                                      |
      |                                   | .. note::                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    After you specify a display name, the sender in email messages will be presented as *Display name*\ **<noreply@otc.t-systems.com>**. Otherwise, the sender will be **noreply@otc.t-systems.com**. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | A tag is a key-value pair. Tags identify cloud resources so that you can easily categorize and search for your resources.                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  A key can contain up to 36 characters. A value can contain up to 43 characters. Both **Key** and **Value** can contain only digits, letters, hyphens (-), at signs (@), and underscores (_).      |
      |                                   | -  You can add up to 20 tags for each topic.                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK.**

   The topic you created is displayed in the topic list. The system generates a topic URN, which is the unique resource identifier of the topic and cannot be changed.

   To search for a topic, filter topics by project or enter the topic name in the upper right corner of the topic list. Then click |image2| or press **Enter**. Alternatively, click **Search by Tag** above the upper right corner of the topic list and search for a topic by tag key and value.

#. Click the name of the topic to view its details, including the topic URN, display name, tags, and subscriptions.

Step 2. Add a Subscription
--------------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image3| and select the desired region and project.

#. Select **Simple Message Notification** under **Application**.

   The SMN console is displayed.

#. In the navigation pane on the left, choose **Subscriptions**.

#. In the upper right corner, click **Add Subscription**.

   The **Add Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0152880872.png
      :alt: **Figure 3** Add Subscription

      **Figure 3** Add Subscription

#. Specify the required subscription information.

   a. Beside **Topic Name**, click **Select Topic**.
   b. Specify the subscription protocol and endpoints.

      .. table:: **Table 2** Parameters for adding a subscription

         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                         |
         +===================================+=====================================================================================================================================================+
         | Topic Name                        | Specifies the name of the topic to which messages are published.                                                                                    |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
         | Protocol                          | Specifies the protocol over which messages are sent. Possible values are **SMS**, **HTTP**, **HTTPS**, **FunctionGraph (function)**, and **Email**. |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
         | Endpoint                          | Specifies the subscription endpoint. You can add up to 10 SMS, email, HTTP, or HTTPS endpoints, one in each line.                                   |
         |                                   |                                                                                                                                                     |
         |                                   | -  **SMS**: Enter one or more valid phone numbers.                                                                                                  |
         |                                   |                                                                                                                                                     |
         |                                   |    A phone number must be preceded by a plus sign (+) and a country code.                                                                           |
         |                                   |                                                                                                                                                     |
         |                                   |    Examples:                                                                                                                                        |
         |                                   |                                                                                                                                                     |
         |                                   |    **+4900000000**                                                                                                                                  |
         |                                   |                                                                                                                                                     |
         |                                   |    **+4900000001**                                                                                                                                  |
         |                                   |                                                                                                                                                     |
         |                                   |    **+4900000002**                                                                                                                                  |
         |                                   |                                                                                                                                                     |
         |                                   |    **+4900000003**                                                                                                                                  |
         |                                   |                                                                                                                                                     |
         |                                   | -  **Email**: Enter one or more valid email addresses.                                                                                              |
         |                                   |                                                                                                                                                     |
         |                                   |    Examples:                                                                                                                                        |
         |                                   |                                                                                                                                                     |
         |                                   |    **username@example.com**                                                                                                                         |
         |                                   |                                                                                                                                                     |
         |                                   |    **username2@example.com**                                                                                                                        |
         |                                   |                                                                                                                                                     |
         |                                   | -  **HTTP**: Enter one or more public network URLs.                                                                                                 |
         |                                   |                                                                                                                                                     |
         |                                   |    Example:                                                                                                                                         |
         |                                   |                                                                                                                                                     |
         |                                   |    **http://example.com/notification/action**                                                                                                       |
         |                                   |                                                                                                                                                     |
         |                                   | -  **HTTPS**: Enter one or more public network URLs.                                                                                                |
         |                                   |                                                                                                                                                     |
         |                                   |    Example:                                                                                                                                         |
         |                                   |                                                                                                                                                     |
         |                                   |    **https://example.com/notification/action**                                                                                                      |
         |                                   |                                                                                                                                                     |
         |                                   | -  **FunctionGraph (function)**: Click |image4| to select a function and specify its version.                                                       |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
         | Version                           | This parameter is only available if **FunctionGraph (function)** is selected for **Protocol**. Select the version for the function.                 |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Specifies the remarks of the subscription.                                                                                                          |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   The subscription you added is displayed in the subscription list.

   To search for a subscription, you can filter subscriptions by protocol or subscription status in the upper right corner of the subscription list. You can also enter a subscription endpoint and click |image5| or press **Enter**.

   .. note::

      -  To prevent malicious users from attacking subscription endpoints, SMN limits the number of confirmation messages that can be sent to an endpoint within a specified period. For details, see :ref:`Traffic Control over Subscription Confirmation <smn_ug_a4000>`.
      -  SMN does not check whether subscription endpoints exist when you add subscriptions.
      -  After you add a subscription or request subscription confirmation, SMN will send a confirmation message to the endpoints, and the link in the confirmation message will be valid for 48 hours.
      -  Subscription confirmation messages will be counted as messages sent and will be billed.

Step 3. Create a Message Template
---------------------------------

#. Log in to the management console.

#. Click |image6| on the upper left to select the desired region and project.

#. Select **Simple Message Notification** under **Application**.

   The SMN console is displayed.

#. In the navigation pane on the left, choose **Message Templates**.

#. In the upper right corner, click **Create Message Template**.

   The **Create Message Template** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0095667221.png
      :alt: **Figure 4** Create Message Template

      **Figure 4** Create Message Template

#. Specify the template name, protocol, and content.

   .. table:: **Table 3** Parameters required for creating a message template

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================+
      | Template Name                     | Template name, which:                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | -  Contains only letters, digits, hyphens (-), and underscores (_) and must start with a letter or digit.                                                                                                                                                                                               |
      |                                   | -  Can contain 1 to 64 characters.                                                                                                                                                                                                                                                                      |
      |                                   | -  Cannot be modified once the template is created.                                                                                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | Endpoint protocol of the template, which cannot be changed once the template is created                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | The protocol can be **Default**, **SMS**, **HTTP**, **HTTPS**, **Email**, or **FunctionGraph (function)**.                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | If you do not specify a protocol, **Default** is used.                                                                                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Content                           | Template content                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | Use *{xxx}* as the placeholder to create a template. When you use this template to publish messages, replace *{xxx}* with specific content. *xxx* must start with a letter or digit and can contain up to 21 characters, including only letters, digits, hyphens (-), periods (.), and underscores (_). |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | The message template must meet the following requirements:                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | -  The template supports plain text only.                                                                                                                                                                                                                                                               |
      |                                   | -  The template content cannot be left blank and its size cannot exceed 256 KB.                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                         |
      |                                   | -  The template can contain up to 256 variables in total, but that includes redundant variables. For unique variables, there can be no more than 90.                                                                                                                                                    |
      |                                   | -  When you publish messages using a template, the message content you specify for each variable cannot exceed 1 KB.                                                                                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, the template information is as follows:

   -  **Template Name**: **tem_001**
   -  **Protocol**: **Default**
   -  **Content**: **The Arts and Crafts Exposition will be held from {startdate} through {enddate}. We sincerely invite you to join us.**

#. Click **OK**.

   The template you created is displayed in the template list.

   To search for a template, enter the template name in the upper right corner of the message template list and click |image7| or press **Enter**.

Step 4. Publish a Template Message
----------------------------------

#. Log in to the management console.

#. Click |image8| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic that you need to publish a message to and click **Publish Message** in the **Operation** column.

   Alternatively, locate the topic and click its name. In the upper right corner of the displayed topic details page, click **Publish Message**.

#. Configure the required parameters. (The topic name is provided by default and cannot be changed. **Subject** is optional.)

   Select **Template** for **Message Format**. Then, manually type the template content in the **Message** box or click **Generate Template Message** to generate it automatically. The message content cannot be left blank and its size cannot exceed 256 KB.

   -  If you choose to manually type the template message, see :ref:`Template Message Format <smn_ug_a2000>` for detailed requirements.
   -  If you choose to automatically generate the template message, proceed with :ref:`7 <smn_qs_30010__en-us_topic_0111470019_en-us_topic_0044170770_li37303092212221>` through :ref:`10 <smn_qs_30010__en-us_topic_0111470019_en-us_topic_0044170770_li3929025721230>`.

#. .. _smn_qs_30010__en-us_topic_0111470019_en-us_topic_0044170770_li37303092212221:

   Click **Generate Template Message**.

#. Select a template name, for example, **tem_001**. Enter values for the variables.

   The system replaces the variables with the message content you specified. The protocols configured in the template are displayed after each variable. Only the **Default** protocol is specified in **tem_001**, as shown in :ref:`Figure 5 <smn_qs_30010__en-us_topic_0111470019_en-us_topic_0044170770_fig365979611560>`. Therefore, all confirmed subscribers in the topic will receive the message content in the default template.

   .. _smn_qs_30010__en-us_topic_0111470019_en-us_topic_0044170770_fig365979611560:

   .. figure:: /_static/images/en-us_image_0095665660.png
      :alt: **Figure 5** Generate Template Message

      **Figure 5** Generate Template Message

#. Click the **Preview** tab and click **Message Preview** to preview the message.

   In this example, the message generated is **The Arts and Crafts Exposition will be held from February 10 through February 21. We sincerely invite you to join us.**.


   .. figure:: /_static/images/en-us_image_0095665678.png
      :alt: **Figure 6** Previewing the template message

      **Figure 6** Previewing the template message

#. .. _smn_qs_30010__en-us_topic_0111470019_en-us_topic_0044170770_li3929025721230:

   Click **OK**.

   The message that is generated contains the template name and variables.


   .. figure:: /_static/images/en-us_image_0095665722.png
      :alt: **Figure 7** Template message example

      **Figure 7** Template message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about messages for different protocols, see :ref:`Messages Using Different Protocols <smn_ug_a3000>`.

Step 5. Receive the Message
---------------------------

Subscription endpoints of different protocols receive different messages.

-  Email

   Subscription endpoints are email addresses.

   Email messages contain the message subject, content, and a link to unsubscribe.


   .. figure:: /_static/images/en-us_image_0114842271.png
      :alt: **Figure 8** Email message

      **Figure 8** Email message

-  HTTP/HTTPS

   Subscription endpoints are public network URLs. For details, see :ref:`HTTP/HTTPS Messages <smn_ug_0031>`.

-  SMS

   Subscription endpoints are phone numbers.

   SMS messages contain only the message content.

-  FunctionGraph (function)

   Subscription endpoints are functions. To view messages received, see `Using an SMN Trigger <https://docs.otc.t-systems.com/function-graph/umn/creating_triggers/using_an_smn_trigger.html>`__ in *FunctionGraph User Guide*.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0000001973089658.png
.. |image3| image:: /_static/images/en-us_image_0259222477.png
.. |image4| image:: /_static/images/en-us_image_0000001495292001.png
.. |image5| image:: /_static/images/en-us_image_0000002009609645.png
.. |image6| image:: /_static/images/en-us_image_0259222474.png
.. |image7| image:: /_static/images/en-us_image_0000002009490141.png
.. |image8| image:: /_static/images/en-us_image_0259222478.png
