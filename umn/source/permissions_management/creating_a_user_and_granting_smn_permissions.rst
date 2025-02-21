:original_name: smn_ug_0037.html

.. _smn_ug_0037:

Creating a User and Granting SMN Permissions
============================================

Use `IAM <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html>`__ to implement fine-grained permissions control over your SMN resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing SMN resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or cloud service to perform efficient O&M on your SMN resources.

If your account does not require individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <smn_ug_0037__en-us_topic_0173533526_en-us_topic_0173481716_en-us_topic_0172268189_fig12481104618719>`).

Prerequisites
-------------

Learn about the system permissions (see :ref:`Permissions <smn_ug_0034>`) supported by SMN and choose policies or roles according to your requirements. For system permissions of other cloud services, see `Permissions <https://docs.otc.t-systems.com/identity-access-management/permissions/permissions.html>`__.

Process Flow
------------

The following describes how to grant the **SMN ReadOnlyAccess** permissions.

.. _smn_ug_0037__en-us_topic_0173533526_en-us_topic_0173481716_en-us_topic_0172268189_fig12481104618719:

.. figure:: /_static/images/en-us_image_0000001569113488.png
   :alt: **Figure 1** Process for granting the **SMN ReadOnlyAccess** permissions

   **Figure 1** Process for granting the **SMN ReadOnlyAccess** permissions

#. .. _smn_ug_0037__en-us_topic_0173533526_en-us_topic_0173481716_en-us_topic_0172268189_li10269636890:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__

   Create a user group on the IAM console and assign the **SMN ReadOnlyAccess** permissions to the group.

#. `Create a user and add it to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <smn_ug_0037__en-us_topic_0173533526_en-us_topic_0173481716_en-us_topic_0172268189_li10269636890>`.

#. `Log in as the created user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify the **SMN ReadOnlyAccess** permissions.

   Log in to the SMN console by using the created user and verify that the user only has the **SMN ReadOnlyAccess** permissions.

   -  Choose **Service List** > **Simple Message Notification**. On the SMN **Topics** page, click **Create Topic** in the upper right corner. If the topic cannot be created, the **SMN ReadOnlyAccess** policy has already taken effect.
   -  Choose any other service on the **Service List** page. If a message appears indicating that you have insufficient permissions to access the service, the **SMN ReadOnlyAccess** policy has already taken effect.
   -  Choose **Service List** > **Simple Message Notification**. On the **Topics** page, if you can view existing topics, the **SMN ReadOnlyAccess** policy has already taken effect.
