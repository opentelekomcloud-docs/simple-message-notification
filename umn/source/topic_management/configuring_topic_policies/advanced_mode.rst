:original_name: en-us_topic_0043394868.html

.. _en-us_topic_0043394868:

Advanced Mode
=============

The advanced mode provides a more flexible topic policy. You can specify which users and cloud services can perform which topic operations, for example, querying topic details, modifying topics, publishing messages, and deleting topics.

Introduction to Topic Policies
------------------------------

A topic policy is configured by a topic creator to allow or disallow other users or cloud services to perform specified operations to a topic. :ref:`Table 1 <en-us_topic_0043394868__table53240944112753>` lists the elements consisting of a topic policy.

.. _en-us_topic_0043394868__table53240944112753:

.. table:: **Table 1** Topic policy elements

   +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | **Parameter** | Description                                                                                                                                                     | Constraint                                                                                                                                                           |
   +===============+=================================================================================================================================================================+======================================================================================================================================================================+
   | Version       | Policy specification version                                                                                                                                    | Currently, only **2016-09-07** is supported.                                                                                                                         |
   +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Id            | Policy ID, which uniquely identifies a policy                                                                                                                   | The policy ID cannot be left blank.                                                                                                                                  |
   +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Statement     | Statements used to configure which users and cloud services can perform specified operations in a topic policy. Each policy may contain one or more statements. | A policy must contain at least one statement. For details about elements in a statement, see :ref:`Statement Elements <en-us_topic_0043394868__section19563388474>`. |
   +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following is an example topic policy, which contains two statements, **Statement1** and **Statement2**.

.. code-block::

   {
       "Version": "2016-09-07",
       "Id": "access_policy_01",
       "Statement": [
          {Statement1},
          {Statement2}
       ]
   }

.. _en-us_topic_0043394868__section19563388474:

Statement Elements
------------------

:ref:`Table 2 <en-us_topic_0043394868__table13574080155334>` lists the elements composed of a statement, as shown in the following example topic policy:

.. code-block::

   {
       "Version": "2016-09-07",
       "Id": "__default_policy_ID",
       "Statement": [
              //The first statement.
           {
               "Sid": "__user_pub_0",
               "Effect": "Allow",
               "Principal": {
                   "CSP": [
                       "urn:csp:iam::123456789:root",
                       "urn:csp:iam::987654321:root"
                   ]
               },
               "Action": [
                   "SMN:Publish",
                   "SMN:QueryTopicDetail"
               ],
               "Resource": "urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic"
           },
           //The second statement
          {
               "Sid": "__service_pub_0",
               "Effect": "Allow",
               "Principal": {
                   "Service": [
                       "obs"
                   ]
               },
               "Action": [
                   "SMN:Publish",
                   "SMN:QueryTopicDetail"
               ],
               "Resource": "urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic"
           }
       ]
   }

.. _en-us_topic_0043394868__table13574080155334:

.. table:: **Table 2** Statement elements description

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Element               | Description                                                                                                                                                                                                                     | Constraint                                                                                                                                                       |
   +=======================+=================================================================================================================================================================================================================================+==================================================================================================================================================================+
   | Sid                   | Statement ID                                                                                                                                                                                                                    | The statement ID must be unique, for example, **statement01** or **statement02**.                                                                                |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Effect                | Statement effect                                                                                                                                                                                                                | The value can be **Allow** or **Deny**.                                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Principal             | -  **Principal**: object to which the statement applies                                                                                                                                                                         | Either the **Principal** or **NotPrincipal** element must be configured.                                                                                         |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   | NotPrincipal          | -  **NotPrincipal**: object to which the statement does not apply                                                                                                                                                               | If you enter **CSP**, you must specify user information in the format **urn:csp:iam::domainId:root**. You need to obtain the domain ID of each user you specify. |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   |                       |    There are currently two supported values:                                                                                                                                                                                    | If you enter **Service**, you must specify the cloud service names in lower case.                                                                                |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   |                       |    -  **CSP**: Specify one or more cloud users.                                                                                                                                                                                 |                                                                                                                                                                  |
   |                       |    -  **Service**: Specify one or more cloud services.                                                                                                                                                                          |                                                                                                                                                                  |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action                | -  **Action**: allowed statement action                                                                                                                                                                                         | Either the **Action** or **NotAction** element must be configured.                                                                                               |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   | NotAction             | -  **NotAction**: statement action not allowed                                                                                                                                                                                  | The following actions are supported:                                                                                                                             |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   |                       |    You can use a wildcard character to configure a set of actions by type, for example, **SMN:Update\*** and **SMN:Delete\***. If you only enter a wildcard character (*) in a statement, all supported actions are configured. | -  SMN:UpdateTopic                                                                                                                                               |
   |                       |                                                                                                                                                                                                                                 | -  SMN:DeleteTopic                                                                                                                                               |
   |                       |                                                                                                                                                                                                                                 | -  SMN:QueryTopicDetail                                                                                                                                          |
   |                       |                                                                                                                                                                                                                                 | -  SMN:ListTopicAttributes                                                                                                                                       |
   |                       |                                                                                                                                                                                                                                 | -  SMN:UpdateTopicAttribute                                                                                                                                      |
   |                       |                                                                                                                                                                                                                                 | -  SMN:DeleteTopicAttributes                                                                                                                                     |
   |                       |                                                                                                                                                                                                                                 | -  SMN:DeleteTopicAttributeByName                                                                                                                                |
   |                       |                                                                                                                                                                                                                                 | -  SMN:ListSubscriptionsByTopic                                                                                                                                  |
   |                       |                                                                                                                                                                                                                                 | -  SMN:Subscribe                                                                                                                                                 |
   |                       |                                                                                                                                                                                                                                 | -  SMN:Unsubscribe                                                                                                                                               |
   |                       |                                                                                                                                                                                                                                 | -  SMN:Publish                                                                                                                                                   |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   |                       |                                                                                                                                                                                                                                 | For details about mappings between actions and APIs, see section :ref:`A.5 Mappings Between SMN Operations and APIs <smn_ug_a6000>`.                             |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource              | -  **Resource**: topic to which a statement applies                                                                                                                                                                             | Either the **Resource** or **NotResource** element must be configured.                                                                                           |
   |                       | -  **NotResource**: topic to which the statement does not apply                                                                                                                                                                 |                                                                                                                                                                  |
   | NotResource           |                                                                                                                                                                                                                                 | You need to enter a topic URN.                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Condition             | (Optional) Condition under which a policy statement takes effect                                                                                                                                                                | Enter supported condition operators and key words.                                                                                                               |
   |                       |                                                                                                                                                                                                                                 |                                                                                                                                                                  |
   |                       |                                                                                                                                                                                                                                 | For details, see :ref:`Condition Elements <en-us_topic_0043394868__section14635144017214>`.                                                                      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0043394868__section14635144017214:

