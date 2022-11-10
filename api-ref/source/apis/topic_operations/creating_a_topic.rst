:original_name: smn_api_51001.html

.. _smn_api_51001:

Creating a Topic
================

Description
-----------

-  API name

   CreateTopic

-  Function

   Create a topic. Each user can create 3000 topics at most. In the high-concurrent scenario, a user may create a few topics more than 3000.

   The API is idempotent. It returns a successful result after creating a topic. If a topic of the same name already exists, the status code is 200. Otherwise, the status code is 201.

URI
---

-  URI format

   POST /v2/{project_id}/notifications/topics

-  Parameter description

   +-----------------+-----------------+-----------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                        |
   +=================+=================+=================+====================================================+
   | project_id      | Yes             | String          | Project ID                                         |
   |                 |                 |                 |                                                    |
   |                 |                 |                 | See :ref:`Obtaining a Project ID <smn_api_66000>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------+

Request
-------

-  Parameter description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================+
   | name            | Yes             | String          | Name of the topic to be created                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | The topic name is a string of 1 to 255 characters. It must contain letters, digits, hyphens (-), and underscores (_), and must start with a letter or digit. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name    | No              | String          | Topic display name, which is presented as the name of the email sender in email messages                                                                     |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | The display name cannot exceed 192 bytes.                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | The value is left blank by default.                                                                                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Request example

   .. code-block:: text

      POST https://{SMN_Endpoint}/v2/{project_id}/notifications/topics

   .. code-block::

      {
          "name": "test_topic_v2",
          "display_name": "testtest"
      }

Response
--------

-  Parameter description

   +------------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                       |
   +============+========+===================================================================================================+
   | request_id | String | Request ID, which is unique                                                                       |
   +------------+--------+---------------------------------------------------------------------------------------------------+
   | topic_urn  | String | Unique resource ID of a topic. You can obtain it based on :ref:`Querying Topics <smn_api_51004>`. |
   +------------+--------+---------------------------------------------------------------------------------------------------+

-  Response example

   .. code-block::

      {
          "request_id": "6a63a18b8bab40ffb71ebd9cb80d0085",
          "topic_urn": "urn:smn:regionId:f96188c7ccaf4ffba0c9aa149ab2bd57:test_topic_v2"
      }

Returned Value
--------------

See :ref:`Returned Value <smn_api_63002>`.

Error Codes
-----------

See :ref:`Error Code <smn_api_64000>`.
