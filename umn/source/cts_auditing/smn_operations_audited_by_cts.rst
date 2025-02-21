:original_name: smn_ug_0012.html

.. _smn_ug_0012:

SMN Operations Audited by CTS
=============================

After you enable CTS, whenever an SMN API is called, the operation may be recorded in a log file, which is then dumped to a specified OBS bucket for storage based on time and data changes.

However, if someone calls the SMN API to cancel a subscription without login, CTS will not record the operation. For example, if a subscriber clicks the link in an email to cancel the subscription, the API for unsubscribing is called, but CTS does not record the operation.

:ref:`Table 1 <smn_ug_0012__table2434760155120>` lists the SMN operations that will be recorded by CTS.

.. _smn_ug_0012__table2434760155120:

.. table:: **Table 1** SMN operations recorded by CTS

   ============================ ================ =====================
   Operation                    Resource Type    Trace Name
   ============================ ================ =====================
   Creating a topic             topic            createTopic
   Deleting a topic             topic            deleteTopic
   Updating a topic             topic            updateTopic
   Updating a topic policy      topic            updateTopicAttribute
   Adding a subscription        subscription     subscribe
   Deleting a subscription      subscription     delsubscribe
   Creating a message template  message_template createMessageTemplate
   Modifying a message template message_template updateMessageTemplate
   Deleting a message template  message_template deleteMessageTemplate
   Batch adding tags            tag              batchCreateTag
   Deleting a tag               tag              deleteTag
   ============================ ================ =====================
