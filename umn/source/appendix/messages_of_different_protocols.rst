:original_name: smn_ug_a3000.html

.. _smn_ug_a3000:

Messages of Different Protocols
===============================

Messages delivered to endpoints using different protocols contain different content.

-  Email or HTTP/HTTPS endpoints will receive the message subject, content, and a link to unsubscribe.

-  SMS endpoints will only receive the message content.

-  DMS messages contain the message subject, content, and topic URN. :ref:`Table 1 <smn_ug_a3000__table64014010193925>` describes parameters in DMS messages. The following is an example message:

   .. code-block::

      {
         "message":[{
            "body":"{
              "event_version":"1.0",
              "subject":"test",
              "event_source":"smn",
              "event_subscription_urn":"urn:smn:regionId:c5acb70716ec4d489213da33e06b15f6:smn_123:47cff941a17f435ea5f6091d3579664e",
              "message_id":"174a38fb1ef24724bf8043954b7330c9",
              "topic_urn":"urn:smn:regionId:c5acb70716ec4d489213da33e06b15f6:smn_123",
              "type":"notification",
              "message":"Hello",
              "timestamp":"2017-10-24T09:37:02Z"
             }"
        ]}
      }

   .. _smn_ug_a3000__table64014010193925:

   .. table:: **Table 1** Parameters in a DMS message

      ====================== =========== ================
      Parameter              Type        Description
      ====================== =========== ================
      message                JSON object Message list
      body                   String      Message body
      event_version          String      Version
      subject                String      Message subject
      event_source           String      Message source
      event_subscription_urn String      Subscription URN
      message_id             String      Message ID
      topic_urn              String      Topic URN
      type                   String      Message type
      message                String      Message content
      timestamp              String      Timestamp
      ====================== =========== ================
