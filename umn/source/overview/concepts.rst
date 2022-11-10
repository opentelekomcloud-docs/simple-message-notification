:original_name: smn_pd_28000.html

.. _smn_pd_28000:

Concepts
========

Project
-------

Projects are used to group and isolate OpenStack resources, including computing, storage, and network resources. A project can be either a department or a project team. Multiple projects can be created in one account.

Protocol
--------

A protocol is a message type. Currently, SMN supports the following protocols: SMS, DMS, email, HTTP, and HTTPS.

Publisher
---------

A publisher sends messages to a topic.

Subscriber
----------

A subscriber receives messages delivered from a topic.

When adding a subscription, you can choose protocols as required:

-  For the email protocol, the subscriber is an email address.
-  For the SMS protocol, the subscriber is a phone number.
-  For the HTTP or HTTPS protocol, the subscriber is a URL.
-  For the DMS protocol, the subscriber is a message queue.

Topic
-----

A topic is a specified event to publish messages and subscribe to notifications. It can be used to isolate messages. A topic serves as a message sending channel, where publishers and subscribers can interact with each other.

URN
---

Uniform Resource Names (URNs) are used to identify SMN resources.

-  Topic URN

   After a topic is created, SMN generates a topic URN composed of the service name, region name, project ID, and topic name to uniquely identify the topic, for example, **urn:smn:region:cffe4fc4c9a54219b60dbaf7b586e132:Mytopic**. When you call an API to create a topic, a topic URN will be returned. A URN will be used whenever a publisher or subscriber performs operations to a topic.

-  Subscription URN

   After a user subscribes to a topic, SMN will generate a URN for the subscription composed of the service name, region name, project ID, and topic name, for example, **urn:smn:region:cffe4fc4c9a54219b60dbaf7b586e132:Mytopic:5293b436967f450abc51e0c36347b27a**. A URN is displayed on the page for subscribers to confirm and cancel a subscription.

Message Template
----------------

Message templates contain fixed and changeable content and can be used to send messages quickly. Changeable content is represented with variables. When you publish template messages, the system replaces the variables with the message content you specify.

Template Variable
-----------------

A message template contains fixed and changeable content. Changeable content is represented with variables. You can specify values for variables when publishing messages using a template.

For example, the template content is **The Arts and Crafts Exposition will be held from {startdate} through {enddate}. We sincerely invite you to join us.** In the content, **{startdate}** and **{enddate}** are variables.
