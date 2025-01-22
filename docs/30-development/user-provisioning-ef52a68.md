<!-- loioef52a682060c4051a0645f4ecc5859d0 -->

# User Provisioning

User provisioning is the automated process of creating users, that are later granted permissions to access business services and applications, to allow system to system communication, or to perform troubleshooting.

> ### Note:  
> Please make sure that employee and business user data is maintained in accordance with the `login_attribute`system provisioning parameter \(see [Creating ABAP System](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-abap-system?version=Cloud)\) and the subject name identifier configured in the Identity Authentication application \(see [Configure the Subject Name Identifier Sent to the Application](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/1d020e3a3ba34c43a71fde70bfa6419a.html?version=Cloud)\): If `login_attribute = email` is used, the email address at employee level needs to be maintained for identity federation to work, if login\_attribute = user\_name is configured, the username on business user level needs to match the login name provided in the identity authentication user.



<a name="loioef52a682060c4051a0645f4ecc5859d0__section_bq1_xms_xsb"/>

## Creating SAP BTP ABAP environment Users

Each business user created in the ABAP environment system has a unique and stable employee ID. Employees are maintained in the SAP Fiori app *Maintain Employees*. See [Maintain Employees](../50-administration-and-ops/maintain-employees-e882b0f.md).

> ### Recommendation:  
> We recommend setting the employee ID by an HR system, which allows you to update master data in the *Maintain Employees* app, for example, when a business user has a new email address because of a name change, or if you want to edit the user information of the initial admin of an ABAP environment service instance.

The following provisioning methods to automate identity lifecycle processes for business users are available:

-   SAP Fiori app *Maintain Employees* with CSV file upload. See [Maintain Employees](../50-administration-and-ops/maintain-employees-e882b0f.md).
-   SOAP service using communication scenario Identity Management Integration `SAP_COM_0093`. See [Inbound Service: Business User](inbound-service-business-user-a631f4e.md) and [Inbound Service: Business User - Read](inbound-service-business-user-read-535e7af.md).
-   Identity Provisioning service using communication scenario SAP Cloud Identity Services - Identity Provisioning `SAP_COM_0193`. See [Identity Provisioning - SAP BTP ABAP Environment as a Target System](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/e763123cbba9418d99a43b72c9783c60.html).

> ### Recommendation:  
> To create new business users in the ABAP environment, we recommend using the Identity Provisioning service.
> 
> This requires setting up the Identity Authentication service as a source system for identity provisioning and managing employee information in the user store. The Identity Provisioning service can then read this information and map the Identity Authentication logon name to the ABAP environment employee ID. See [Identity Authentication as a Source System](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/e4e25f1fae094c2a89ad62159e1cd230.html) and [Tutorial: Provision Users into your SAP BTP ABAP Environment](https://developers.sap.com/tutorials/abap-environment-ips.html#9e4583da-62d2-4c05-8991-325d4c3a524).

To create **communication users**, see [How to Create Communication Users](../50-administration-and-ops/how-to-create-communication-users-0377ade.md).

SAP support users are owned and created by SAP. However, in the *Display Technical Users* SAP Fiori app, you can check when and why SAP support users accessed your customer system in the past 12 months. See [SAP Support User Request Log](../50-administration-and-ops/sap-support-user-request-log-934a027.md).



<a name="loioef52a682060c4051a0645f4ecc5859d0__section_fnk_3ns_xsb"/>

## Creating SAP BTP Users

To create **platform users** and **space members**, see [User and Member Management](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/cc1c676b43904066abb2a4838cbd0c37.html?version=Cloud) and [Creating New Space Members and Assigning Space Developer Roles to Them](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/967fc4e2b1314cf7afc7d7043b53e566.html?version=Cloud).

**Related Information**  


[What Is Identity Provisioning?](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/f2b2df8a273642a1bf801e99ecc4a043.html)

