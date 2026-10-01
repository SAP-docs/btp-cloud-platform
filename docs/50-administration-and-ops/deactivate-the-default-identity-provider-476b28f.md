<!-- loio476b28f88d354fe9bf5f82e26f1c04bf -->

# Deactivate the Default Identity Provider

You can deactivate the default identity provider for an individual global account and subaccount.



<a name="loio476b28f88d354fe9bf5f82e26f1c04bf__prereq_deactivate_idp"/>

## Prerequisites

The prerequisites differ depending on the account type. Make sure you fulfill all conditions for your account type before proceeding.


<table>
<tr>
<th valign="top">

Account Type

</th>
<th valign="top">

Prerequisites

</th>
</tr>
<tr>
<td valign="top">

Global account

</td>
<td valign="top">

-   The global account administrator must have signed in using a custom platform trust configuration, not the default trust configuration.




</td>
</tr>
<tr>
<td valign="top">

Subaccount

</td>
<td valign="top">

-   The subaccount administrator must have signed in using a custom platform trust configuration, not the default trust configuration.

-   At least one custom trust configuration for application users is available in the subaccount.

-   > ### Note:  
    > To deactivate the default trust configuration, you can also use the following command of the SAP BTP command line interface \(btp CLI\).
    > 
    > `btp [OPTIONS] update security/trust ORIGIN [--subaccount [ID]] [--status [STATUS]]`
    > 
    > > ### Example:  
    > > `btp update security/trust sap.default --subaccount 195a6e-c379-5041-87b2-2baa7e7fdea3 --status inactive`
    > 
    > For more information, see [Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md).




</td>
</tr>
</table>



## Context

To deactivate the default identity provider for a global account and subaccount, take the following steps.



## Procedure

1.  Go to your global account or subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration* in the SAP BTP cockpit.

    The list of trust configurations appears showing the default trust configuration and the custom trust configurations.

2.  Choose the default identity provider.

3.  Choose *Edit* in the details screen.

4.  To deactivate the default identity provider, go to *Status*, and choose *Inactive*.

5.  Save your changes.


