:original_name: smn_ug_a9005.html

.. _smn_ug_a9005:

Using a Subscription Filter Policy
==================================

Scenarios
---------

This section describes how to configure a subscription filter policy when adding a subscription to specify the scope of message publishing. A subscription filter policy applies to message attributes. If you have set filter policies and message attributes when publishing a message, the system determines whether to push the message to subscribers based on the filter policy you set.

In this example, the filter attributes are based on the enterprise team and job position dimensions:

-  company: enterprise team (**group_a**, **group_b**, and **group_c**)
-  position: job position (**admin**: O&M administrator, **finance**: finance, **dev**: R&D, and **ops**: O&M)

Prerequisites
-------------

A topic has been created. For details, see :ref:`Creating a Topic <en-us_topic_0043961401>`.

Adding a Subscription
---------------------

You can add the following subscriptions to the created topic by referring to :ref:`Adding a Subscription to a Topic <en-us_topic_0043961402>`.

For details about how to configure subscription filter policies, see `Creating Message Filter Policies for a Subscriber <https://docs.otc.t-systems.com/en-us/api/smn/smn_api_91000.html>`__ in the *Simple Message Notification API Reference*.

For details about how to configure message attributes, see :ref:`Table 2 <en-us_topic_0043961403__table17341132634914>`.

-  If you add a subscription endpoint A to the topic and want finance and R&D personnel from teams **group_a** and **group_b** to receive only **finance** and **dev** messages, you can configure the following subscription filter policy when creating subscription A:

   .. code-block::

      {
          "filter_polices":[
              {
                  "name":"company",
                  "string_equals":[
                      "group_a",
                      "group_b"
                  ]
              },
              {
                  "name":"position",
                  "string_equals":[
                      "finance",
                      "dev"
                  ]
              }
          ]
      }

-  If you add a subscription endpoint B to the topic and want the O&M administrators from teams **group_b** and **group_c** to receive only **admin** and **ops** alarm notifications, you can configure the following subscription filter policy when creating subscription B:

   .. code-block::

      {
          "filter_polices":[
              {
                  "name":"company",
                  "string_equals":[
                      "group_b",
                      "group_c"
                  ]
              },
              {
                  "name":"position",
                  "string_equals":[
                      "admin",
                      "ops"
                  ]
              }
          ]
      }

Publishing a Message
--------------------

When you publish a message to a topic, the following scenarios may occur depending on the added subscriptions.

For details about how to publish a message, see :ref:`Introduction <en-us_topic_0044170758>`.

-  Scenario 1

   The message attribute fields are as follows:

   .. code-block::

      {
          "name":"company",
          "type":"STRING",
          "value":[
              "group_a"
          ]
      }

   Sending result: In the message attributes, only **company** is specified, and **position** is not specified. Therefore, this message will only be sent to subscription A.

-  Scenario 2:

   The message attribute fields are as follows:

   .. code-block::

      [
          {
              "name":"company",
              "type":"STRING",
              "value":[
                  "group_a"
              ]
          },
          {
              "name":"position",
              "type":"STRING",
              "value":[
                  "ops"
              ]
          }
      ]

   Sending result: This message is intended for subscribers in **group_a** holding the **ops** (O&M) position. Neither subscription A nor subscription B matches the criteria. Therefore, this message will not be sent to subscription A or subscription B.

-  Scenario 3:

   The message attribute fields are as follows:

   .. code-block::

      [
          {
              "name":"company",
              "type":"STRING",
              "value":[
                  "group_c"
              ]
          },
          {
              "name":"position",
              "type":"STRING",
              "value":[
                  "admin"
              ]
          }
      ]

   Sending result: This message is intended for subscribers in **group_c** holding the **admin** (O&M administrator) position. Subscription A does not match the criteria, whereas subscription B is an exact match. Therefore, this message will only be sent to subscription B.

-  Scenario 4

   The message attribute fields are as follows:

   .. code-block::

      [
          {
              "name":"company",
              "type":"STRING",
              "value":[
                  "group_b"
              ]
          },
          {
              "name":"position",
              "type":"STRING",
              "value":[
                  "finance"
              ]
          }
      ]

   Sending result: This message is intended for subscribers in **group_b** holding the **finance** position. Subscription A matches the criteria, whereas subscription B does not. Therefore, this message will not be sent to subscription B.

-  Scenario 5

   The message attribute fields are as follows:

   .. code-block::

      [
          {
              "name":"company",
              "type":"STRING_ARRAY",
              "value":[
                  "group_a",
                  "group_b",
                  "group_c"
              ]
          },
          {
              "name":"position",
              "type":"STRING_ARRAY",
              "value":[
                  "dev",
                  "ops"
              ]
          }
      ]

   Sending result: This message covers all teams and includes both **dev** (R&D) and **ops** (O&M) positions. Both subscription A and subscription B matches the criteria. Therefore, this message will be sent to both subscription A and subscription B.

-  Scenario 6

   No subscription filter policy is configured.

   Sending result: Messages with any non-protocol message attributes will not be sent to subscriptions that do not have a subscription filter policy configured.

-  Scenario 7

   No subscription filter policy is configured, and no message attribute is specified.

   Sending result: Messages will be sent to all subscriptions.
