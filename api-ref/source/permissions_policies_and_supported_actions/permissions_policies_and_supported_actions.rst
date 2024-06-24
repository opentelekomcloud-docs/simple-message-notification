:original_name: en-us_topic_0173558608.html

.. _en-us_topic_0173558608:

Permissions Policies and Supported Actions
==========================================

This section describes fine-grained permissions management for your SMN resources. If your account does not need individual IAM users, you can skip over this section.

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles: A type of coarse-grained authorization mechanism that defines service-level permissions based on user responsibilities. There are only a limited number of roles for granting permissions to users. Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization and secure access control.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all of the permissions required to call all APIs, but IAM users must have the required permissions specifically assigned. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query ECSs using an API, the user must have been granted permissions that allow the **ecs:servers:list** action.

Supported Actions
-----------------

IAM provides system-defined policies that can be directly used. You can also create custom policies to supplement system-defined policies for more refined access control. Actions supported by policies are specific to APIs. Common concepts related to policies include:

-  Permissions: Statements in a policy that allow or deny certain operations.
-  APIs: REST APIs that can be called by a user who has been granted specific permissions.
-  Actions: Specific operations that are allowed or denied.
-  Related actions: Actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the dependent actions.
-  IAM or enterprise projects: Type of projects for which an action will take effect. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that only contain actions for IAM projects can be used and only take effect for IAM. Administrators can check whether an action supports IAM projects or enterprise projects in the action list. "Y" indicates that the action supports the project and "x" indicates that the action does not support the project.

SMN supports the following actions that can be defined in custom policies:

-  :ref:`Topic Operations <en-us_topic_0173593941>`, including actions supported by topic management APIs, such as APIs for creating, querying, updating, and deleting topics
-  :ref:`Template Operations <en-us_topic_0173593943>`, including actions supported by message template management APIs, such as the APIs for creating, querying, updating, and deleting message templates
-  :ref:`Tag Operations <en-us_topic_0173593946>`, including actions supported by TMS APIs, such as the APIs for querying resources, adding a resource tag, adding or deleting resource tags in batches, and deleting a resource a tag
-  :ref:`Message Publishing <en-us_topic_0173593944>`, including actions supported by message publishing management APIs, such as the message publishing API
-  :ref:`Sending an Application Message <en-us_topic_0173593949>`, including actions supported by direct application messaging management API, such as the API for sending an application message
