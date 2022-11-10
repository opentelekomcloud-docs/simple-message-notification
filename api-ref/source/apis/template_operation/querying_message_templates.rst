:original_name: smn_api_53004.html

.. _smn_api_53004:

Querying Message Templates
==========================

Description
-----------

-  API name

   ListMessageTemplates

-  Function

   Query the template list by page. The list is sorted by the template creation time in ascending order. If no template has been created, an empty list is returned. The parameters **message_template_name** and **protocol** are added.

.. note::

   The template list provides only brief information. To query the template details, see section :ref:`Querying the Message Template Details <smn_api_53005>`.

URI
---

-  URI format

   GET /v2/{project_id}/notifications/message_template?offset={offset}&limit={limit}&message_template_name={message_template_name}&protocol={protocol}

-  Parameter description

   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                         |
   +=======================+=================+=================+=====================================================================================================================================================================================+
   | project_id            | Yes             | String          | Project ID                                                                                                                                                                          |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`.                                                                                                                                  |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset                | No              | int             | Offset                                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | If the value is an integer greater than 0 but less than the number of resources, all resources after this offset will be queried. The default value is **0**.                       |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                 | No              | int             | -  Number of resources returned on each page                                                                                                                                        |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | -  Value range: 1-100                                                                                                                                                               |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 |    Commonly used values are **10**, **20**, and **50**.                                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 |    The default value is **100**.                                                                                                                                                    |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | message_template_name | No              | String          | Template name                                                                                                                                                                       |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | The template name is a string of 1 to 64 characters. It must contain upper- or lower-case letters, digits, hyphens (-), and underscores (_), and must start with a letter or digit. |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | No              | String          | Protocol supported by the template                                                                                                                                                  |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | Currently, the following protocols are supported:                                                                                                                                   |
   |                       |                 |                 |                                                                                                                                                                                     |
   |                       |                 |                 | -  **email**                                                                                                                                                                        |
   |                       |                 |                 | -  **default**                                                                                                                                                                      |
   |                       |                 |                 | -  **sms**                                                                                                                                                                          |
   |                       |                 |                 | -  **dms**                                                                                                                                                                          |
   |                       |                 |                 | -  **http** and **https**                                                                                                                                                           |
   +-----------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

Request example

.. code-block:: text

   GET https://{SMN_Endpoint}/v2/{project_id}/notifications/message_template?offset=0&limit=2&message_template_name=test1&protocol=email

Response
--------

-  Parameter description

   +------------------------+----------------------------------+-----------------------------------------------------------------------+
   | Parameter              | Type                             | Description                                                           |
   +========================+==================================+=======================================================================+
   | request_id             | String                           | Request ID, which is unique                                           |
   +------------------------+----------------------------------+-----------------------------------------------------------------------+
   | message_template_count | int                              | Number of returned templates                                          |
   +------------------------+----------------------------------+-----------------------------------------------------------------------+
   | message_templates      | Message template structure array | For details, see :ref:`Table 1 <smn_api_53004__table52721373195752>`. |
   +------------------------+----------------------------------+-----------------------------------------------------------------------+

   .. _smn_api_53004__table52721373195752:

   .. table:: **Table 1** Message template structure

      +-----------------------+-----------------------+---------------------------------------------------+
      | Parameter             | Type                  | Description                                       |
      +=======================+=======================+===================================================+
      | message_template_id   | String                | Template ID                                       |
      +-----------------------+-----------------------+---------------------------------------------------+
      | message_template_name | String                | Template name                                     |
      +-----------------------+-----------------------+---------------------------------------------------+
      | protocol              | String                | Protocol supported by the template                |
      |                       |                       |                                                   |
      |                       |                       | Currently, the following protocols are supported: |
      |                       |                       |                                                   |
      |                       |                       | -  **email**                                      |
      |                       |                       | -  **default**                                    |
      |                       |                       | -  **sms**                                        |
      |                       |                       | -  **dms**                                        |
      |                       |                       | -  **http** and **https**                         |
      +-----------------------+-----------------------+---------------------------------------------------+
      | tag_names             | String array          | Template variable list                            |
      +-----------------------+-----------------------+---------------------------------------------------+
      | create_time           | String                | Time when the template was created                |
      |                       |                       |                                                   |
      |                       |                       | The UTC time is in *YYYY-MM-DDTHH:MM:SSZ* format. |
      +-----------------------+-----------------------+---------------------------------------------------+
      | update_time           | String                | Last time when the template was updated           |
      |                       |                       |                                                   |
      |                       |                       | The UTC time is in *YYYY-MM-DDTHH:MM:SSZ* format. |
      +-----------------------+-----------------------+---------------------------------------------------+

-  Response example

   .. code-block::

      {
          "message_templates":[
              {
                  "message_template_name":"confirm_message",
                  "update_time":"2016-08-02T08:22:18Z",
                  "create_time":"2016-08-02T08:22:18Z",
                  "tag_names":[
                      "topic_urn"
                  ],
                  "message_template_id":"79227dfdf88d4e52a1820ca1eb411635"
              },
              {
                  "message_template_name":"confirm_message",
                  "protocol":"email",
                  "update_time":"2016-08-02T08:22:19Z",
                  "create_time":"2016-08-02T08:22:19Z",
                  "tag_names":[
                      "topic_id"
                  ],
                  "message_template_id":"ecf63465804a4b10a0573980be78ffba"
              },
              {
                  "message_template_name":"confirm_message",
                  "protocol":"https",
                  "update_time":"2016-08-02T08:22:20Z",
                  "create_time":"2016-08-02T08:22:20Z",
                  "tag_names":[
                      "topic_id"
                  ],
                  "message_template_id":"57ba8dcecda844878c5dd5815b65d10f"
              }
          ],
          "request_id":"ce7f2f7343224f8c9597b05a9a0bcc2e",
          "message_template_count":3
      }

Returned Value
--------------

See section :ref:`Returned Value <smn_api_63002>`.

Error Code
----------

See section :ref:`Error Code <smn_api_64000>`.
