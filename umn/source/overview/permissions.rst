:original_name: smn_ug_0034_1.html

.. _smn_ug_0034_1:

Permissions
===========

You can use Identity and Access Management (IAM) to manage SMN permissions and control access to your resources. IAM provides identity authentication, permissions management, and access control.

You can create IAM users for your employees and assign permissions to these users on a principle of least privilege (PoLP) basis to control their access to specific resource types. For example, you can create IAM users for software developers and assign specific permissions to allow them to use SMN resources but prevent them from being able to delete resources or perform any high-risk operations.

If your account does not require individual IAM users for permissions management, skip this section.

IAM can be used free of charge. You pay only for the resources in your account.

For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0026.html>`__.

SMN Permissions
---------------

By default, new IAM users do not have any permissions assigned. To assign permissions to these new users, add them to one or more groups and attach permissions policies or roles to these groups.

SMN is a project-level service deployed and accessed in specific physical regions. When assigning SMN permissions to a user group, specify region-specific projects where the permissions will take effect. If you select **All projects**, the permissions will be granted for all region-specific projects. When accessing SMN, the users need to switch to a region where they have been authorized to use this service.

You can grant users permissions by using roles and policies.

-  Roles: a type of coarse-grained authorization that provides only a limited number of service-level roles Services depend on each other. When granting permissions using roles, assign other dependent roles to users. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: a type of fine-grained authorization that defines permissions required to perform operations on specific cloud resources under certain conditions This authorization allows for more flexible policy-based authorization for secure access control. For example, you can grant SMN users only the permissions for managing a certain type of SMN resources. Most policies define permissions based on APIs. For the API actions supported by SMN, see section "Permissions Policies and Supported Actions" in the *Simple Message Notification API Reference*.

:ref:`Table 1 <smn_ug_0034_1__en-us_topic_0173524723_en-us_topic_0173475706_en-us_topic_0170232209_table481412518317>` lists all system-defined policies supported by SMN.

.. _smn_ug_0034_1__en-us_topic_0173524723_en-us_topic_0173475706_en-us_topic_0170232209_table481412518317:

.. table:: **Table 1** System-defined policies supported by SMN

   +--------------------+-----------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | Role/Policy Name   | Description                                                                                                     | Type                  | Dependency                                                                                    |
   +====================+=================================================================================================================+=======================+===============================================================================================+
   | SMN Administrator  | Has all permissions for SMN resources.                                                                          | System-defined role   | The **Tenant Guest** and **SMN Administrator** roles need to be assigned in the same project. |
   +--------------------+-----------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | SMN FullAccess     | Administrator permissions for SMN. Users granted these permissions can perform all operations on SMN resources. | System-defined policy | None                                                                                          |
   +--------------------+-----------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------+
   | SMN ReadOnlyAccess | Read-only permissions for SMN.                                                                                  | System-defined policy | None                                                                                          |
   |                    |                                                                                                                 |                       |                                                                                               |
   |                    | Users granted these permissions can only view SMN data.                                                         |                       |                                                                                               |
   +--------------------+-----------------------------------------------------------------------------------------------------------------+-----------------------+-----------------------------------------------------------------------------------------------+

:ref:`Table 2 <smn_ug_0034_1__table13641113421711>` lists the common operations supported by each SMN system policy or role. Select the policies or roles as needed.

.. _smn_ug_0034_1__table13641113421711:

.. table:: **Table 2** Common operations supported by each system-defined policy or role of SMN

   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Operation                            | Fine-Grained Action | SMN Administrator | SMN FullAccess | SMN ReadOnlyAccess | Dependency        |
   +======================================+=====================+===================+================+====================+===================+
   | Creating a topic                     | smn:topic:create    | Y                 | Y              | x                  | None              |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Updating a topic                     | smn:topic:update    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Deleting a topic                     | smn:topic:delete    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Querying topics                      | smn:topic:list      | Y                 | Y              | Y                  | None              |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Adding a subscription to a topic     | smn:topic:update    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Configuring topic policies           | smn:topic:update    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Publishing a message                 | smn:topic:publish   | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Adding a subscription                | smn:topic:update    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Requesting subscription confirmation | smn:topic:update    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Deleting a subscription              | smn:topic:update    | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Querying subscriptions               | smn:topic:list      | Y                 | Y              | Y                  | None              |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Creating a message template          | smn:template:create | Y                 | Y              | x                  | None              |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Modifying a message template         | smn:template:update | Y                 | Y              | x                  | smn:template:list |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Deleting a message template          | smn:template:delete | Y                 | Y              | x                  | smn:template:list |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Querying a message template          | smn:template:list   | Y                 | Y              | Y                  | None              |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Adding a tag                         | smn:tag:create      | Y                 | Y              | x                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Updating a tag                       | smn:tag:update      | Y                 | Y              | x                  | -  smn:topic:list |
   |                                      |                     |                   |                |                    | -  smn:tag:list   |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Deleting a tag                       | smn:tag:delete      | Y                 | Y              | x                  | -  smn:topic:list |
   |                                      |                     |                   |                |                    | -  smn:tag:list   |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
   | Querying tags                        | smn:tag:list        | Y                 | Y              | Y                  | smn:topic:list    |
   +--------------------------------------+---------------------+-------------------+----------------+--------------------+-------------------+
