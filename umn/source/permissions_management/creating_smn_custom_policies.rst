:original_name: smn_ug_0038.html

.. _smn_ug_0038:

Creating SMN Custom Policies
============================

You can create custom policies to supplement the system-defined policies of SMN. For the actions supported by custom policies, see section "Permissions Policies and Supported Actions" in *Simple Message Notification API Reference*.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Create a JSON policy or edit an existing one.

The following are examples of custom policies created for SMN. .

Example SMN Custom Policies
---------------------------

-  Example 1: Grant permissions to create a topic.

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "smn:topic:create"
                  ]
              }
          ]
      }

-  Example 2: Grant permissions to deny topic deletion.

   A policy with only "Deny" permissions must be used with other policies. If the permissions granted to an IAM user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   You can assign a system policy of **SMN FullAccess** and a custom policy of denying topic deletion to the user group which the user belongs to at the same time. Thus the user can perform all operations on SMN except deleting topics. The following is an example of a deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Deny",
                  "Action": [
                      "smn:topic:delete"
                  ]
              }
          ]
      }

-  Example 3: Create a custom policy containing multiple actions.

   A custom policy can contain multiple actions that belong to any global or project-level services. The following is a custom policy containing multiple actions:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "smn:topic:create",
                      "smn:tag:create"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "elb:certificates:create",
                      "elb:whitelists:create",
                      "elb:pools:create",
                      "elb:members:create",
                      "elb:healthmonitors:create",
                      "elb:l7policies:create",
                      "elb:listeners:create",
                      "elb:loadbalancers:create"
                  ]
              }
          ]
      }
