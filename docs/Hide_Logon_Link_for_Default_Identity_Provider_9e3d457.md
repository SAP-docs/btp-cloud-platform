<!-- loio9e3d4578e6cb4ad09a819e78e6adf309 -->

# Hide Logon Link for Default Identity Provider

You use one or multiple custom identity providers for business users as well as the default identity provider primarily for platform users. To provide a good logon experience for your business users, you want to hide the default identity provider, which remains active.



<a name="loio9e3d4578e6cb4ad09a819e78e6adf309__prereq_ik3_rl3_qjb"/>

## Prerequisites

-   You have configured a custom trust configuration for a custom identity provider, for example Identity Authentication, and set it to active.

-   You've checked the *Available for User Logon* checkbox in your custom trust configuration.

-   The default trust configuration \(`SAP ID service`\) is active.




## Context

To hide the default identity provider at logon time, proceed as follows:



## Procedure

1.  Go to your subaccount\(see [Navigate to Orgs and Spaces](Navigate_to_Orgs_and_Spaces_5bf8735.md)\) and choose *Security* \> *Trust Configuration* in the SAP BTP cockpit.

    You see the list of trust configurations: the default trust configuration and the custom trust configuration\(s\).

2.  Choose     \(Edit\) for the default trust configuration. It has the status *Default*.

3.  To hide the default trust configuration \(`SAP ID service`\) for logon, uncheck the *Available for User Logon* checkbox.

4.  Save your changes.

    The default trust configuration is now hidden but remains active.


