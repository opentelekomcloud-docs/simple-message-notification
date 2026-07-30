:original_name: en-us_topic_0043394891.html

.. _en-us_topic_0043394891:

Configuring a Topic Policy
==========================

Only users under the same account as the topic creator have the permissions to publish messages through the topic. Using topic policies, you can specify which users or cloud services can perform what topic operations, for example, querying topic details and publishing messages. Topic creators always have permissions over a topic even if they grant topic permissions to other users.


Configuring a Topic Policy
--------------------------

#. Log in to the management console.

#. In the upper left corner of the page, click |image1| and select the desired region and project.

#. Select **Application** > **Simple Message Notification**.

   The SMN console appears.

#. In the navigation pane, choose **Topics**.

   The **Topics** page appears.

#. Locate the target topic and choose **More** > **Configure Topic Policy** in the **Operation** column.

   Alternatively, click the topic name. In the upper right corner of the displayed page, click **Configure Topic Policy**.

#. In the **Configure Topic Policy** dialog box, configure the topic policy in basic mode.

   The basic mode simply specifies which users or cloud services have permissions to publish messages to the topic. For details, see :ref:`Table 1 <en-us_topic_0043394891__table41411027111244>`.

   .. _en-us_topic_0043394891__table41411027111244:

   .. table:: **Table 1** Parameters for configuring a topic policy in basic mode

      +--------------------------------------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                        | Value                                                                        | Description                                                                                                                                                                                                                       |
      +==================================================+==============================================================================+===================================================================================================================================================================================================================================+
      | Users who can publish messages to this topic     | Topic creator                                                                | Only users under the same account as the topic creator have the permissions to publish messages through the topic.                                                                                                                |
      +--------------------------------------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Users who can publish messages to this topic     | All users                                                                    | All users have the permissions to publish messages to the topic.                                                                                                                                                                  |
      +--------------------------------------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Users who can publish messages to this topic     | Specified user accounts                                                      | Only specified users have the permissions to publish messages to the topic. Users are specified in the **urn:csp:iam::domainId:root** format.                                                                                     |
      |                                                  |                                                                              |                                                                                                                                                                                                                                   |
      |                                                  |                                                                              | You only need to enter the domain ID and click **OK**. The system supplements all other required information for you. There is no limit to the number of IDs you enter, but the total size of a topic policy cannot exceed 30 KB. |
      |                                                  |                                                                              |                                                                                                                                                                                                                                   |
      |                                                  |                                                                              | To obtain your domain ID, log in to the SMN console. In the upper right corner, hover the mouse over your login account and select **My Credentials** from the drop-down list.                                                    |
      |                                                  |                                                                              |                                                                                                                                                                                                                                   |
      |                                                  |                                                                              | Enter one account ID or URN per line.                                                                                                                                                                                             |
      +--------------------------------------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Services that can publish messages to this topic | Example: **OBS**                                                             | The selected cloud services have the permissions to publish messages to this topic.                                                                                                                                               |
      |                                                  |                                                                              |                                                                                                                                                                                                                                   |
      |                                                  | The services that can publish messages to a topic vary depending on regions. | .. note::                                                                                                                                                                                                                         |
      |                                                  |                                                                              |                                                                                                                                                                                                                                   |
      |                                                  |                                                                              |    By default, Cloud Eye and Anti-DDoS have the permissions to publish messages to topics created by all users. For details about how to use SMN, see user guides of the related services.                                        |
      +--------------------------------------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0151546390.png
