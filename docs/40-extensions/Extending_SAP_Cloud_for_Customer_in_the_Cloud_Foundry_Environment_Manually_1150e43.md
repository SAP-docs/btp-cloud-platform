<!-- loio1150e4395ba6487bad2a7164db7ea417 -->

# Extending SAP Cloud for Customer in the Cloud Foundry Environment Manually

This section guides you through the configuration tasks that you need to perform to enable the SAP BTP, Cloud Foundry environment for developing extension applications for your SAP Cloud for Customer system.



<a name="loio1150e4395ba6487bad2a7164db7ea417__section_c2w_qbf_l2b"/>

## Process Flow

You have to configure the cloud platform extension integration with SAP Cloud for Customer to enable the use of applications running on top of the platform from SAP Cloud for Customer.



### 1. Authentication and Principal Propagation

A single sign-on configuration between SAP Cloud for Customer and the cloud platform and the principal propagation enablement ensure the secure and consistent access for the extension solutions. If your solution requires system-to-system data access, with no user propagation, you can implement it using a user with Basic authentication and no principal propagation.

> ### Tip:  
> We recommend that you use SSO and OData access with principal propagation, to ensure that the data is accessed on behalf of the proper authorized user.

 **Implementation with SSO and principal propagation** 

When your scenario requires SSO and principal propagation, the SAP Cloud for Customer system and the subaccount in SAP BTPSAP BTP \(where the extension application is deployed or subscribed\) have to trust each other and use one and the same identity provider. For more information, see [Configuring Single Sign-On on Cloud Foundry Environment](Configuring_Single_Sign-On_on_Cloud_Foundry_Environment_6080a92.md).

**Implementation without SSO and principal propagation**

If your scenario does not require SSO, principal propagation, or UI integration, you use a dedicated user and create an HTTP destination with Basic Authentication to configure the connectivity. For more information, see [Create and Configure the HTTP Destination](Create_and_Configure_the_HTTP_Destination_21e50d8.md).



### 2. Connectivity Between SAP BTP and SAP Cloud for Customer

When your extension application needs to do read and write operations from/to the SAP Cloud for Customer system, you have to configure the connectivity to enable the use of SAP Cloud for Customer OData APIs. You need such connectivity to be established also when you want to embed the UIs of the extension solution into the SAP Cloud for Customer user interface.

The connectivity configuration steps are required on both systems and can be implemented with the following options depending on the security mechanisms for protecting the connectivity:

**Using OAuth**

> ### Note:  

-   On the SAP Cloud for Customer side:

    -   [Configure OAuth Identity Provider in SAP Cloud for Customer](Configure_OAuth_Identity_Provider_in_SAP_Cloud_for_Customer_40d20a2.md)

    -   [Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md)



-   On the SAP BTP side:

    -   Create an HTTP destination with OAuthSAMLBearerAssertion for authentication method. For more details, see [Create and Configure the HTTP Destination](Create_and_Configure_the_HTTP_Destination_21e50d8.md).



**Using Basic Authentication**

-   On SAP Cloud for Customer side:

    -   \(If not available\) Create a technical user with permissions to access the required SAP Cloud for Customer OData APIs and use it for the HTTP destination configuration when you choose Basic authentication for protecting the connectivity.



-   On the SAP BTP side:

    -   Create an HTTP destination with Basic authentication using the credentials of a technical user in the SAP Cloud for Customer system. For more details, see [Create and Configure the HTTP Destination](Create_and_Configure_the_HTTP_Destination_21e50d8.md).





### 3. User Interface Integration

The extension capabilities of the cloud platform allow developers to embed the user interface of the new solution in the SAP Cloud for Customer screens and this way to offer seamless end-user experience.

The UI integration is via the HTML mashups of the SAP Cloud for Customer solution. For more details how to create an HTML mashup for your new extension solution and how to make it visible in the SAP Cloud for Customer screens, see [Add Mashups on Screens](https://help.sap.com/viewer/5d3ae4aa1f174b2cb6ec625c93ef8884/CLOUD/en-US/98b729dd6d8e1014821a8a1b078819be.html).

