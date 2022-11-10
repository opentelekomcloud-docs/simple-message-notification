:original_name: en-us_topic_0043394891.html

.. _en-us_topic_0043394891:

Basic Mode
==========

The topic creator has the right to configure topic policies. Using topic policies, you can specify which users and cloud services can perform which topic operations, for example, querying topic details and publishing messages. Topic creators always have permissions over a topic even if they grant topic permissions to other users.

Configuring Topic Policies in Basic Mode
----------------------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Locate a topic, click **More** under **Operation**, and select **Configure Topic Policy**.

#. In the **Configure Topic Policy** box, configure the topic policy in basic mode.

   The basic mode simply specifies which users or cloud services have permissions to publish messages to a topic. For details, see :ref:`Table 1 <en-us_topic_0043394891__table41411027111244>`.

   The advanced mode provides more flexible permission settings. For details, see section :ref:`3.4.2 Advanced Mode <en-us_topic_0043394868>`.

   .. _en-us_topic_0043394891__table41411027111244:

   .. table:: **Table 1** Description for configuring topic policies in basic mode

      +--------------------------------------------------+-------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Item                                             | Parameter                                                         | Description                                                                                                                                                                                                                     |
      +==================================================+===================================================================+=================================================================================================================================================================================================================================+
      | Users who can publish messages to this topic     | Topic creator                                                     | Only the topic creator has permission to publish messages to the topic.                                                                                                                                                         |
      +--------------------------------------------------+-------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                                  | All users                                                         | All users have permission to publish messages to the topic.                                                                                                                                                                     |
      +--------------------------------------------------+-------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                                  | Specified user domains                                            | Only specified users have permission to publish messages to the topic. Users are specified in the format **urn:csp:iam::domainId:root**.                                                                                        |
      |                                                  |                                                                   |                                                                                                                                                                                                                                 |
      |                                                  |                                                                   | You only need to enter the domain ID and click **OK**. The system completes all other required information for you. SMN does not limit the number of IDs you enter, but the total length of a topic policy cannot exceed 30 KB. |
      |                                                  |                                                                   |                                                                                                                                                                                                                                 |
      |                                                  |                                                                   | All settings in the basic mode are also presented in the advanced policy. You can modify them in the advanced mode if necessary. For details, see section :ref:`3.4.2 Advanced Mode <en-us_topic_0043394868>`.                  |
      |                                                  |                                                                   |                                                                                                                                                                                                                                 |
      |                                                  |                                                                   | To obtain a user's domain ID, log in to the SMN console and click **My Credentials** in the username drop-down list on the upper right.                                                                                         |
      +--------------------------------------------------+-------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Services that can publish messages to this topic | The services that can publish messages vary according to regions. | The selected cloud services have operation permissions of the topic.                                                                                                                                                            |
      |                                                  |                                                                   |                                                                                                                                                                                                                                 |
      |                                                  |                                                                   | .. note::                                                                                                                                                                                                                       |
      |                                                  |                                                                   |                                                                                                                                                                                                                                 |
      |                                                  |                                                                   |    By default, Cloud Eye and Anti-DDoS have permissions to publish messages to topics created by all users.                                                                                                                     |
      |                                                  |                                                                   |                                                                                                                                                                                                                                 |
      |                                                  |                                                                   |    For details about how to use SMN in other cloud services, see user guides of the related services.                                                                                                                           |
      +--------------------------------------------------+-------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001366545396.png
