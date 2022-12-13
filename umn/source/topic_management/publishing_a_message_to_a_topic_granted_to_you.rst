:original_name: smn_ug_47000.html

.. _smn_ug_47000:

Publishing a Message to a Topic Granted to You
==============================================

Scenarios
---------

If another user creates a topic and grants you permissions to publish messages, you can publish text or JSON messages to the topic.

Prerequisites
-------------

You have obtained the URN of the topic granted to you. For details about obtaining the URN of a topic, see :ref:`Creating a Topic <en-us_topic_0043961401>`.

To Publish a Message to a Topic Granted to You
----------------------------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Under **Application**, select **Simple Message Notification**.

   The SMN console is displayed.

#. On the **Dashboard** page, click **Publish Message**.

#. Specify the topic URN, message subject, and message format and enter your message content.

   .. note::

      Clicking |image2| beside **Topic URN** only enables you to select a topic you created, instead of a topic that you are granted permissions to.


   .. figure:: /_static/images/en-us_image_0095665783.png
      :alt: **Figure 1** Publishing a message to a topic granted to you

      **Figure 1** Publishing a message to a topic granted to you

   For more details, see :ref:`Publishing a Text Message <en-us_topic_0043961403>` and :ref:`Publishing a JSON Message <en-us_topic_0044170767>`.

.. |image1| image:: /_static/images/en-us_image_0259222503.png
.. |image2| image:: /_static/images/en-us_image_0148412674.png
