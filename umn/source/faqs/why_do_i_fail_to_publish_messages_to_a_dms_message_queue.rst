:original_name: smn_faq_0022.html

.. _smn_faq_0022:

Why Do I Fail to Publish Messages to a DMS Message Queue?
=========================================================

Check whether required permissions of the DMS message queue are granted to SMN.

-  If no, perform the following operations to grant permissions.
-  If yes, but you still cannot push messages, the failure may be caused by unstable network connection or other reasons. Contact customer service to address the issue.

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. In the queue list, locate the required queue and click its name.

   Details of the queue are displayed.

#. On the **Policy Management** tab, click **Create Queue Policy**.

   Set **Permission** to **Allow**, **Policy Type** to **Service-based**, and **Service** to **SMN**. Specify the action as needed.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0238428725.png
