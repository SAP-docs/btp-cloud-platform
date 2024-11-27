<!-- loio2b38193358d84270870d9f5017266058 -->

# User Base Doesn't Appear in Existing Neo Subaccounts



## Symptom

When trying to add new members, Neo member management doesn't have the custom identity provider configured in the global account, as the user base.



## Reason and Prerequisites

For subaccounts in the Neo environment, the identity provider will be offered in the value help only if a user in that identity provider has created at least one Neo subaccount in the corresponding global account and Neo region. For more information about this, see [here](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/c36898473d704e07a33268c9f9d29515.html?version=Cloud#next-steps).



## Solution



### Create at least one new Neo subaccount

A user from the configured custom identity provider needs to create at least one new Neo subaccount in the Neo region where the user base selection is missing.

