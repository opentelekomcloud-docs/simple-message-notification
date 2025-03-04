:original_name: smn_pd_22000.html

.. _smn_pd_22000:

Application Scenarios
=====================

-  **System notifications**

   After events or alarms are triggered, SMN can send notifications to specified users by email, SMS message, FunctionGraph (function), or HTTP/HTTPS message. For example, Cloud Trace Service (CTS) detects key cloud service operations and uses SMN to notify you and other users.

-  **Integrating with cloud services**

   SMN can function as a message middleware to directly connect cloud services, improving service efficiency. For example, Cloud Eye does not have to be integrated with Object Storage Service (OBS) to interact with each other. Instead, they can be connected by SMN, so faults in one service will not affect the other.

-  **Off-peak traffic control**

   If there is a discrepancy between processing capabilities of the upstream and downstream systems, SMN can cache data to reduce downstream pressure to reduce breakdowns, enhance availability, and mitigate complexity in the system.
