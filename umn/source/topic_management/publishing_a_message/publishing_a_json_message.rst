:original_name: en-us_topic_0044170767.html

.. _en-us_topic_0044170767:

Publishing a JSON Message
=========================

Scenario
--------

In a JSON message, you can specify different message content for different protocols, including SMS, email, DMS, HTTP, and HTTPS.

Prerequisites
-------------

Subscribers in the topic must have confirmed the subscription, or they will not be able to receive any messages.

To Publish a JSON Message
-------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic to which you need to publish a message and click **Publish Message** under **Operation**.

#. Configure the required parameters according to :ref:`Table 1 <en-us_topic_0043961403__table616755201736>`. The topic name is provided by default and cannot be changed.

   Select **JSON** for **Message Format**. Then, manually type the JSON message in the **Message** box or click **Generate JSON Message** to generate it automatically. The total size of a JSON message cannot exceed 256 KB.

   -  If you choose to manually type the JSON message, see :ref:`A.1 JSON Message Format <smn_ug_a1000>` for detailed requirements.
   -  If you choose to automatically generate the JSON message, proceed with steps :ref:`7 <en-us_topic_0044170767__li59465700211512>` through :ref:`10 <en-us_topic_0044170767__li3542952114596>`.

#. .. _en-us_topic_0044170767__li59465700211512:

   Click **Generate JSON Message**.

#. Enter your message content, for example, "This is a default message.", in the **Message** box and select the desired message protocols.

   The size of a JSON message varies depending on the protocol combinations. As you type in the message content, the system will calculate the number of bytes you have entered, the size of the JSON message, and how many bytes are left. The total size of a JSON message includes braces, quotation marks, spaces, line breaks, and message content. For details about how to calculate the size of a JSON message, see :ref:`Calculation on the JSON Message Size <smn_ug_a1000__section11977745123756>` in :ref:`A.1 JSON Message Format <smn_ug_a1000>`.


   .. figure:: /_static/images/en-us_image_0000001366545412.png
      :alt: **Figure 1** Generate JSON Message

      **Figure 1** Generate JSON Message

#. Click **OK**. The system generates a JSON message.


   .. figure:: /_static/images/en-us_image_0000001417145493.png
      :alt: **Figure 2** JSON message

      **Figure 2** JSON message

#. .. _en-us_topic_0044170767__li3542952114596:

   Modify the message content for each protocol so that different messages are sent to endpoints of different protocols. The system generates JSON-formatted content that includes a default message and message for each protocol. When SMN fails to match any specific message protocol, it sends the default message. For detailed JSON message format, see :ref:`A.1 JSON Message Format <smn_ug_a1000>`.

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about messages for different protocols, see :ref:`A.3 Messages of Different Protocols <smn_ug_a3000>`.

.. |image1| image:: /_static/images/en-us_image_0000001366545396.png
