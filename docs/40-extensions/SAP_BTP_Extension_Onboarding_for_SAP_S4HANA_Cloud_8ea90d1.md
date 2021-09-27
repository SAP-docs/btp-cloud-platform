<!-- loio8ea90d190daf46cca0d63e7d6150f714 -->

# SAP BTP Extension Onboarding for SAP S/4HANA Cloud

The SAP BTP, Cloud Foundry environment extension onboarding enables the integration between the cloud platform and SAP S/4HANA Cloud. This allows the SAP S/4HANA Cloud side-by-side extension applications to run on top of the cloud platform.

The Identity Authentication service provides authentication, single sign-on, and on-premise integration. The Identity Authentication service is closely integrated with SAP BTP, and it is offered as part of the platform.

The authentication to SAP S/4HANA Cloud applications is restricted to the authorized users. The identification of a user is verified by the identity provider, as specified by SAML 2.0. The Identity Authentication service stores a list of all users that are allowed to access the service provider \(SAP S/4HANA Cloud\) along with their credentials. The integration between the SAP S/4HANA Cloud and the Identity Authentication service is based on a trust configuration. When a user attempts to access SAP S/4HANA Cloud for the first time, the system redirects the user to the identity provider for identification. From then on, the user session is kept active, and the user is no longer prompted for credentials when trying to use the SAP S/4HANA Cloud application. This is called single sign-on \(SSO\).

To ensure the required security for accessing the applications, you need to configure the single sign-on between the SAP BTP subaccount and the SAP S/4HANA Cloud tenant using a SAML identity provider, for example Identity Authentication service. The single sign-on requires both solutions to be configured as trusted SAML service providers for the Identity Authentication service, and at the same time, the Identity Authentication service to be configured as trusted identity provider for the two solutions.

> ### Note:  
> You own an SAP S/4HANA Cloud tenant with an Identity Authentication tenant configured. You need to use the same Identity Authentication tenant for your subaccount in SAP BTP.

-   **[Configure Single Sign-On with the Identity Authentication Service](Configure_Single_Sign-On_with_the_Identity_Authentication_Service_8d3c376.md "To use the SAML 2.0 bearer assertion authentication for the communication flow between
		the extension application and SAP S/4HANA Cloud, you need to configure single-sign on
		(SSO).")**  
To use the SAML 2.0 bearer assertion authentication for the communication flow between the extension application and SAP S/4HANA Cloud, you need to configure single-sign on \(SSO\).

