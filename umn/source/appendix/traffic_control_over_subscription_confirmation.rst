:original_name: smn_ug_a4000.html

.. _smn_ug_a4000:

Traffic Control over Subscription Confirmation
==============================================

To prevent malicious users from harassing subscribers, SMN limits the number of subscription confirmation messages a user can send to an individual subscriber within a specified period of time. Traffic control policies apply to confirmation requests issued both from the SMN console and by API calling.

Traffic control policies for different subscription protocols are as follows:

-  Email: Up to 20 subscription confirmation emails can be sent within one hour and up to 40 subscription confirmation emails can be sent within two days. If 20 subscription confirmation emails have been sent within one hour, SMN will not send subscription confirmation emails to the endpoint in the next hour. If 40 subscription confirmation emails have been sent within two days, no subscription confirmation email will be sent to the endpoint within the next seven days. If the subscriber confirms the subscription, SMN clears the count in the traffic control policy.
-  SMS: Up to 10 subscription confirmation messages can be sent within one hour and up to 20 subscription confirmation messages can be sent within two days. If 10 subscription confirmation messages have been sent within one hour, SMN will not send subscription confirmation messages to the endpoint in the next hour. If 20 subscription confirmation messages have been sent within two days, no subscription confirmation message will be sent to the endpoint within the next seven days. After the subscriber confirms the subscription, SMN clears the count in the traffic control policy.
-  HTTP or HTTPS: Up to 200 confirmation messages can be sent within 10 minutes.

.. note::

   The preceding limitations are for reference only and will be adjusted based on service requirements.
