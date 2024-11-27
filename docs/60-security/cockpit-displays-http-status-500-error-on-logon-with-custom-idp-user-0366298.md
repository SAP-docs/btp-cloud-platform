<!-- loio0366298c45a748599c5dc59088cffc69 -->

# Cockpit Displays HTTP Status 500 Error on Logon with Custom IdP User



## Symptom



## Reason and Prerequisites

After successfully logging on with a custom identity provider \(IdP\) user, the cockpit displays an error page: *HTTP Status 500 – Internal Server Error*.

The following are the known reasons for this error:

-   The mail claim in the OpenID Connect \(OIDC\) token from the Identity Authentication \(IAS\) tenant, is empty. This could happen in the following cases.
    -   The corporate identity provider \(for example, MS Azure AD\) is connected to the IAS and the user in the corporate IdP does not have an email address assigned.
    -   The [Identity Authentication user store](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c029bbbaefbf4350af15115396ba14e2.html#use-identity-authentication-user-store) is enabled, and the corporate identity provider is configured to send the email address of its user in another SAML attribute or OIDC claim than what is defined in the default attributes of the application in the Identity Authentication tenant.
    -   The Identity Authentication user store is disabled. This requires the corporate identity provider to send the user’s email address in a SAML attribute or OIDC claim mail.

-   The *mail*, *first\_name*, or *last\_name* claim in the OIDC token from IAS contains multiple values. This could happen in the following cases.
    -   The IAS tenant or application is configured to use a corporate IdP with identity federation enabled and the user also exists in the IAS user store, or the corporate IdP sends multiple values in the first place.
    -   In the case of the *mail* claim, the corporate IdPs OIDC token or SAML assertion does not send the email address in all lowercase. IAS always converts the email address to lowercase for local users.

-   The issuer in the connected IAS tenant was changed after the trust to that tenant was established.



## Solution



### Configure the corporate identity provider

As typically, either some attribute is missing or has multiple values instead of a single one, configure the corporate identity provider to correctly send the mail claim or required attributes.

-   If a platform user has problems when logging on with the a custom identity provider, refer to the [IAS Troubleshooting Logs \(OIDC\)](https://help.sap.com/docs/identity-authentication/identity-authentication/logging-openid-connect-tokens) for that affected user.
-   In particular, check if there is exactly one value \(and the correct value\) for the [specified attributes](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/40c2e54a5eb140baa46ed5bb15de4d3b.html?version=Cloud).



### Check the issuer in the IAS

The issuer in the IAS must not be changed after the trust has been established. This is also documented as a restriction [here](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/6f0a623807b541a0aef41f3d65c7a0fa.html?version=Cloud).

