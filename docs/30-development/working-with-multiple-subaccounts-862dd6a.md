<!-- loio862dd6abbcb349698c430d0167fa65c5 -->

# Working with Multiple Subaccounts

With the SAP BTP Operator module, you can create configurations for several subaccounts in a single Kyma cluster.



## Context

By default, a Kyma cluster is associated with one subaccount. Consequently, any service instance created within any namespace is provisioned in the associated subaccount. See [Preconfigured Credentials and Access](preconfigured-credentials-and-access-ab106d7.md). However, with SAP BTP Operator, you can create configurations in a single Kyma cluster that are applied to several subaccounts.

To apply the multitenancy feature, choose the method that suits your needs and application architecture:

-   [Namespace-level mapping](namespace-level-mapping-63ad410.md): Connect namespaces to separate subaccounts by configuring dedicated credentials for each namespace.

-   [Instance-level mapping](instance-level-mapping-d9e9c7f.md): Define a specific subaccount for each service instance, regardless of the namespace context.


Regardless of the method, you must create Secrets managed in the `kyma-system` namespace.



### Secrets Precedence

SAP BTP Operator searches for the credentials in the following order:

1.  Explicit Secret defined in a service instance
2.  Managed namespace Secret assigned for a given namespace
3.  Managed namespace default Secret

![](images/Secrets_Precedence_3d4e301.svg)



<a name="loio862dd6abbcb349698c430d0167fa65c5__steps-unordered_qnl_fkg_xcc"/>

## Procedure

-   To connect a namespace to a specific subaccount, see [Namespace-Level Mapping](namespace-level-mapping-63ad410.md).

-   To deploy service instances belonging to different subaccounts within the same namespace, see [Instance-Level Mapping](instance-level-mapping-d9e9c7f.md).


