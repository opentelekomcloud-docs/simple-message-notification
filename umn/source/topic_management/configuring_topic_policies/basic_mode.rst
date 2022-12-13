:original_name: en-us_topic_0043394891.html

.. _en-us_topic_0043394891:

Basic Mode
==========

The topic creator has the right to configure topic policies. Using topic policies, you can specify which users and cloud services can perform which topic operations, for example, querying topic details and publishing messages. Topic creators always have permissions over a topic even if they grant topic permissions to other users.

Configuring Topic Policies in Basic Mode
----------------------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the navigation pane, choose **Topics**.

   The **Topics** page is displayed.

#. Locate a topic, click **More** under **Operation**, and select **Configure Topic Policy**.

#. In the **Configure Topic Policy** dialog box, configure the topic policy in basic mode.

   The basic mode simply specifies which users or cloud services have permissions to publish messages to a topic. For details, see :ref:`Table 1 <en-us_topic_0043394891__table41411027111244>`.

   .. _en-us_topic_0043394891__table41411027111244:

   .. table:: **Table 1** Description for configuring topic policies in basic mode

      +--------------------------------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Item                                             | Parameter                                                                    | Description                                                                                                                                                                                                                   |
      +==================================================+==============================================================================+===============================================================================================================================================================================================================================+
      | Users who can publish messages to this topic     | Topic creator                                                                | Only the topic creator has the permission to publish messages to the topic.                                                                                                                                                   |
      +--------------------------------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                                  | All users                                                                    | All users have the permission to publish messages to the topic.                                                                                                                                                               |
      +--------------------------------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                                  | Specified user domains                                                       | Only specified users have the permission to publish messages to the topic. Users are specified in the following format: urn:csp:iam::domainId:root.                                                                           |
      |                                                  |                                                                              |                                                                                                                                                                                                                               |
      |                                                  |                                                                              | You only need to enter the domain ID and click **OK**. The system completes all other required information for you. SMN does not limit the number of IDs you enter, but the total size of a topic policy cannot exceed 30 KB. |
      |                                                  |                                                                              |                                                                                                                                                                                                                               |
      |                                                  |                                                                              | To obtain your domain ID, log in to the SMN console. In the upper right corner, hover the mouse over your login account, and select **My Credentials** from the drop-down list.                                               |
      +--------------------------------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Services that can publish messages to this topic | Example: **OBS**                                                             | The selected cloud services have operation permissions of the topic.                                                                                                                                                          |
      |                                                  |                                                                              |                                                                                                                                                                                                                               |
      |                                                  | The services that can publish messages to a topic vary in different regions. | .. note::                                                                                                                                                                                                                     |
      |                                                  |                                                                              |                                                                                                                                                                                                                               |
      |                                                  |                                                                              |    By default, Cloud Eye and Anti-DDoS have the permission to publish messages to topics created by all users. For details about how to use SMN in other cloud services, see user guides of the related services.             |
      +--------------------------------------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0151546390.png
