<!-- loio2204416a491f4068ba36066ca1aa9ca0 -->

# Deploy the Multitenant Application to the Provider Subaccount

After you have developed your multitenant application and authorizations, you need to deploy the application in a Cloud Foundry space in the provider's subaccount.



## Context

To make the application available to subaccounts in multiple regions, you need to deploy the application to a provider subaccount in each of the regions.



## Procedure

1.  Create a subaccount in the Cloud Foundry environment in the global account of the application provider. This subaccount will host the multitenant application for the provider tenant.

    For general instructions, see [Create a Subaccount](../50-administration-and-ops/create-a-subaccount-05280a1.md).

2.  In the subaccount, create a space in a Cloud Foundry organization.

    For general instructions, see [Create Spaces](../50-administration-and-ops/create-spaces-2f6ed22.md).

3.  Assign the appropriate quota for the application runtime memory to the provider's subaccount.

    For general instructions, see [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/configure-entitlements-and-quotas-for-subaccounts-5ba357b.md).

4.  Deploy the application to the Cloud Foundry space and start it by executing the `push` command in the command line interface \(cf CLI\).

    For more information, see [Deploy Business Applications in the Cloud Foundry Environment](deploy-business-applications-in-the-cloud-foundry-environment-4946ea5.md).


