<!-- loio0bef9822f5cc40e2b48303e51bec6b94 -->

# Log On with a Custom Identity Provider to the SAP BTP Cockpit

All users can log on to the SAP BTP cockpit with a custom identity provider.



<a name="loio0bef9822f5cc40e2b48303e51bec6b94__prereq_b1y_q3f_fvb"/>

## Prerequisites

-   Your user has administration or viewer rights in this subaccount or global account. For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).

-   You have established trust with a custom identity provider for platform users.

    For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md).




<a name="loio0bef9822f5cc40e2b48303e51bec6b94__context_bpv_4cf_fvb"/>

## Context

Use the *Open* link in the *SAP BTP Cockpit* column. It contains a URL for the user to log on with the custom identity provider.

> ### Example:  
> *https://emea.cockpit.btp.cloud.sap/cockpit/?idp=mytenant.accounts.ondemand.com*



<a name="loio0bef9822f5cc40e2b48303e51bec6b94__steps_cyc_rcf_fvb"/>

## Procedure

1.  Go to your global account or subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration* in the SAP BTP cockpit.

2.  Use the *Open* link in the SAP BTP*Cockpit* column.

    -   To enable other platform users to log on with a custom identity provider, send the link to these users.

    -   To work with your user accounts from multiple identity providers at the same time, open the link in a private or incognito browser window or tab.

        > ### Note:  
        > A browser that isn't in private or incognito mode has one single session with the cockpit. If you have an existing cockpit session with one identity provider and log on with another one, the existing session closes and creates a new session. For this reason, you can't have parallel sessions with different identity providers.


3.  Log on using the custom identity provider.


