:original_name: smn_ug_90001.html

.. _smn_ug_90001:

Audit Using CTS
===============

CTS records SMN-related operations, including request content, source IP addresses, request senders, and the time when a request was sent, for future query, audit, and backtracking.

Prerequisites
-------------

You have enabled CTS.

SMN Operations Recorded by CTS
------------------------------

.. table:: **Table 1** SMN operations recorded by CTS

   =============================== ================ =====================
   Operation                       Resource Type    Trace Name
   =============================== ================ =====================
   Creating a topic                topic            createTopic
   Deleting a topic                topic            deleteTopic
   Updating a topic                topic            updateTopic
   Updating a topic policy         topic            updateTopicAttribute
   Adding a subscription           subscription     subscribe
   Deleting a subscription         subscription     delsubscribe
   Creating a message template     message_template createMessageTemplate
   Modifying a message template    message_template updateMessageTemplate
   Deleting a message template     message_template deleteMessageTemplate
   Adding resource tags in batches tag              batchCreateTag
   Deleting a resource tag         tag              deleteTag
   =============================== ================ =====================

Viewing Traces
--------------

For details about how to view SMN traces, see `Querying Real-Time Traces <https://docs.otc.t-systems.com/en-us/usermanual/cts/en-us_topic_0030598499.html>`__.