Condition Elements
------------------

Conditions determine whether a statement takes effect. They enable you to configure more fine-grained control over topic permissions. :ref:`Table 3 <en-us_topic_0043394868__table101491067599>` lists elements in a condition.

.. _en-us_topic_0043394868__table101491067599:

.. table:: **Table 3** Condition elements

   +--------------------+--------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Description                                            | Constraint                                                                                                                                   |
   +====================+========================================================+==============================================================================================================================================+
   | Condition operator | Character string, numeral, date, or time to be matched | The time you entered must comply with ISO 8601 specifications. For details, see :ref:`Table 4 <en-us_topic_0043394868__table5968190619132>`. |
   +--------------------+--------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Key word           | Object to which the condition operation applies        | The key word cannot be left blank. For details, see :ref:`Table 5 <en-us_topic_0043394868__table2955116119132>`.                             |
   +--------------------+--------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

A statement allows the requested operation only when all conditions in the statement are met. Otherwise, the operation will be denied.

As shown in :ref:`Figure 1 <en-us_topic_0043394868__fig47755643154052>`, when a condition contains multiple operators, for example, **condition1** and **condition2**, an AND operation is executed.

When the operator **condition1** contains multiple keywords, for example, **conditionKey1** and **conditionKey2**, an AND operation is executed.

When the keyword **conditionKey1** contains multiple values, for example, **value11** and **value12**, an OR operation is executed.

.. _en-us_topic_0043394868__fig47755643154052:

.. figure:: /_static/images/en-us_image_0000001416865457.png
   :alt: **Figure 1** Condition logic

   **Figure 1** Condition logic

An example condition is as follows:

.. code-block::

   "Condition": {
       "DateLessThan":{
            "csp:CurrentTime":"2016-11-07T15:35:00Z"
       },
       "StringLike": {
            "smn:Endpoint":["*@gmail.com","*@hotmail.com"]
       }
   }

.. _en-us_topic_0043394868__table5968190619132:

.. table:: **Table 4** Condition operators

   +----------+---------------------------+------------------------------------------------------------------------------+
   | Category | Operator                  | Description                                                                  |
   +==========+===========================+==============================================================================+
   | String   | StringEquals              | Match a string (case-sensitive).                                             |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | StringNotEquals           | Exclude a string (case-sensitive).                                           |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | StringEqualsIgnoreCase    | Match a string (case-insensitive).                                           |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | StringNotEqualsIgnoreCase | Exclude a string (case-insensitive).                                         |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | StringLike                | Match a string. The value can contain one or more wildcard characters (*).   |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | StringNotLike             | Exclude a string. The value can contain one or more wildcard characters (*). |
   +----------+---------------------------+------------------------------------------------------------------------------+
   | Numeric  | NumericEquals             | Match an integer or decimal.                                                 |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | NumericNotEquals          | Exclude an integer or decimal.                                               |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | NumericLessThan           | Match any numeral less than an integer or decimal.                           |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | NumericLessThanEquals     | Match any numeral less than or equal to an integer or decimal.               |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | NumericGreaterThan        | Match any numeral greater than an integer or decimal.                        |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | NumericGreaterThanEquals  | Match any numeral greater than or equal to an integer or decimal.            |
   +----------+---------------------------+------------------------------------------------------------------------------+
   | Date     | DateEquals                | Match a date.                                                                |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | DateNotEquals             | Exclude a date.                                                              |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | DateLessThan              | Match any time earlier than a date and time point.                           |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | DateLessThanEquals        | Match any time earlier than or equal to a date and time point.               |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | DateGreaterThan           | Match any time later than a date and time point.                             |
   +----------+---------------------------+------------------------------------------------------------------------------+
   |          | DateGreaterThanEquals     | Match any time later than or equal to a date and time point.                 |
   +----------+---------------------------+------------------------------------------------------------------------------+
   | Bool     | Bool                      | Match a Boolean value.                                                       |
   +----------+---------------------------+------------------------------------------------------------------------------+

.. _en-us_topic_0043394868__table2955116119132:

.. table:: **Table 5** Condition key words

   +-----------------+------------------------------------------------------------------------------+
   | Key Word        | Description                                                                  |
   +=================+==============================================================================+
   | csp:CurrentTime | Current time                                                                 |
   +-----------------+------------------------------------------------------------------------------+
   | smn:Protocol    | Protocol of a subscription, which is valid only for the SMN:Subscribe action |
   +-----------------+------------------------------------------------------------------------------+
   | smn:Endpoint    | Endpoint of a subscription, which is valid only for the SMN:Subscribe action |
   +-----------------+------------------------------------------------------------------------------+
