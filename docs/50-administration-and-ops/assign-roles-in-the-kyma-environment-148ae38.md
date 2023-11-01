<!-- loio148ae38b7d6f4e61bbb696bbfb3996b2 -->

# Assign Roles in the Kyma Environment

Kyma uses roles to manage access within the cluster, which give the assigned users the permissions suitable for their purposes.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__prereq_ehs_rvh_nsb"/>

## Prerequisites

The `cluster-admin` role is assigned to your account.

> ### Note:  
> After creating a Kyma cluster, you become an admin of this instance and the `cluster-admin` role is assigned to you by default. As the `cluster-admin`, you can assign roles to other users. Only the administrator who created the current subaccount can use the SAP BTP cockpit to assign the `cluster-admin` role to other members.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__context_lrm_lv2_hsb"/>

## Context

You can assign roles to a group of users only if you use a custom identity provider. Assigning roles in Kyma is based on the Kubernetes [role-based access control](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) \(RBAC\). Once you become the admin, your user name is read from the SAP BTP \(RBAC\) concept and is passed to the Kyma provisioner to be bound to the `cluster-admin` role in Kyma.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__steps_bvs_hv2_hsb"/>

## Procedure

1.  Log in to Kyma Dashboard. The URL is in the *Overview* section of your subaccount.

2.  In Kyma Dashboard, select or create the Namespace in which you want to assign roles.

3.  To create a role binding, go to *Configuration* \> *Role Bindings* \> *\+ Create Role Binding*. Fill in the required fields:

    1.  As *Name*, insert the name of your binding.

    2.  As *Role Type*, choose *ClusterRole*.

    3.  As *Role*, choose the required role.

    4.  As *Kind*, choose *User*.

    5.  As *User name*, insert the user email address.


4.  Select *Create*.




<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__result_bx4_2v2_hsb"/>

## Results

The users have the required permissions within the specified Namespace. If the users don't have additional Cluster Role Binding to list the Namespaces, they can still access the Kyma Dashboard overview but must enter the required Namespace name manually.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__postreq_rb5_ntn_fvb"/>

## Next Steps

If the permissions of the default role aren't sufficient, clone the role and add the missing resources.

**Related Information**  


[Authorization in Kyma](https://kyma-project.io/#/04-operation-guides/security/sec-02-authorization-in-kyma)

