:original_name: smn_ug_a1000.html

.. _smn_ug_a1000:

JSON Message Format
===================

Description
-----------

The JSON format allows you to specify different message content for different subscription protocols, including **Default**, **SMS**, **HTTP**, **HTTPS**, **FunctionGraph (function)**, and **Email**. The message content you specify will be sent to subscription endpoints using applicable protocols.

.. code-block::

   {
     "default": "Dear Sir or Madam, this is a default message.",
     "email": "Dear Sir or Madam, this is an email message.",
     "http": "{'message':'Dear Sir or Madam, this is an HTTP message.'}",
     "https": "{'message':'Dear Sir or Madam, this is an HTTPS message.'}",
     "sms": "This is an SMS message."
     "functionstage": "Dear Sir or Madam, this is a functiongraph(function) message."
       }

It is recommended that you specify general message content for all subscription types in the **Default** protocol and enter customized content for specific protocols.

In the following example, you enter a shorter message for the SMS protocol because of the length limit on SMS messages. SMS subscribers in the topic receive the message "This is an SMS message.", while other types of subscribers (email, FunctionGraph (function), HTTP, and HTTPS) receive the one "Dear Sir or Madam, this is a default message."

.. code-block::

   {
     "sms": "This is an SMS message.",
     "default": "Dear Sir or Madam, this is a default message."
    }

Constraints
-----------

-  The content must be in JSON format.
-  You must configure the **Default** protocol in the JSON message.
-  The size of a JSON message cannot exceed 256 KB.

.. _smn_ug_a1000__section11977745123756:

Calculation on the Size of a JSON Message
-----------------------------------------

The size of a JSON message, including braces, quotation marks, spaces, line breaks, protocols, and message content, cannot exceed 256 KB. The size of a JSON message generated for each protocol may vary.

For example, message content "This is a default message." contains 26 bytes.

The system automatically adds the **Default** protocol when generating a JSON message.

.. code-block::

   {
     "default": "This is a default message.",
     "protocol1": "This is a default message.",
     "protocol2": "This is a default message.",
     ...
   }

The total number of protocols is *N*, including the **Default** protocol and those you selected.

The size of the message is calculated as follows:

-  Three spaces in each of the *N* protocols: 3 x *N* = 3\ *N* bytes
-  Four quotation marks in each of the *N* protocols: 4 x *N* = 4\ *N* bytes
-  One colon in each of the *N* protocols: 1 x *N* = *N* bytes
-  Message content "This is a default message." in each of the *N* protocols: 26 x *N* = 26\ *N* bytes
-  Commas in (*N* - 1) protocols: 1 x (*N* - 1) = (*N* - 1) bytes
-  Line breaks in (*N* + 1) protocols: 1 x (*N* + 1) = (*N* + 1) bytes
-  Two braces: 2 bytes
-  Protocol name **Default**: 7 bytes

Bytes of protocols you selected:

-  **HTTP**: 4 bytes
-  **HTTPS**: 5 bytes
-  **Email**: 5 bytes
-  **SMS**: 3 bytes
-  **FunctionStage**: 13 bytes

Total size = 36\ *N* + 9 + Bytes of protocols you selected

For example, you selected the HTTP, HTTPS, and email protocols, and the message is as follows:

.. code-block::

   {
     "default": "This is a default message.",
     "email": "This is a default message.",
     "http": "This is a default message.",
     "https": "This is a default message."
   }

The system adds a **Default** protocol, and the value of *N* is 4. The size of this JSON message is:

-  Fixed length: 36 x 4 + 9 = 153 bytes
-  **http**: 4 bytes
-  **https**: 5 bytes
-  **email**: 5 bytes

The total size is 167 bytes (153 + 4 + 5 + 5 = 167).
