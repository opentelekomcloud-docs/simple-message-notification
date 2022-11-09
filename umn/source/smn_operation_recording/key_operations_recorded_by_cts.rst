:original_name: smn_ug_0012.html

.. _smn_ug_0012:

Key Operations Recorded by CTS
==============================

After you enable CTS, whenever an SMN API is called, the operation is recorded in a log file, which is then delivered to a specified OBS bucket for storage.

However, if someone makes an API call to cancel a subscription without login, CTS will not record the operation. For example, if a subscriber clicks the link in an email notification to cancel the subscription, the Unsubscribe API is called, but CTS does not record the operation.

:ref:`Table 1 <smn_ug_0012__table2434760155120>` lists the SMN operations that will be recorded by CTS.

.. _smn_ug_0012__table2434760155120:

.. table:: **Table 1** SMN operations recorded by CTS

   +---------------------------------------+------------------+----------------------------+
   | Operation                             | Resource         | Trace Name                 |
   +=======================================+==================+============================+
   | Creating a topic                      | Topic            | createTopic                |
   +---------------------------------------+------------------+----------------------------+
   | Deleting a topic                      | Topic            | deleteTopic                |
   +---------------------------------------+------------------+----------------------------+
   | Updating a topic                      | Topic            | updateTopic                |
   +---------------------------------------+------------------+----------------------------+
   | Updating attributes of a topic        | Topic            | updateTopicAttribute       |
   +---------------------------------------+------------------+----------------------------+
   | Deleting all topic attributes         | Topic            | deleteTopicAttributes      |
   +---------------------------------------+------------------+----------------------------+
   | Deleting a specified topic attribute  | Topic            | deleteTopicAttributeByName |
   +---------------------------------------+------------------+----------------------------+
   | Adding a subscription                 | Subscription     | subscribe                  |
   +---------------------------------------+------------------+----------------------------+
   | Deleting a subscription               | Subscription     | unsubscribe                |
   +---------------------------------------+------------------+----------------------------+
   | Creating a message template           | Message template | createMessageTemplate      |
   +---------------------------------------+------------------+----------------------------+
   | Creating message templates in batches | Message template | batchCreateMessageTemplate |
   +---------------------------------------+------------------+----------------------------+
   | Modifying a message template          | Message template | updateMessageTemplate      |
   +---------------------------------------+------------------+----------------------------+
   | Deleting a message template           | Message template | deleteMessageTemplate      |
   +---------------------------------------+------------------+----------------------------+
