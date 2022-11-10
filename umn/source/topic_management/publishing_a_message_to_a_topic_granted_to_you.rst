:original_name: smn_ug_47000.html

.. _smn_ug_47000:

Publishing a Message to a Topic Granted to You
==============================================

Scenario
--------

If another user creates a topic and grants you permissions to publish messages, you can publish text or JSON messages to the topic.

Prerequisites
-------------

You have obtained the URN of the topic granted to you. For details about obtaining the URN of a topic, see section :ref:`3.1 Creating a Topic <en-us_topic_0043961401>`.

To Publish a Message to a Topic Granted to You
----------------------------------------------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. In the **Application** category, click **Simple Message Notification**.

   The SMN console is displayed.

#. On the **Dashboard** page, click **Publish Message**.

#. Specify the topic URN, message subject, and message format and enter your message content.

   .. note::

      Clicking |image2| beside **Topic URN** only enables you to select a topic you created, instead of a topic to which you are granted permission.


   .. figure:: /_static/images/en-us_image_0000001366065808.png
      :alt: **Figure 1** Publishing a message to a topic granted to you

      **Figure 1** Publishing a message to a topic granted to you

   For more details, see sections :ref:`3.6.2 Publishing a Text Message <en-us_topic_0043961403>` and :ref:`3.6.3 Publishing a JSON Message <en-us_topic_0044170767>`.

.. |image1| image:: /_static/images/en-us_image_0000001416865417.png
.. |image2| image:: /_static/images/en-us_image_0000001417026841.png
