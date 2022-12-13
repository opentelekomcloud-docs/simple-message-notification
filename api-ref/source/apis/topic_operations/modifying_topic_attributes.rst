:original_name: smn_api_51007.html

.. _smn_api_51007:

Modifying Topic Attributes
==========================

Description
-----------

-  API name

   UpdateTopicAttribute

-  Function

   Modify the topic attributes.

URI
---

-  URI format

   PUT /v2/{project_id}/notifications/topics/{topic_urn}/attributes/{name}

-  Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                 |
   +=================+=================+=================+=============================================================================================================+
   | project_id      | Yes             | String          | Project ID                                                                                                  |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource ID of a topic. You can obtain it according to :ref:`Querying Topics <smn_api_51004>`.       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | Attribute name                                                                                              |
   |                 |                 |                 |                                                                                                             |
   |                 |                 |                 | Only specified attribute names are supported. For details, see :ref:`Topic Attribute List <smn_api_a1000>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                          |
   +=================+=================+=================+======================================================================================================+
   | value           | Yes             | String          | Topic attribute value                                                                                |
   |                 |                 |                 |                                                                                                      |
   |                 |                 |                 | The value cannot exceed 30 KB. For details, see :ref:`Table 1 <smn_api_51007__table53240944112753>`. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+

   .. _smn_api_51007__table53240944112753:

   .. table:: **Table 1** Topic attribute values

      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name      | Description                                                                                                                                                                            | Restriction                                                                                                                                       |
      +===========+========================================================================================================================================================================================+===================================================================================================================================================+
      | Version   | Policy specification version                                                                                                                                                           | Currently, only **2016-09-07** is supported.                                                                                                      |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Id        | Policy ID, which uniquely identifies a policy                                                                                                                                          | The value cannot be empty.                                                                                                                        |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Statement | Statements used to configure a topic policy. Each topic policy may contain one or more statements. You can use statements to grant topic permissions to other users or cloud services. | A policy must contain at least one statement. For details about elements in a statement, see :ref:`Table 2 <smn_api_51007__table13574080155334>`. |
      +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _smn_api_51007__table13574080155334:

   .. table:: **Table 2** Statement elements description

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Element               | Description                                                                                                                                                                                                              | Restriction                                                                                                                                                         |
      +=======================+==========================================================================================================================================================================================================================+=====================================================================================================================================================================+
      | Sid                   | Statement ID                                                                                                                                                                                                             | The statement ID must be unique, for example, **statement01** or **statement02**.                                                                                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                | Statement effect                                                                                                                                                                                                         | The value can be **Allow** or **Deny**.                                                                                                                             |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Principal             | -  **Principal**: object to which the statement applies                                                                                                                                                                  | Either the **Principal** or **NotPrincipal** element must be configured.                                                                                            |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                                     |
      | NotPrincipal          | -  **NotPrincipal**: object to which the statement does not apply                                                                                                                                                        | -  If you enter **CSP**, you must specify user information in the format **urn:csp:iam::domainId:root**. You need to obtain the domain ID of each user you specify. |
      |                       |                                                                                                                                                                                                                          | -  If you enter **Service**, you must specify the cloud service names in lower case.                                                                                |
      |                       |    There are currently two supported values:                                                                                                                                                                             |                                                                                                                                                                     |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                                     |
      |                       |    -  **CSP**: one or more cloud users                                                                                                                                                                                   |                                                                                                                                                                     |
      |                       |    -  **Service**: one or more cloud services                                                                                                                                                                            |                                                                                                                                                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Action                | -  **Action**: allowed statement action                                                                                                                                                                                  | Either the **Action** or **NotAction** element must be configured.                                                                                                  |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                                     |
      | NotAction             | -  **NotAction**: statement action not allowed                                                                                                                                                                           | The following actions are supported:                                                                                                                                |
      |                       |                                                                                                                                                                                                                          |                                                                                                                                                                     |
      |                       |    You can use a wildcard character to configure a set of actions, for example, **SMN:Update\*** and **SMN:Delete\***. If you only enter a wildcard character (``*``) in a statement, all supported actions are allowed. | -  SMN:UpdateTopic                                                                                                                                                  |
      |                       |                                                                                                                                                                                                                          | -  SMN:DeleteTopic                                                                                                                                                  |
      |                       |                                                                                                                                                                                                                          | -  SMN:QueryTopicDetail                                                                                                                                             |
      |                       |                                                                                                                                                                                                                          | -  SMN:ListTopicAttributes                                                                                                                                          |
      |                       |                                                                                                                                                                                                                          | -  SMN:UpdateTopicAttribute                                                                                                                                         |
      |                       |                                                                                                                                                                                                                          | -  SMN:DeleteTopicAttributes                                                                                                                                        |
      |                       |                                                                                                                                                                                                                          | -  SMN:DeleteTopicAttributeByName                                                                                                                                   |
      |                       |                                                                                                                                                                                                                          | -  SMN:ListSubscriptionsByTopic                                                                                                                                     |
      |                       |                                                                                                                                                                                                                          | -  SMN:Subscribe                                                                                                                                                    |
      |                       |                                                                                                                                                                                                                          | -  SMN:Unsubscribe                                                                                                                                                  |
      |                       |                                                                                                                                                                                                                          | -  SMN:Publish                                                                                                                                                      |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource              | -  **Resource**: topic to which a statement applies                                                                                                                                                                      | Either the **Resource** or **NotResource** element must be configured.                                                                                              |
      |                       | -  **NotResource**: topic to which a statement does not apply                                                                                                                                                            |                                                                                                                                                                     |
      | NotResource           |                                                                                                                                                                                                                          | You need to enter a topic URN.                                                                                                                                      |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

      You need to replace **{project_id}**, **{domainID}**, and **{topic_urn}** with the actual values.

      **domainID** indicates the user's domain ID. To obtain it, log in to the SMN console, click **My Credential** in the username drop-down list on the upper right.

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

Error Code
----------

See :ref:`Error Code <smn_api_64000>`.
