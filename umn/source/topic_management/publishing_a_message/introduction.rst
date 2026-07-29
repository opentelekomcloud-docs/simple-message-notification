:original_name: en-us_topic_0044170758.html

.. _en-us_topic_0044170758:

Introduction
============

SMN enables you to publish messages in the following formats:

-  :ref:`Publishing a Text Message <en-us_topic_0043961403>`
-  :ref:`Publishing a JSON Message <en-us_topic_0044170767>`
-  :ref:`Publishing a Template Message <en-us_topic_0044170770>`

After you publish a message to a topic, SMN will deliver the message to all confirmed subscription endpoints in the topic.

For SMS endpoints, if an SMS message is oversized, the system divides it into multiple parts when sending it to subscribers. However, you must note that SMN only sends the first two parts of the SMS message and does not send any additional parts. You are charged based on the actual number of messages sent to the subscribers.

For HTTP or HTTPS endpoints, you must ensure that firewall policies have been enabled for them to allow SMN to send messages over the Internet. An SMN HTTP or HTTPS message consists of a message header and body. For details, see :ref:`HTTP or HTTPS Message Format <smn_ug_a9002>`.

If FunctionGraph (function) is used to receive messages, the message contains message attributes, subject, content, and topic URN. For details, see :ref:`Messages Using Different Protocols <smn_ug_a3000>`.
