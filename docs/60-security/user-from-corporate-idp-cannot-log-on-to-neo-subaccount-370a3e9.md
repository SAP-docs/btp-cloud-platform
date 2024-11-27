<!-- loio370a3e9e25f64093ab41d43f48cd19bf -->

# User from Corporate IdP Cannot Log on to Neo Subaccount



## Symptom

When a user with a corporate identity provider \(IdP\) logs on to the cockpit and tries to navigate to a Neo subaccount, the Identity Authentication \(IAS\) tenant shows the logon screen with the *E-Mail or User Name* and *Password* fields. However, with a properly connected and configured corporate IdP, the IAS logon screen should show only the *E-Mail or User Name* field.



## Reason and Prerequisites

For all the Neo datacenters where you have subaccounts, you might have to configure a separate SAML application \(for example, *SAP Cloud Platform hhw9g3jrxa*\) in the IAS tenant. This behavior is also documented [here](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/c36898473d704e07a33268c9f9d29515.html?version=Cloud#next-steps).

-   A custom IdP with a corporate identity provider \(e.g. MS Azure AD\) is configured in the global account.
-   The affected users from the corporate IdP can log on to the cockpit \(e.g. [https://cockpit.eu10.hana.ondemand.com/cockpit/?idp=ar9ibaxhm.accounts.ondemand.com](https://cockpit.eu10.hana.ondemand.com/cockpit/?idp=ar9ibaxhm.accounts.ondemand.com)\).
-   The affected users are configured as members of the Neo subaccount, with the correct user base.



## Solution

Find the correct SAML application in the configured IAS tenant and configure conditional authentication accordingly. Each Neo region where custom IdP is configured has a separate SAML application in IAS that needs to be configured.

