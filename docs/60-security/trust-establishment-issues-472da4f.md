<!-- loio472da4ff90c340679ef85dd322764de6 -->

# Trust Establishment Issues



## Symptom

You could have trust establishment issues if you encounter one of the following symptoms:

-   In the BTP Cloud Cockpit:
    -   After clicking **Establish Trust**, an Identity Authentication \(IAS\) tenant is not displayed.
    -   Failure after the IAS tenant is selected and confirmed by clicking **Establish Trust**.
    -   **Establish Trust** button is not accessible \(displayed in the inactive state\).
    -   Trust deletion fails.


-   In the REST API:
    -   Usage of the [REST API](https://api.sap.com/api/TrustConfigurationAPI/resource) \(`/sap/rest/identity-providers`\) returns status code `400`, `401`, or `404`.
    -   Trust deletion fails.




## Reason and Prerequisites

To establish trust in an automated manner, the customer ID of the IAS tenant has to match the customer ID of the global account.

Consequently, the issues in trust establishment may be because of the following:

-   The customer ID maintained in the IAS tenant does not match what is in the global account.
-   Trust has already been established \(IdP trust with origin `sap.custom` exists.\).



## Solution



### Check that the IAS tenant is displayed

If an IAS tenant is not displayed, verify the following:

-   The customer ID maintained in the IAS tenant matches what is in the customer ID of the global account.
    -   IAS admin UI: *Applications & Resources \> Tenant Settings \> Customer ID*
    -   Global account: Verify the value in the control center.


In case you require a new IAS tenant, see the corresponding [documentation](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html?version=Cloud). For more information, see [this blog article](https://blogs.sap.com/2021/08/19/new-check-on-one-single-page-all-of-your-identity-authentication-and-identity-provisioning-tenants-and-administrators/).



### Check that the "Establish Trust" button is accessible

If the Establish Trust button is grayed out, there is probably already an Identity Provider \(IdP\) trust with origin, sap.custom. To change the trust, you can delete the existing configuration and create a new one. Note that the trust deletion in the Cloud Cockpit implies the deletion of all existing shadow users \(for this IdP\).

If the Establish Trust button is not visible at all, it could be an issue with the Identity Authentication service \(IAS\) registry or the certificates. This is usually a temporary issue and you should retry accessing it later.



### Check the usage of the REST API

Depending on the status code, verify the following points:

-   `400`: Check the section, *Specific IAS tenant is not shown*. Further, verify that the `/sap/rest/identity-providers/ias` REST API returns the used IAS tenant.
-   `401`: REST API requires a token of the *apiaccess* service plan from your subaccount.
-   `404`: For newly created IAS tenants, it can take up to 2 hours until the DNS entry is propagated to all the DNS caches. Until that is done, you can get an error when trying to call the new IAS tenant. In such a case, wait and retry after 2 hours.



### Check if trust has already been established

-   Verify that you are deleting a custom IdP \(the default IdP cannot be deleted\).
-   Ensure that if you use the identity broker \(or a SaaS application that uses it\), it does not contain any application references or other applications.

