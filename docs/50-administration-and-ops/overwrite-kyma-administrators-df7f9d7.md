<!-- loiodf7f9d7dedf84f1a8f2fda4e86ad4950 -->

# Overwrite Kyma Administrators

In some cases, you may need to overwrite usernames of the current administrators, for example, if they forget their password or leave the organization and nobody can access your Kyma runtime.



<a name="loiodf7f9d7dedf84f1a8f2fda4e86ad4950__prereq_fv1_t2l_nrb"/>

## Prerequisites

-   Your cluster is running Kyma version 2.0 or higher.

-   You are the subaccount administrator.




<a name="loiodf7f9d7dedf84f1a8f2fda4e86ad4950__context_znd_tld_4rb"/>

## Context

To overwrite the names for the **cluster-admin** role, update the Kyma instance and provide new value for the **administrators** field.

> ### Caution:  
> This procedure overwrites current administrators and shouldn't be used to add new ones. Treat it as an emergency self-service procedure in case of lost access. To provide access to new users, the **cluster-admin** should create a RoleBinding and/or a ClusterRoleBinding in the runtime as described in [Authorization in Kyma](https://kyma-project.io/docs/kyma/latest/04-operation-guides/security/sec-02-authorization-in-kyma#role-binding).



<a name="loiodf7f9d7dedf84f1a8f2fda4e86ad4950__steps_vbl_cxh_3rb"/>

## Procedure

1.  In the SAP BTP cockpit, go to your Kyma instance and select *Update*.

2.  Provide a new set of administrators' usernames as an array of strings.

3.  Click *Update*.




<a name="loiodf7f9d7dedf84f1a8f2fda4e86ad4950__result_qzy_nsz_1pb"/>

## Results

Your Kyma instance is updated with the new administrators' usernames.

