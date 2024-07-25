:original_name: smn_api_51007.html

.. _smn_api_51007:

Updating a Topic Policy
=======================

Description
-----------

-  API name

   UpdateTopicAttribute

-  Function

   Update a topic policy.

URI
---

-  URI format

   PUT /v2/{project_id}/notifications/topics/{topic_urn}/attributes/{name}

-  Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                       |
   +=================+=================+=================+===================================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                        |
   |                 |                 |                 |                                                                                                                   |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it by referring to :ref:`Querying Topics <en-us_topic_0036016755>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | Specifies the policy name.                                                                                        |
   |                 |                 |                 |                                                                                                                   |
   |                 |                 |                 | Only specified policy names are supported. For details, see :ref:`Topic Attribute List <smn_api_a1000>`.          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================+
   | value           | Yes             | String          | Topic attribute value                                                                                                              |
   |                 |                 |                 |                                                                                                                                    |
   |                 |                 |                 | -  If you set **name** to **access_policy**, **value** is the topic attributes, and the maximum length of **value** is 30 KB.      |
   |                 |                 |                 | -  If you set **name** to **introduction**, **value** is the topic introduction, and the maximum length of **value** is 120 bytes. |
   |                 |                 |                 |                                                                                                                                    |
   |                 |                 |                 | For details, see :ref:`Table 1 <smn_api_51007__table53240944112753>`.                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_51007__table53240944112753:

   .. table:: **Table 1** Topic attribute values

      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                                                                                                            | Constraint                                                                                                                                        |
      +===========+========================================================================================================================================================================================+===================================================================================================================================================+
      | Version   | Policy specification version                                                                                                                                                           | Only **2016-09-07** is supported.                                                                                                                 |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Id        | Policy ID, which uniquely identifies a policy                                                                                                                                          | **Id** must be specified.                                                                                                                         |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Statement | Statements used to configure a topic policy. Each topic policy may contain one or more statements. You can use statements to grant topic permissions to other users or cloud services. | A policy must contain at least one statement. For details about elements in a statement, see :ref:`Table 2 <smn_api_51007__table13574080155334>`. |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_51007__table13574080155334:

   .. table:: **Table 2** Statement elements description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Element               | Description                                                                                                                                                                                                              | Constraint                                                                                                                                              |
      +=======================+==========================================================================================================================================================================================================================+=========================================================================================================================================================+
      | Sid                   | Statement ID                                                                                                                                                                                                             | The statement ID must be unique, for example, **statement01** or **statement02**.                                                                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                | Statement effect                                                                                                                                                                                                         | The effect can be **Allow** or **Deny**.                                                                                                                |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal             | -  **Principal**: object to which the statement applies                                                                                                                                                                  | Either the **Principal** or **NotPrincipal** element must be configured.                                                                                |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                         |
      | NotPrincipal          | -  **NotPrincipal**: object to which the statement does not apply                                                                                                                                                        | -  If you enter **CSP**, you must specify user information in the format **urn:csp:iam::domainId:root**. Obtain the domain ID of each user you specify. |
      |                       |                                                                                                                                                                                                                          | -  If you enter **Service**, you must specify the cloud service names in lower case.                                                                    |
      |                       |    The following two types of objects are supported:                                                                                                                                                                     |                                                                                                                                                         |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                         |
      |                       |    -  **CSP**: one or more cloud users                                                                                                                                                                                   |                                                                                                                                                         |
      |                       |    -  **Service**: one or more cloud services                                                                                                                                                                            |                                                                                                                                                         |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Action                | -  **Action**: allowed statement action                                                                                                                                                                                  | Either **Action** or **NotAction** must be configured.                                                                                                  |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                         |
      | NotAction             | -  **NotAction**: statement action not allowed                                                                                                                                                                           | The following actions are supported:                                                                                                                    |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                         |
      |                       |    You can use a wildcard character to configure a set of actions, for example, **SMN:Update\*** and **SMN:Delete\***. If you only enter a wildcard character (``*``) in a statement, all supported actions are allowed. | -  SMN:UpdateTopic                                                                                                                                      |
      |                       |                                                                                                                                                                                                                          | -  SMN:DeleteTopic                                                                                                                                      |
      |                       |                                                                                                                                                                                                                          | -  SMN:QueryTopicDetail                                                                                                                                 |
      |                       |                                                                                                                                                                                                                          | -  SMN:ListTopicAttributes                                                                                                                              |
      |                       |                                                                                                                                                                                                                          | -  SMN:UpdateTopicAttribute                                                                                                                             |
      |                       |                                                                                                                                                                                                                          | -  SMN:DeleteTopicAttributes                                                                                                                            |
      |                       |                                                                                                                                                                                                                          | -  SMN:DeleteTopicAttributeByName                                                                                                                       |
      |                       |                                                                                                                                                                                                                          | -  SMN:ListSubscriptionsByTopic                                                                                                                         |
      |                       |                                                                                                                                                                                                                          | -  SMN:Subscribe                                                                                                                                        |
      |                       |                                                                                                                                                                                                                          | -  SMN:Unsubscribe                                                                                                                                      |
      |                       |                                                                                                                                                                                                                          | -  SMN:Publish                                                                                                                                          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource              | Specifies the topic the statement applies to.                                                                                                                                                                            | Either **Resource** or **NotResource** must be configured.                                                                                              |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                         |
      |                       |                                                                                                                                                                                                                          | You need to enter a topic URN.                                                                                                                          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | NotResource           | Specifies the topic the statement does not apply to.                                                                                                                                                                     | Either **Resource** or **NotResource** must be configured.                                                                                              |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                         |
      |                       |                                                                                                                                                                                                                          | You need to enter a topic URN.                                                                                                                          |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      PUT https://{SMN_Endpoint}/v2/{project_id}/notifications/topics/{topic_urn}/attributes/access_policy

   .. code-block::

      {
         "value": "{
               \"Version\": \"2016-09-07\",
               \"Id\": \"__default_policy_ID\",
               \"Statement\": [
                  {
                    \"Sid\": \"__user_pub_0\",
                    \"Effect\": \"Allow\",
                    \"Principal\": {
                      \"CSP\": [
                              \"urn:csp:iam::{domainID}:root\"
                             ]
                       },
                    \"Action\": [\"SMN:Publish\",\"SMN:QueryTopicDetail\"],
                    \"Resource\": \"{topic_urn}\"
                    },
                    {
                    \"Sid\": \"__service_pub_0\",
                    \"Effect\": \"Allow\",
                    \"Principal\": {
                       \"Service\": [\"obs\"]
                       },
                    \"Action\": [\"SMN:Publish\",\"SMN:QueryTopicDetail\"],
                    \"Resource\": \"{topic_urn}\"
                    }
                   ]
                }"
        }

   .. note::

      Replace **{project_id}**, **{domainID}**, and **{topic_urn}** with the actual values.

      **domainID** indicates the user's account ID. To obtain it, log in to the SMN console, click **My Credentials** in the username drop-down list on the upper right.

Response
--------

-  Parameter description

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   request_id String Request ID, which is unique
   ========== ====== ===========================

-  Example response

   .. code-block::

      {
          "request_id":"6837531fd3f54550927b930180a706bf"
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Codes <smn_api_64000>`.
