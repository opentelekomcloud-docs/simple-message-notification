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

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic that you need to publish a message to and click **Publish Message** in the **Operation** column.

   Alternatively, locate the topic and click its name. In the upper right corner of the displayed topic details page, click **Publish Message**.

#. Configure the required parameters based on :ref:`Table 1 <en-us_topic_0043961403__table155951825112619>`.

   The topic name is provided by default and cannot be changed.

   .. _en-us_topic_0043961403__table155951825112619:

   .. table:: **Table 1** Parameters required for publishing a message

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                               |
      +===================================+===========================================================================================================================+
      | Subject                           | (Optional) Specifies the message subject, which must be fewer than 512 bytes.                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Message Format                    | Specifies in which format a message is published. You can select only one message format each time you publish a message. |
      |                                   |                                                                                                                           |
      |                                   | -  **Text**: common text message                                                                                          |
      |                                   | -  **JSON**: JSON message                                                                                                 |
      |                                   | -  **Template**: template message. For details, see :ref:`Message Template Management <en-us_topic_0043394889>`.          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Message                           | Specifies the message content. The message content cannot be left blank and its size cannot exceed 256 KB.                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+

   :ref:`Figure 1 <en-us_topic_0043961403__fig4596122572617>` shows an example text message.

   .. _en-us_topic_0043961403__fig4596122572617:

   .. figure:: /_static/images/en-us_image_0000001889675317.png
      :alt: **Figure 1** Text message example

      **Figure 1** Text message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about the messages received by each endpoint, see :ref:`Messages Using Different Protocols <smn_ug_a3000>`.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
