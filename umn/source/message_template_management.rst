:original_name: en-us_topic_0043394889.html

.. _en-us_topic_0043394889:

Message Template Management
===========================

Scenario
--------

Message templates contain fixed and changeable content and can be used to send messages quickly. When you publish a message using a template, you can specify values for variables in the template.

Message templates are grouped by template name. You can create templates for different protocols using the same template name. You must specify the default protocol in any template name, or the system will not allow you to publish messages using that template name. When sending messages using a template, SMN tries to match different types of subscribers to the template protocols. If there is no template for a specified protocol, SMN will use the default template to send messages to subscribers of that protocol.

This section describes how to publish messages using a template.

.. _en-us_topic_0043394889__section66624127194914:

To Create a Message Template
----------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Message Templates**.

#. Click **Create Message Template**.

   The **Create Message Template** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001416865433.png
      :alt: **Figure 1** Create Message Template

      **Figure 1** Create Message Template

#. Specify the template name, protocol, and content.

   .. table:: **Table 1** Parameters required for creating a message template

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
         :alt: **Figure 2** Create Message Template

         **Figure 2** Create Message Template

#. Click **OK**.

   The template you created is displayed in the template list.

To Modify a Template
--------------------

#. Locate the template to be modified in the template list.
#. Click **Modify** under **Operation** to change its content.

To Delete a Template
--------------------

#. Locate the template to be deleted in the template list.
#. Click **Delete** under **Operation**.

.. |image1| image:: /_static/images/en-us_image_0000001366225560.png
