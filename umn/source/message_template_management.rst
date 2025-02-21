:original_name: en-us_topic_0043394889.html

.. _en-us_topic_0043394889:

Message Template Management
===========================

Scenarios
---------

Message templates contain fixed and changeable content and can be used to create messages more quickly. When you use a template to publish a message, you need to specify values for different variables in the template.

Message templates are identified by name, but you can create different templates with the same name as long as they are configured for different protocols. All template messages must include a **Default** template or they cannot be sent out. The **Default** template is used anytime a template has not been configured for a given protocol, but as long as there is a template for the protocol, then any subscriber who selected that protocol when they subscribed will receive a message using the corresponding template.

This section describes how to publish messages using a template.

.. _en-us_topic_0043394889__section66624127194914:

Creating a Message Template
---------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Select **Simple Message Notification** under **Application**.

   The SMN console is displayed.

#. In the navigation pane on the left, choose **Message Templates**.

#. In the upper right corner, click **Create Message Template**.

   The **Create Message Template** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0095667221.png
      :alt: **Figure 1** Create Message Template

      **Figure 1** Create Message Template

#. Specify the template name, protocol, and content.

   .. table:: **Table 1** Parameters required for creating a message template

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

   To search for a template, enter the template name in the upper right corner of the message template list and click |image2| or press **Enter**.

Modifying a Template
--------------------

#. On the **Message Templates** page, locate the template to be modified in the template list.
#. Click **Modify** in the **Operation** column to change its content.

Deleting a Template
-------------------

#. On the **Message Templates** page, locate the template to be deleted in the template list.
#. Click **Delete** in the **Operation** column.

.. |image1| image:: /_static/images/en-us_image_0259222474.png
.. |image2| image:: /_static/images/en-us_image_0000002009490141.png
