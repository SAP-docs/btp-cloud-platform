<!-- loio5a31ca1032334a52bc084816567f16ec -->

# Configuring Single Sign-On Using Identity Authentication

To ensure the required security for your landscape you need to perform a few configuration tasks on all the sides - SAP BTP, Identity Authentication and SAP Cloud for Customer.



<a name="loio5a31ca1032334a52bc084816567f16ec__context_hlb_fzw_k2b"/>

## Context

The following procedure describes how to configure Identity Authentication and SAP Cloud for Customer to use the authentication and Single Sign-On capabilities based on the industry standard SAML 2.0. You can also find information about how to configure the trust between Identity Authentication and the subaccount in the SAP BTP, Cloud Foundry environment, in case it is not configured by default.



<a name="loio5a31ca1032334a52bc084816567f16ec__steps_ilb_fzw_k2b"/>

## Procedure

1.  Configure the trust settings between Identity Authentication and your SAP Cloud for Customer system. For more information, see [Setting Up Trust Between Identity Authentication and SAP Cloud for Customer](Setting_Up_Trust_Between_Identity_Authentication_and_SAP_Cloud_for_Customer_2903a3c.md).

    > ### Note:  
    > If you already have a SAP Cloud for Customer system with existing users, you need to define these users in the Identity Authentication service as well. To do that, export as a CSV file the users of your company employees from your SAP Cloud for Customer system and import it into Identity Authentication.

2.  Configure the SAP BTP trust settings and add the tenant of Identity Authentication available for your company as a SAML identity provider. For more information, see [Setting Up Trust Between Identity Authentication and SAP BTP](Setting_Up_Trust_Between_Identity_Authentication_and_SAP_BTP_9dba751.md).


-   **[Setting Up Trust Between Identity Authentication and SAP Cloud for Customer](Setting_Up_Trust_Between_Identity_Authentication_and_SAP_Cloud_for_Customer_2903a3c.md "To use Identity
                                Authentication
		as a common identity provider between SAP BTP, Cloud Foundry
		environment and SAP Cloud for
                            Customer, first you
		need to configure it for the SAP Cloud for
                            Customer
		system.")**  
To use Identity Authentication as a common identity provider between SAP BTP, Cloud Foundry environment and SAP Cloud for Customer, first you need to configure it for the SAP Cloud for Customer system.
-   **[Uploading Users to Identity Authentication](Uploading_Users_to_Identity_Authentication_c6d983a.md "When you configure the Identity
                                Authentication service as the
		SAML identity provider for your SAP Cloud for
                            Customer system, you
		have to make sure that all users from SAP Cloud for
                            Customer will have an
		identity record in the Identity
                                Authentication service. For this
		purpose, you have to export the user details in a CSV file format and then use this CSV file
		to import these users into the Identity
                                Authentication tenant of your
		company that will be used as the identity provider.")**  
When you configure the Identity Authentication service as the SAML identity provider for your SAP Cloud for Customer system, you have to make sure that all users from SAP Cloud for Customer will have an identity record in the Identity Authentication service. For this purpose, you have to export the user details in a CSV file format and then use this CSV file to import these users into the Identity Authentication tenant of your company that will be used as the identity provider.
-   **[Setting Up Trust Between Identity Authentication and SAP BTP](Setting_Up_Trust_Between_Identity_Authentication_and_SAP_BTP_9dba751.md "Use this procedure to configure the SAP BTP, Cloud Foundry
		environment trust settings and to add the tenant of Identity
                                Authentication registered for
		your current SAP user as an identity provider.")**  
Use this procedure to configure the SAP BTP, Cloud Foundry environment trust settings and to add the tenant of Identity Authentication registered for your current SAP user as an identity provider.

