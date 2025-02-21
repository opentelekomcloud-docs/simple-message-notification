:original_name: smn_ug_a2000.html

.. _smn_ug_a2000:

Template Message Format
=======================

Message templates are used to publish messages with fixed content and use variables as placeholders to represent content that you can change.

The size of template message cannot exceed 256 KB. The following is an example of how to format a template when you manually type the template message content:

.. code-block::

   {
      "message_template_name":"confirm_message",
      "tags":{
          "topic_urn":"urn:smn:regionId:xxxx:SMN_01"
       }
   }

.. table:: **Table 1** Parameters description and setting

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Description                                                                                                                                                                                                                                                          |
   +=======================+======================================================================================================================================================================================================================================================================+
   | message_template_name | Specifies the template name, which must be specified. You can query the template name in the template list. You must create a template of the default protocol so that SMN can send messages using the default template once it fails to match a specified protocol. |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Variables in the template, which are presented as JSON mappings. You can create templates for different protocols using the same template name and configure different variables in each template.                                                                   |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
