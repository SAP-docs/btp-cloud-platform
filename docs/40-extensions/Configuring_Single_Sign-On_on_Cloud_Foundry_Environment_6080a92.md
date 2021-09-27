<!-- loio6080a929b4bc4ad482a8998ed6a92a2f -->

# Configuring Single Sign-On on Cloud Foundry Environment

You can configure the cloud platform extension integration with SAP Cloud for Customer to enable the use of applications running on top of the platform from SAP Cloud for Customer.



<a name="loio6080a929b4bc4ad482a8998ed6a92a2f__section_qfz_n5d_x1b"/>

## Using SAP BTP

The SAP BTP service provides authentication, Single Sign-On, and on-premise integration. The SAP BTP service is closely integrated with SAP BTP, and it is offered as part of the platform.

To ensure the required security for accessing the extension applications, you need to configure the Single Sign-On between the extension subaccount in SAP BTP and the SAP Cloud for Customer tenant using a SAML identity provider, for example SAP BTP. The Single Sign-On requires both solutions to be configured as trusted SAML service providers for the SAP BTP service and on the other side the SAP BTP service to be configured as trusted identity provider for the two solutions.

In this scenario, the authentication to SAP Cloud for Customer extension applications is restricted to the authorized users. The identity of a user is verified by the identity provider, as specified by SAML 2.0. The identity provider, \(SAP BTP\), stores a list of all users that are allowed to access the service provider \(SAP Cloud for Customer\) along with their credentials. The integration between the SAP Cloud for Customer and the SAP BTP is based on trust configuration. When a user attempts to access SAP Cloud for Customer for the first time, the system redirects the user to the identity provider for identification. From then on, the user session is kept active, and the user is no longer prompted for credentials when he or she, for example, tries to use the extension application. This is called Single Sign-On \(SSO\).



<a name="loio6080a929b4bc4ad482a8998ed6a92a2f__section_bpd_r5d_x1b"/>

## Using Third-Party Identity Provider

You can use a third-party identity provider \(which means a different from SAP BTP\) as well to ensure the required security for your landscape. In this case you also need to perform a few configuration tasks on all the sides - SAP BTP, SAP Cloud for Customer, and the identity provider that you are using.

-   **[Configuring Single Sign-On Using Identity Authentication](Configuring_Single_Sign-On_Using_Identity_Authentication_5a31ca1.md "To ensure the required security for your landscape you need to perform a few
		configuration tasks on all the sides - SAP BTP, Identity
                                Authentication and SAP Cloud for
                            Customer.")**  
To ensure the required security for your landscape you need to perform a few configuration tasks on all the sides - SAP BTP, Identity Authentication and SAP Cloud for Customer.
-   **[Configuring Single Sign-On Using Third-Party Identity Provider](Configuring_Single_Sign-On_Using_Third-Party_Identity_Provider_755fb0d.md "To ensure the required security for your landscape you need to perform a few
		configuration tasks on all the sides - SAP BTP, SAP Cloud for
                            Customer, and the
		identity provider that you are using (if this provider is different from Identity
                                Authentication, for which there
		is a dedicated section).")**  
To ensure the required security for your landscape you need to perform a few configuration tasks on all the sides - SAP BTP, SAP Cloud for Customer, and the identity provider that you are using \(if this provider is different from Identity Authentication, for which there is a dedicated section\).

**Related Information**  


[Configuring Single Sign-On Using Identity Authentication](Configuring_Single_Sign-On_Using_Identity_Authentication_5a31ca1.md "To ensure the required security for your landscape you need to perform a few configuration tasks on all the sides - SAP BTP, Identity Authentication and SAP Cloud for Customer.")

[Configuring Single Sign-On Using Third-Party Identity Provider](Configuring_Single_Sign-On_Using_Third-Party_Identity_Provider_755fb0d.md "To ensure the required security for your landscape you need to perform a few configuration tasks on all the sides - SAP BTP, SAP Cloud for Customer, and the identity provider that you are using (if this provider is different from Identity Authentication, for which there is a dedicated section).")

