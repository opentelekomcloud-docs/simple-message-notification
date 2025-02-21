:original_name: smn_ug_a3000.html

.. _smn_ug_a3000:

Messages Using Different Protocols
==================================

Message contents delivered to endpoints using different protocols may differ.

-  Email or HTTP/HTTPS endpoints will receive the message subject, content, and a link to unsubscribe.

-  SMS endpoints receive only the message content.

-  FunctionGraph (function) messages contain the message attributes, subject, content, and topic URN. :ref:`Table 1 <smn_ug_a3000__table66871305193114>` describes parameters in FunctionGraph (function) messages. The following is an example message:

   .. code-block::

      {
         "record": [{
             "event_version": "1.0",
             "smn": {
                 "message_attributes": "",
                 "subject": "Welcome",
                 "message_id": "e6fa59c6b3e0424c9c02cbed35b680e7",
                 "topic_urn": "urn:smn:regionId:66e0f4622d6f4e3fb2db2e495298a61a:smn_123",
                 "type": "notification",
                 "message": "Hello",
                 "timestamp": "2017-08-17T10:07:14Z"                             },
             "event_source": "smn",
             "event_subscription_urn": "urn:cff:regionId:66e0f4622d6f4e3fb2db2e495298a61a:function:DEFAULT:mytest:latest"
             }]
      }

   .. _smn_ug_a3000__table66871305193114:

   .. table:: **Table 1** Parameters in a FunctionGraph (function) message

      ====================== =========== ==================
      Parameter              Type        Description
      ====================== =========== ==================
      record                 JSON object Message list
      event_version          String      Version
      message_attributes     String      Message attributes
      subject                String      Message subject
      message_id             String      Message ID
      topic_urn              String      Topic URN
      type                   String      Message type
      message                String      Message content
      timestamp              String      Timestamp
      event_source           String      Message source
      event_subscription_urn String      Subscription URN
      ====================== =========== ==================
