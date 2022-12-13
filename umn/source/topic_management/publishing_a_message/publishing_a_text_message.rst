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

To Publish a Text Message
-------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic that you need to publish a message to and click **Publish Message** under **Operation**.

#. Configure the required parameters based on :ref:`Table 1 <en-us_topic_0043961403__table616755201736>`.

   The topic name is provided by default and cannot be changed.

   .. _en-us_topic_0043961403__table616755201736:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                     |
      +===================================+=================================================================================================================+
      | Subject                           | (Optional) The message subject must be less than 512 bytes.                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
      | Message Format                    | The message format can be **Text**, **JSON**, or **Template**. In this context, select **Text**.                |
      |                                   |                                                                                                                 |
      |                                   | -  **Text**: common text message                                                                                |
      |                                   | -  **JSON**: JSON message                                                                                       |
      |                                   | -  **Template**: template message. For details, see :ref:`Message Template Management <en-us_topic_0043394889>` |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+
      | Message                           | This is the message content, which cannot be left blank nor exceed 256 KB.                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------+

   :ref:`Figure 1 <en-us_topic_0043961403__fig804716611238>` shows an example text message.

   .. _en-us_topic_0043961403__fig804716611238:

   .. figure:: /_static/images/en-us_image_0095665442.png
      :alt: **Figure 1** Text message example

      **Figure 1** Text message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about the messages received by each endpoint, see :ref:`Messages of Different Protocols <smn_ug_a3000>`.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
