:original_name: smn_ug_0013.html

.. _smn_ug_0013:

CTS Traces
==========

Scenarios
---------

After CTS is enabled, it starts recording operations on cloud resources. You can view the operation records of the last seven days on the management console.

This topic describes how to query or export the last seven days of operation records on the CTS console.

Procedure
---------

#. Log in to the management console.

#. Click |image1| on the upper left to select the desired region and project.

#. Click **Service List** in the upper left corner. Under **Management & Deployment**, select **Cloud Trace Service**.

#. In the left navigation pane, choose **Trace List**.

#. Specify filters as needed. The following filters are available:


   .. figure:: /_static/images/en-us_image_0245209654.png
      :alt: **Figure 1** Filters

      **Figure 1** Filters

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**

      Select the filter from the drop-down list.

      -  When you select **Trace name** for **Search By**, you also need to select a specific trace name.
      -  When you select **Resource ID** for **Search By**, you also need to enter a resource ID.
      -  When you select **Resource name** for **Search By**, select or enter a specific resource name.

   -  **Operator**: Select a specific operator.

   -  **Trace Status**: Available options include **All trace statuses**, **Normal**, **Warning**, and **Incident**. You can select only one of them.

   -  Time range: You can query traces generated at any time range of the last seven days.

#. Click |image2| on the left of the required trace to expand its details.

#. Click **View Trace**.

CTS Log Entries
---------------

Each log entry consists of a trace in JSON format. A log entry indicates an SMN API request, including the requested operation, the date and time, operation parameters, and information about the user who sent the request. The user information is obtained from the Identity and Access Management (IAM) service.

The following example shows CTS log entries for the **CreateTopic**, **DeleteTopic**, and **UpdateTopic** actions:

.. code-block::

   {
      "time": "2017-02-15 14:21:50 GMT+08:00",
      "user": "xxx",
      "request": "xxx",
      "response": "xxx",
      "code": 200,
      "service_type": "SMN",
      "resource_type": "topic",
      "resource_id": "topicUrn instance",
      "source_ip": "127.0.0.1",
      "trace_name": "createTopic",
      "trace_rating": "normal",
      "trace_type": "ApiCall",
      "api_version": "2.0",
      "project_id": "tenantId instance",
      "record_time": "2017-02-15 14:21:50 GMT+08:00",
      "trace_id": "xxx"
   }

   {
      "time": "2017-02-15 14:12:15 GMT+08:00",
      "user": "xxx",
      "response": "xxx",
      "code": 200,
      "service_type": "SMN",
      "resource_type": "topic",
      "resource_id": "topicUrn instance",
      "source_ip": "127.0.0.1",
      "trace_name": "deleteTopic",
      "trace_rating": "normal",
      "trace_type": "ApiCall",
      "api_version": "2.0",
      "project_id": "tenantId instance",
      "record_time": "2017-02-15 14:12:15 GMT+08:00",
      "trace_id": "xxx"
   }

   {
      "time": "2017-02-13 15:38:30 GMT+08:00",
      "user": "xxx",
      "request": "xxx",
      "response": "xxx",
      "code": 200,
      "service_type": "SMN",
      "resource_type": "topic",
      "resource_id": "topicUrn instance",
      "source_ip": "127.0.0.1",
      "trace_name": "updateTopic",
      "trace_rating": "normal",
      "trace_type": "ApiCall",
      "api_version": "2.0",
      "project_id": "tenantId instance",
      "record_time": "2017-02-13 15:38:30 GMT+08:00",
      "trace_id": "xxx"
   }

.. |image1| image:: /_static/images/en-us_image_0151546390.png
.. |image2| image:: /_static/images/en-us_image_0238437725.jpg
