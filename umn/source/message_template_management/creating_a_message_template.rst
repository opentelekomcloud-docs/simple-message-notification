:original_name: smn_ug_0086.html

.. _smn_ug_0086:

Creating a Message Template
===========================

Scenarios
---------

Message templates contain fixed and changeable content and can be used to create and send messages more quickly. When you use a template to publish a message, you can specify values for different variables in the template.

This section describes how to create a message template on the management console.

Procedure
---------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console appears.

#. In the navigation pane on the left, choose **Message Templates**.

#. On the **Message Templates** page, click **Create Message Template**.

   The **Create Message Template** dialog box appears.


   .. figure:: /_static/images/en-us_image_0000002624784058.png
      :alt: **Figure 1** Creating a message template

      **Figure 1** Creating a message template

#. Specify the template name, protocol, and content.

   .. table:: **Table 1** Parameters required for creating a message template

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================================================================================================+
      | Template Name                     | Template name, which:                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | -  Contains only letters, digits, hyphens (-), and underscores (_) and must start with a letter or digit.                                                                                                                                                                                             |
      |                                   | -  Can contain 1 to 64 characters.                                                                                                                                                                                                                                                                    |
      |                                   | -  Cannot be modified once it is created.                                                                                                                                                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | Endpoint protocol. It cannot be changed once the template is created.                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | The protocol can be **Default**, **SMS**, **HTTP**, **HTTPS**, **Email**, or **FunctionGraph (function)**.                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | The default protocol is **Default**. You can select other protocols for the same template as needed.                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | Each template must include the Default protocol.                                                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Content                           | Template content.                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | Use *{xxx}* as the placeholder to create a template. When you use this template to publish messages, replace {xxx} with specific content. *xxx* must start with a letter or digit and can contain up to 21 characters, including only letters, digits, hyphens (-), periods (.), and underscores (_). |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | The template content must meet the following requirements:                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | -  The template content supports plain text only.                                                                                                                                                                                                                                                     |
      |                                   | -  The template content cannot be empty.                                                                                                                                                                                                                                                              |
      |                                   | -  The size of the template content cannot exceed 256 KB.                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                       |
      |                                   | -  The template can contain up to 256 variables in total, but that includes redundant variables. For unique variables, there can be no more than 90.                                                                                                                                                  |
      |                                   | -  When you publish messages using a template, the value you specify for each variable cannot exceed 1 KB.                                                                                                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   For example, the template information is as follows:

   -  **Template Name**: **tem_001**
   -  **Protocol**: **Default**
   -  **Content**: **The Arts and Crafts Exposition will be held from {startdate} through {enddate}. We sincerely invite you to join us.**

#. Click **OK**.

   The template you created is displayed in the template list.

   To search for a template, set the filter criteria in the search box. You can search for templates by template name, ID, protocol, and last modification time.

   After the search is complete, click |image2| in the search box. The **Save as Quick Filter Set** dialog box is displayed. Enter a filter set name and click **OK** to save the current filter criteria as a quick filter set.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0000002628919572.png
