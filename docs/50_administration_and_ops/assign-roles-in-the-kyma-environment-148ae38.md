<!-- loio148ae38b7d6f4e61bbb696bbfb3996b2 -->

# Assign Roles in the Kyma Environment

Kyma uses roles and groups to manage access within the cluster. Every Kyma cluster comes with predefined roles for admins and developers, which give the assigned users the permissions suitable for their purposes.



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__prereq_mx3_tyv_pqb"/>

## Prerequisites

-   To assign the admin role \(**KymaRuntimeNamespaceAdmin**\), you must be subaccount admininistrator.

-   To assign the developer role \(**KymaRuntimeDeveloper**\), you must have the KymaRuntimeNamespaceAdmin role.




<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__context_y3l_ywh_3rb"/>

## Context

The roles predefined for the Kyma environment are:

-   **KymaRuntimeNamespaceAdmin**: Can access Kubernetes and Kyma resources and components with administrative rights, create their own Namespaces, and assign the KymaRuntimeDeveloper role to SAP BTP users. This role **does not** give access to [Kyma system Namespaces](https://github.com/kyma-project/kyma/blob/master/resources/permission-controller/values.yaml#L25) and grants only read access to [AddonsConfigurations](https://kyma-project.io/docs/master/components/helm-broker#custom-resource-addons-configuration) because administration of these resources is restricted to Kyma system admins.

-   **KymaRuntimeDeveloper**: Can list and edit Kubernetes and Kyma-specific resources scoped to specific Namespaces in order to build implementations with Kyma.


> ### Note:  
> To learn how to define role collections and assign them to users and user groups, see [Working with Role Collections](working-with-role-collections-393ea0b.md).



<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__steps_sql_ryv_pqb"/>

## Procedure

1.  Log in to the SAP BTP cockpit and choose the subaccount you want to assign roles to.

2.  Follow the instructions in [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).

    If you’ve already enabled the Kyma environment in your subaccount, you see the following predefined role collections:

    -   KymaRuntimeDeveloper role collection with the KymaRuntimeDeveloper role assigned

    -   KymaRuntimeNamespaceAdmin role collection with the KymaRuntimeNamespaceAdmin role assigned


    When you add the user you want to assign to the respective role, provide the user's e-mail address and choose *SAP ID Service* as the Identity Provider.

    > ### Note:  
    > -   For assigning the KymaRuntimeNamespaceAdmin role, you’re now finished: The selected users have the KymaRuntimeNamespaceAdmin rights and can access the Kyma Console.
    > 
    > -   For users who were assigned the KymaRuntimeDeveloper role, now a KymaRuntimeNamespaceAdmin must assign the role in the Kyma Console.

3.  To assign the KymaRuntimeDeveloper role, log in to the Kyma Console. The URL is in the *Overview* section of your subaccount.

4.  In the Kyma Console, select or create the Namespace you want to assign roles to.

5.  To create a binding to your role collection, go to *Configuration* \> *Permissions* \> *+ Create Binding*. Choose *User Group* and fill in the required fields:

    1.  As *Name*, insert *runtimeDeveloper*.

    2.  As *Role*, choose *kyma-developer*.


6.  Save your configuration.




<a name="loio148ae38b7d6f4e61bbb696bbfb3996b2__result_qgx_51w_pqb"/>

## Results

The users have the required authorizations as admin or developer, and can access the Kyma Console.

