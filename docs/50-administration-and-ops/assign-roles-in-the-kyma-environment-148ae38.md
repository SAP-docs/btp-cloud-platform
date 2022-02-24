<!-- loio148ae38b7d6f4e61bbb696bbfb3996b2 -->

# Assign Roles in the Kyma Environment

Kyma uses roles to manage access within the cluster. Every Kyma cluster comes with predefined roles, for example, for admins and developers, which give the assigned users the permissions suitable for their purposes.

 <a name="task_pyf_bv2_hsb"/>

<!-- task\_pyf\_bv2\_hsb -->

## Assign Roles in Kyma 1.x



<a name="task_pyf_bv2_hsb__prereq_mx3_tyv_pqb"/>

## Prerequisites

-   To assign the admin role \(**KymaRuntimeNamespaceAdmin**\), you must be subaccount administrator.

-   To assign the developer role \(**KymaRuntimeDeveloper**\), you must have the KymaRuntimeNamespaceAdmin role.




<a name="task_pyf_bv2_hsb__context_alm_yx2_hsb"/>

## Context

The roles predefined for the Kyma environment are:

-   **KymaRuntimeNamespaceAdmin**: Can access Kubernetes and Kyma resources and components with administrative rights, create their own Namespaces, and assign the KymaRuntimeDeveloper role to SAP BTP users. This role **does not** give access to [Kyma system Namespaces](https://github.com/kyma-project/kyma/blob/release-1.25/resources/permission-controller/values.yaml) and grants only read access to [AddonsConfigurations](https://kyma-project-old.netlify.app/docs/components/helm-broker/#custom-resource-addons-configuration) because administration of these resources is restricted to Kyma system admins.

-   **KymaRuntimeDeveloper**: Can list and edit Kubernetes and Kyma-specific resources scoped to specific Namespaces in order to build implementations with Kyma.


> ### Note:  
> To learn how to define role collections and assign them to users and user groups, see [Working with Role Collections](working-with-role-collections-393ea0b.md).



<a name="task_pyf_bv2_hsb__steps_sql_ryv_pqb"/>

## Procedure

1.  Log in to the SAP BTP cockpit and choose the subaccount you want to assign roles to.

2.  Follow the instructions in [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).

    If you’ve already enabled the Kyma environment in your subaccount, you see the following predefined role collections:

    -   KymaRuntimeDeveloper role collection with the KymaRuntimeDeveloper role assigned

    -   KymaRuntimeNamespaceAdmin role collection with the KymaRuntimeNamespaceAdmin role assigned


    When you add the user you want to assign to the respective role, provide the user's e-mail address and choose *SAP ID Service* as the Identity Provider.

    > ### Note:  
    > -   For assigning the KymaRuntimeNamespaceAdmin role, you’re now finished: The selected users have the KymaRuntimeNamespaceAdmin rights and can access the Kyma Console/Dashboard.
    > 
    > -   For users who were assigned the KymaRuntimeDeveloper role, now a KymaRuntimeNamespaceAdmin must assign the role in the Kyma Console/Dashboard.

3.  To assign the KymaRuntimeDeveloper role, log in to the Kyma Console/Dashboard. The URL is in the *Overview* section of your subaccount.

4.  In the Kyma Console/Dashboard, select or create the Namespace you want to assign roles to.

5.  To create a binding to your role collection, go to *Configuration* \> *Permissions* \> *+ Create Binding*. Choose *User Group* and fill in the required fields:

    1.  As *Name*, insert *runtimeDeveloper*.

    2.  As *Role*, choose *kyma-developer*.


6.  Save your configuration.




<a name="task_pyf_bv2_hsb__result_qgx_51w_pqb"/>

## Results

The users have the required authorizations as admin or developer, and can access the Kyma Console/Dashboard.

 <a name="task_dg1_x52_hsb"/>

<!-- task\_dg1\_x52\_hsb -->

## Assign Roles in Kyma 2.x



<a name="task_dg1_x52_hsb__prereq_ehs_rvh_nsb"/>

## Prerequisites

The **cluster-admin** role is assigned to your account.



<a name="task_dg1_x52_hsb__context_lrm_lv2_hsb"/>

## Context

After creating a Kyma cluster, you become an admin of this instance and the **cluster-admin** role is assigned to you by default. As the **cluster-admin**, you can assign roles to other users. You can assign roles to a group of users only if you use a custom identity provider. Assigning roles in Kyma is based on the Kubernetes [role-based access control](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) \(RBAC\) concept and can be done in the context of the entire cluster or a specific Namespace. Kyma comes with a set of predefined roles. To learn more, read the [Authorization in Kyma](https://kyma-project.io/docs/kyma/latest/04-operation-guides/security/sec-02-authorization-in-kyma/) document. Once you become the admin, your user name is read from the SAP BTP session context and is passed to the Kyma provisioner to be bound to the **cluster-admin** role in Kyma.

To assign the **kyma-developer** role to a user in a Namespace, follow these steps:



<a name="task_dg1_x52_hsb__steps_bvs_hv2_hsb"/>

## Procedure

1.  Log in to Kyma Console/Dashboard. The URL is in the *Overview* section of your subaccount.

2.  In Kyma Console/Dashboard, select or create the Namespace in which you want to assign roles.

3.  To create a role binding, go to *Configuration* \> *Role Bindings* \> *+ Create Role Binding*. Fill in the required fields:

    1.  As *Name*, insert ***runtimeDeveloper***.

    2.  As *Role*, choose *kyma-developer*.

    3.  As *Kind*, choose *User*.

    4.  As *User Name*, insert the user e-mail address.


4.  Select *Create*.




<a name="task_dg1_x52_hsb__result_bx4_2v2_hsb"/>

## Results

The users have the required authorizations as developer, and can access Kyma Console/Dashboard.

