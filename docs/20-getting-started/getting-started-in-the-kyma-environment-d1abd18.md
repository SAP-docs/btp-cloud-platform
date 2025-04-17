<!-- loiod1abd18556f24fb091d081b2e3454b8b -->

# Getting Started in the Kyma Environment

As an administrator, you must perform several steps to set up a fully operational Kyma environment to which you can connect the chosen SAP solutions.



<a name="loiod1abd18556f24fb091d081b2e3454b8b__prereq_hdj_k23_nrb"/>

## Prerequisites

-   To perform administrative and development tasks, you need a global account and one or several subaccounts for which you can provision the Kyma environment. For details, see [Creating a Kyma Instance](../50-administration-and-ops/creating-a-kyma-instance-09dd313.md).

-   The subaccount must have the following entitlements assigned:

    -   Kyma environment \(added by the subaccount manager\)

    -   Service Manager \(added by default\). However, if you removed the entitlement, you must add it again in your subaccount


    For details, see [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/configure-entitlements-and-quotas-for-subaccounts-5ba357b.md).




<a name="loiod1abd18556f24fb091d081b2e3454b8b__steps_xs3_l23_nrb"/>

## Procedure

1.  Set up a Kubernetes cluster with the project "Kyma" to connect and extend SAP systems: [Creating a Kyma Instance](../50-administration-and-ops/creating-a-kyma-instance-09dd313.md)

2.  Add the modules you'd like to use: [Kyma Modules](../10-concepts/kyma-modules-0dda141.md).

3.  Assign the roles to users to allow the administrators to manage Kyma and the developers to create Functions: [Assign Roles in the Kyma Environment](../60-security/assign-roles-in-the-kyma-environment-148ae38.md)

    > ### Caution:  
    > Assign the roles before the users start using the Kyma dashboard. Not granting the roles results in an error.

4.  Use the Kyma environment to integrate external systems: [Register an SAP Customer Experience System](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/1582d723f3814d30beba5fc0daa0bb0d.html)

    You have the following options:

    -   Integrate a CX system and the Kyma environment, so that the Functions you develop can use the system's API and receive business events.

    -   Integrate an SAP S/4 HANA Cloud system to use the services it provides to extend your applications.


    After you've integrated externals systems, the developers can start working on their Functions.

5.  Extend SAP S/4HANA Cloud by developing event-driven extensions and applications: [Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/40b9e6c3cc43498b92472da13e88c7bf.html)

6.  Group several solutions into one formation to meet the requirements of your business scenario: [Including SAP Systems in a Formation](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/68b04fa73aa740cb96ed380a85a4761a.html)




<a name="loiod1abd18556f24fb091d081b2e3454b8b__result_h4y_5f3_nrb"/>

## Results

You have set up the Kyma environment and connected it as required.



<a name="loiod1abd18556f24fb091d081b2e3454b8b__postreq_jht_xf3_nrb"/>

## Next Steps

After the administrator has set up the Kyma environment, the developers can access it through the Kyma dashboard. After logging on, developers can start creating extensions for the SAP systems either from the Kyma dashboard or from the terminal after downloading the kubeconfig file with the cluster configuration. For details, see [Development in the Kyma Environment](../30-development/development-in-the-kyma-environment-606ec61.md).

