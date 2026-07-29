:original_name: en-us_topic_0043961401.html

.. _en-us_topic_0043961401:

Creating a Topic
================

Scenarios
---------

A topic is a specified event to publish messages and subscribe to notifications. It serves as a message sending channel, where publishers and subscribers can interact with each other.

Procedure
---------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console appears.

#. In the navigation pane, choose **Topics**.

   The **Topics** page appears.

#. In the upper right corner, click **Create Topic**.


   .. figure:: /_static/images/en-us_image_0000002624942854.png
      :alt: **Figure 1** Create Topic

      **Figure 1** Create Topic

#. Enter a topic name and display name.

   .. _en-us_topic_0043961401__en-us_topic_0043394871_table9567729153632:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                          |
      +===================================+======================================================================================================================================================================================================+
      | Topic Name                        | Topic name, which:                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  Contains only letters, digits, hyphens (-), and underscores (_) and must start with a letter or digit.                                                                                            |
      |                                   | -  Contains 1 to 255 characters.                                                                                                                                                                     |
      |                                   | -  Must be unique and cannot be modified once the topic is created.                                                                                                                                  |
      |                                   | -  Must be specified.                                                                                                                                                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Display Name                      | Message sender name, which can contain a maximum of 192 characters                                                                                                                                   |
      |                                   |                                                                                                                                                                                                      |
      |                                   | This parameter is optional.                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                      |
      |                                   | .. note::                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   |    After you specify a display name, the sender in email messages will be presented as *Display name*\ **<noreply@otc.t-systems.com>**. Otherwise, the sender will be **noreply@otc.t-systems.com**. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Name of an enterprise project. An enterprise project facilitates project-level management and grouping of cloud resources and users.                                                                 |
      |                                   |                                                                                                                                                                                                      |
      |                                   | This parameter is mandatory for enterprise users.                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | A tag is a key-value pair. Tags identify cloud resources so that you can easily categorize and search for your resources.                                                                            |
      |                                   |                                                                                                                                                                                                      |
      |                                   | -  A key can contain up to 36 characters. A value can contain up to 43 characters. Both **Key** and **Value** can contain only digits, letters, hyphens (-), at signs (@), and underscores (_).      |
      |                                   | -  You can add up to 20 tags for each topic.                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK.**

   The topic you created is displayed in the topic list. The system generates a topic URN, which is the unique resource identifier of the topic and cannot be changed.

   To search for a topic, set the filter criteria in the search box above the topic list. You can search for topics by topic name, ID, URN, creation time, and display name.

   After the search is complete, click |image2| in the search box. The **Save as Quick Filter Set** dialog box is displayed. Enter a filter set name and click **OK** to save the current filter criteria as a quick filter set.

#. Click the name of the topic to view its details, including the topic URN, display name, tags, and subscriptions.

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0000002659158837.png
