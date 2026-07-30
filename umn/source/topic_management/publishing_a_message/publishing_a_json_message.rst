:original_name: en-us_topic_0044170767.html

.. _en-us_topic_0044170767:

Publishing a JSON Message
=========================

Scenarios
---------

In a JSON message, you can specify different message content for different protocols, including SMS, email, FunctionGraph (function), HTTP, and HTTPS.

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

#. Configure parameters by referring to :ref:`Table 1 <en-us_topic_0044170767__table616755201736>`.

   .. _en-us_topic_0044170767__table616755201736:

   .. table:: **Table 1** Parameters required for publishing a message

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                    |
      +===================================+================================================================================================================================================+
      | Subject                           | The message subject, which can contain a maximum of 512 bytes. This parameter is optional.                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Message Format                    | The message format, which can be **Text**, **JSON**, or **Template**. Only one message format can be selected each time you publish a message. |
      |                                   |                                                                                                                                                |
      |                                   | -  **Text**: common text message                                                                                                               |
      |                                   | -  **JSON**: JSON message                                                                                                                      |
      |                                   | -  **Template**: template message. For details, see :ref:`Message Template Management <en-us_topic_0043394889>`.                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Message                           | The message content, which cannot be left blank and cannot exceed 256 KB.                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

   Select **JSON** for **Message Format**. Then, manually type the JSON message in the **Message** box or click **Generate JSON Message** to generate it automatically.

   -  If you choose to manually type the JSON message, see :ref:`JSON Message Format <smn_ug_a1000>`.
   -  If you choose to automatically generate the JSON message, proceed with steps :ref:`7 <en-us_topic_0044170767__li59465700211512>` through :ref:`10 <en-us_topic_0044170767__li3542952114596>`.

#. .. _en-us_topic_0044170767__li59465700211512:

   Click **Generate JSON Message**.

#. Enter your message content, for example, **This is a default message.**, in the **Message** box and select the desired message protocols.

   The size of a JSON message varies depending on the protocol combinations. As you type in the message content, the system will calculate the number of bytes you have entered, the size of the JSON message, and how many bytes are left. The total size of a JSON message includes braces, quotation marks, spaces, line breaks, and message content. For details, see :ref:`Figure 1 <en-us_topic_0044170767__fig1130720419115>`.For details about how to calculate the size of a JSON message, see :ref:`Calculation on the Size of a JSON Message <smn_ug_a1000__section11977745123756>` in :ref:`JSON Message Format <smn_ug_a1000>`.

   .. _en-us_topic_0044170767__fig1130720419115:

   .. figure:: /_static/images/en-us_image_0000002624796744.png
      :alt: **Figure 1** Generate JSON Message

      **Figure 1** Generate JSON Message

#. Click **OK**.


   .. figure:: /_static/images/en-us_image_0000002624797784.png
      :alt: **Figure 2** JSON message

      **Figure 2** JSON message

#. .. _en-us_topic_0044170767__li3542952114596:

   Modify the message content for each protocol so that different messages are sent to endpoints of different protocols. The system generates JSON-formatted content that includes a default message and content for each protocol. When SMN fails to match any specific message protocol, it sends the default message. For details, see :ref:`JSON Message Format <smn_ug_a1000>`.

#. (Optional) Configure message attribute parameters. Message attributes specify the scope of message publishing.

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

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about the messages received by each endpoint, see :ref:`Messages Using Different Protocols <smn_ug_a3000>`.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
