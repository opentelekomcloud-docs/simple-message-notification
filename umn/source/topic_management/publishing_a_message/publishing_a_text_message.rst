:original_name: en-us_topic_0043961403.html

.. _en-us_topic_0043961403:

Publishing a Text Message
=========================

Scenarios
---------

After you publish a text message to a topic, SMN will deliver the message to all confirmed subscription endpoints in the topic.

Prerequisites
-------------

Subscribers in the topic must have confirmed the subscription, or they will not be able to receive any messages.

Procedure
---------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console appears.

#. In the navigation pane, choose **Topics**.

   The **Topics** page appears.

#. In the topic list, locate the topic that you need to publish a message to and click **Publish Message** in the **Operation** column.

   Alternatively, locate the topic and click its name. In the upper right corner of the displayed topic details page, click **Publish Message**.

#. Configure the required parameters based on :ref:`Table 1 <en-us_topic_0043961403__table616755201736>`.

   a. Configure basic information about message publishing.

      .. _en-us_topic_0043961403__table616755201736:

      .. table:: **Table 1** Parameters required for publishing a message

         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                             |
         +===================================+=========================================================================================================================+
         | Subject                           | The message subject, which can contain a maximum of 512 bytes. This parameter is optional.                              |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
         | Message Format                    | The message format, which can be **Text**, **JSON**, or **Template**. Only one format can be selected for each message. |
         |                                   |                                                                                                                         |
         |                                   | -  **Text**: common text message                                                                                        |
         |                                   | -  **JSON**: JSON message                                                                                               |
         |                                   | -  **Template**: template message. For details, see :ref:`Message Template Management <en-us_topic_0043394889>`.        |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
         | Message                           | The message content, which cannot be left blank and cannot exceed 256 KB.                                               |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+

   b. (Optional) Configure message attribute parameters. Message attributes specify the scope of message publishing.

      .. _en-us_topic_0043961403__table17341132634914:

      .. table:: **Table 2** Message attribute parameters

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                |
         +===================================+============================================================================================================================================================================================================+
         | Type                              | Select the type of the message to be published.                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                            |
         |                                   | -  Protocol                                                                                                                                                                                                |
         |                                   | -  string.array                                                                                                                                                                                            |
         |                                   | -  String                                                                                                                                                                                                  |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Name                              | Enter up to 32 characters, including only digits, lowercase letters, and underscores (_). Start with a number or lowercase letter. Do not end with an underscore (_) or enter consecutive underscores (_). |
         |                                   |                                                                                                                                                                                                            |
         |                                   | -  When you set **Type** to **Protocol**, **Name** will be **smn_protocol** by default.                                                                                                                    |
         |                                   | -  When you set **Type** to **string.array**, enter the name of the array that restricts the message to be published.                                                                                      |
         |                                   | -  When you set **Type** to **String**, enter the name of the character string that restricts the message to be published.                                                                                 |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Value                             | -  When you set **Type** to **Protocol**, select a protocol from the drop-down list. The available options are **SMS**, **Email**, **HTTP**, **HTTPS**, and **FunctionGraph (function)**.                  |
         |                                   |                                                                                                                                                                                                            |
         |                                   | -  When you set **Type** to **string.array**, the value must be a string array with a length of 1 to 10 elements.                                                                                          |
         |                                   |                                                                                                                                                                                                            |
         |                                   |    For example: [ "email", "sms" ]                                                                                                                                                                         |
         |                                   |                                                                                                                                                                                                            |
         |                                   | -  When you set **Type** to **String**, you cannot leave **Value** blank. Enter up to 32 characters, including only digits, letters, and underscores (_).                                                  |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   :ref:`Figure 1 <en-us_topic_0043961403__fig108334131919>` shows an example text message.

   .. _en-us_topic_0043961403__fig108334131919:

   .. figure:: /_static/images/en-us_image_0000002655155639.png
      :alt: **Figure 1** Text message example

      **Figure 1** Text message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about the messages received by each endpoint, see :ref:`Messages Using Different Protocols <smn_ug_a3000>`.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
