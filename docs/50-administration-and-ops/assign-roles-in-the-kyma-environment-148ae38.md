<!-- loio148ae38b7d6f4e61bbb696bbfb3996b2 -->

# Assign Roles in the Kyma Environment

Kyma uses roles to manage access within the cluster. Every Kyma cluster comes with predefined roles, for example, for admins and developers, which give the assigned users the permissions suitable for their purposes.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__prereq_ehs_rvh_nsb"/>

## Prerequisites

The **cluster-admin** role is assigned to your account.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__context_lrm_lv2_hsb"/>

## Context

After creating a Kyma cluster, you become an admin of this instance and the **cluster-admin** role is assigned to you by default. As the **cluster-admin**, you can assign roles to other users. You can assign roles to a group of users only if you use a custom identity provider. Assigning roles in Kyma is based on the Kubernetes [role-based access control](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)Kyma comes with a set of predefined roles. To learn more, read the \(RBAC\) concept and can be done in the context of the entire cluster or a specific Namespace. [Authorization in Kyma](https://kyma-project.io/docs/kyma/latest/04-operation-guides/security/sec-02-authorization-in-kyma/) document. Once you become the admin, your user name is read from the SAP BTP \(RBAC\) concept and can be done session context and is passed to the Kyma provisioner to be bound to the **cluster-admin** role in Kyma.

To assign the **kyma-developer** role to a user in a Namespace, follow these steps:



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__steps_bvs_hv2_hsb"/>

## Procedure

1.  Log in to Kyma Dashboard. The URL is in the *Overview* section of your subaccount.

2.  In Kyma Dashboard, select or create the Namespace in which you want to assign roles.

3.  To create a role binding, go to *Configuration* \> *Role Bindings* \> *\+ Create Role Binding*. Fill in the required fields:

    1.  As *Name*, insert ***runtimeDeveloper***.

    2.  As *Role*, choose *kyma-developer*.

    3.  As *Kind*, choose *User*.

    4.  As *User name*, insert the user e-mail address.


4.  Select *Create*.




<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__result_bx4_2v2_hsb"/>

## Results

The users have the kyma-developer permissions within the specified Namespace. If the users do not have additional Cluster Role Binding to list the Namespaces, they can still access the Kyma Dashboard overview but must enter the required Namespace name manually. If the permissions of the kyma-developer role are not sufficient, the role can be cloned and missing resources can be added.

