:original_name: en-us_topic_0043961401.html

.. _en-us_topic_0043961401:

Creating a Topic
================

Scenario
--------

A topic is a specified event to publish messages and subscribe to notifications. It serves as a message sending channel, where publishers and subscribers can interact with each other.

To Create a Topic
-----------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Click **Create Topic**.

   The **Create Topic** box is displayed.


   .. figure:: /_static/images/en-us_image_0000001416865373.png
      :alt: **Figure 1** Create Topic

      **Figure 1** Create Topic

#. Enter a topic name and display name.

   .. _en-us_topic_0043961401__en-us_topic_0043394871_table9567729153632:

   .. table:: **Table 1** Information required for creating a topic

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================+
      | Topic Name                        | Topic name, which:                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                    |
      |                                   | -  Contains only letters, numerals, hyphens (-), and underscores (_) and starts with a letter or numeral.                                                                                          |
      |                                   | -  Is a string of 1 to 255 characters.                                                                                                                                                             |
      |                                   | -  Must be unique and cannot be modified once the topic is created.                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Display Name                      | Message sender name, which must be less than 192 bytes.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                    |
      |                                   |    After you specify a display name, the sender in email messages will be presented as *Display name*\ **<username@example.com>**. Otherwise, the sender will be **username@example.com**.         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | Tags consist of keys and values. They identify cloud resources so that you can easily categorize and search for your resources.                                                                    |
      |                                   |                                                                                                                                                                                                    |
      |                                   | -  A key or value is composed of letters, numerals, special characters -_@ and cannot start or end with a space. A key contains 36 characters at most, and a value contains 43 characters at most. |
      |                                   | -  You can add up to 10 tags for each topic.                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK.**

   The topic you created is displayed in the topic list. The system generates a topic URN, which is the unique resource identifier of the topic and cannot be changed.

#. Click the name of the topic to view its details, including the subscriptions, URN, and display name.

.. |image1| image:: /_static/images/en-us_image_0000001366545396.png
