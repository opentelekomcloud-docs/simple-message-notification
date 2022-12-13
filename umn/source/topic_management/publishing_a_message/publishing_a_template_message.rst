:original_name: en-us_topic_0044170770.html

.. _en-us_topic_0044170770:

Publishing a Template Message
=============================

Scenarios
---------

Message templates contain fixed message content. If you need to send the same or similar messages multiple times, you can create a message template for quick message sending.

You can create different templates for different protocols using the same template name so that each type of subscribers can receive customized messages. Templates contain variables as the placeholders to represent changeable content that you can replace with your own message content. Note that you must create a template whose Protocol is **Default**, or the system will not allow you to publish messages using this template name.

When you are creating messages using a template, select a template name. The system will list all variables in the following protocol sequence: default, SMS, email, DMS, HTTP, and HTTPS. The same variables are listed only once even if they are used in multiple protocols, and the protocols they support are listed after each variable. Specify content for each variable in the message template, and SMN replaces them with the content you entered. If you do not enter any content for a variable, the system will treat it as empty when sending messages.

SMN tries to match different types of subscribers to the template protocols. If there is no template for a specified protocol, SMN will use the default template to send messages to subscribers of that protocol.

This section describes how to publish messages using a template. For more details about message templates, see :ref:`Message Template Management <en-us_topic_0043394889>`.

Prerequisites
-------------

Subscribers in the topic must have confirmed the subscription, or they will not be able to receive any messages.

To Create a Message Template
----------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Message Templates**.

#. In the upper right corner, click **Create Message Template**. For details, see :ref:`To Create a Message Template <en-us_topic_0043394889__section66624127194914>` in :ref:`Message Template Management <en-us_topic_0043394889>`.

   For example, the template information is as follows:

   -  **Template Name**: **tem_001**

   -  **Protocol**: **Default**

   -  **Content**: **The Arts and Crafts Exposition will be held from {startdate} through {enddate}. We sincerely invite you to join us.**


      .. figure:: /_static/images/en-us_image_0095665587.png
         :alt: **Figure 1** Create Message Template

         **Figure 1** Create Message Template

To Publish a Template Message
-----------------------------

#. Log in to the management console.

#. Click |image2| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. In the topic list, locate the topic that you need to publish a message to and click **Publish Message** under **Operation**.

#. Configure the required parameters.

   The topic name is provided by default and cannot be changed.

   Select **Template** for **Message Format**. Then, manually type the template content in the **Message** box or click **Generate Template Message** to generate it automatically. The template message content cannot exceed 256 KB.

   -  If you choose to manually type the template message, see :ref:`Template Message Format <smn_ug_a2000>` for detailed requirements.
   -  If you choose to automatically generate the template message, proceed with :ref:`7 <en-us_topic_0044170770__li37303092212221>` through :ref:`10 <en-us_topic_0044170770__li3929025721230>`.

#. .. _en-us_topic_0044170770__li37303092212221:

   Click **Generate Template Message**.

#. Select a template name, for example, **tem_001**, and enter values for the variables.

   The system replaces the variables with the message content you specified. The protocols configured in the template are displayed after each variable. Only the **Default** protocol is specified in **tem_001**, as shown in :ref:`Figure 2 <en-us_topic_0044170770__fig365979611560>`. Therefore, all confirmed subscribers in the topic will receive the message content in the default template.

   .. _en-us_topic_0044170770__fig365979611560:

   .. figure:: /_static/images/en-us_image_0095665660.png
      :alt: **Figure 2** Generate Template Message

      **Figure 2** Generate Template Message

#. Click the **Preview** tab to preview the message.

   In this example, the message generated is "The Arts and Crafts Exposition will be held from February 10 through February 21. We sincerely invite you to join us."


   .. figure:: /_static/images/en-us_image_0095665678.png
      :alt: **Figure 3** Previewing the template message

      **Figure 3** Previewing the template message

#. .. _en-us_topic_0044170770__li3929025721230:

   Click **OK**.

   The message that is generated contains the template name and variables.


   .. figure:: /_static/images/en-us_image_0095665722.png
      :alt: **Figure 4** Template message example

      **Figure 4** Template message example

#. Click **OK**.

   SMN delivers your message to all subscription endpoints. For details about messages for different protocols, see :ref:`Messages of Different Protocols <smn_ug_a3000>`.

.. |image1| image:: /_static/images/en-us_image_0259222479.png
.. |image2| image:: /_static/images/en-us_image_0259222478.png
