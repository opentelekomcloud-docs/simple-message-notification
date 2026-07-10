:original_name: smn_ug_0085.html

.. _smn_ug_0085:

Overview
========

What Is a Message Template?
---------------------------

Message templates contain fixed and changeable content and can be used to create and send messages more quickly. When you use a template to publish a message, you can specify values for different variables in the template.

Message templates are identified by name, but you can create different templates with the same name as long as they are configured for different protocols. You must create a **Default** template with the same name as each custom template. The **Default** template is used when no specific template has been set for a given protocol. If a template is configured for a specific protocol, any subscriber who chose that protocol during subscription will receive messages using that specific template. If you create a custom template but do not create a default template with the same name, you cannot use the custom template to publish messages.
