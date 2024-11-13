<!-- loio4bfe9c71cf10466a8674a6ef8953cb18 -->

# Configuration for Using the Resource Consumption APIs in the SAP Business Accelerator Hub

The **Resource Consumption** APIs of the SAP Usage Data Management service for SAP BTP are protected with OAuth 2.0 Client Credentials grant type and in some cases, also the Password grant type.



> ### Note:  
> OAuth 2.0 Password grant type is only mandatory for the `subaccountUsage` API.



<a name="loio4bfe9c71cf10466a8674a6ef8953cb18__section_im4_f4d_k3b"/>

## Prerequisites

-   To use the *Resource Consumption* APIs of the SAP Usage Data Management service

    -   You must have service access to the relevant **uas** service plan. For information about available service plans, see [SAP Usage Data Management Service - Service Plans](sap-usage-data-management-service-service-plans-c94c85e.md).
    -   When using **Password grant type** the user must be assigned one of the following role collections:


        <table>
        <tr>
        <th valign="top">

        API
        
        </th>
        <th valign="top">

        Role Collection Required
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `monthlyUsage`, `/monthlySubaccountsCost`, and `subaccountUsage`
        
        </td>
        <td valign="top">
        
        Global Account Administrator and Global Account Viewer
        
        </td>
        </tr>
        </table>
        
        For more information, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).



> ### Note:  
> To create a service instance in other environments using the Service Manager Control \(SMCTL\) CLI, SAP Service Manager APIs, or the SAP BTP cockpit, see [Consuming Services in Other Environments Using the SAP Service Manager Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).



<a name="loio4bfe9c71cf10466a8674a6ef8953cb18__section_xph_mcr_w3b"/>

## Procedure

1.  Create a service instance for the service plans that correspond to the APIs that you want to use.

    When you create the service instance, specify the following parameters:

    -   `PLAN:` The name of the service plan that you want to use. See [SAP Usage Data Management Service - Service Plans](sap-usage-data-management-service-service-plans-c94c85e.md).
    -   `SERVICE_INSTANCE:` Name of the service instance.

    There are several options available to create instances depending on the environment you use.

    -   To create a service instance in other environments using the Service Manager Control \(SMCTL\) CLI or SAP Service Manager APIs, see [Consuming Services in Other Environments Using the SAP Service Manager Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).

    -   To create a service instance in the Cloud Foundry environment using the SAP BTP cockpit or the cf CLI, see [Creating Service Instances](../30-development/creating-service-instances-8221b74.md).

    -   To create a service instance in Kyma using the Kyma dashboard, see [Using SAP BTP Services in the Kyma Environment](../30-development/using-sap-btp-services-in-the-kyma-environment-ea4dd81.md).

    > ### Recommendation:  
    > If you are not working in Cloud Foundry, Kyma, or Kubernetes, use the SAP Service Manager to create and manage service instances. These instances are platform-agnostic and can be deployed and integrated with any other environment of your choice.

2.  Get the OAuth 2.0 client information and `uas` service endpoints by creating a service key or binding. There are several options available to create service keys or bindings depending on the environment you use.
    -   To create bindings in other environments, see [Consuming Services in Other Environments Using the SAP Service Manager Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).

    -   To create a service key in the Cloud Foundry environment using the SAP BTP cockpit or the cf CLI, see [Creating Service Keys](../30-development/creating-service-keys-4514a14.md).

    -   To create credentials for calling the service and retrieving information in the Kyma environment, see [Using SAP BTP Services in the Kyma Environment](../30-development/using-sap-btp-services-in-the-kyma-environment-ea4dd81.md).


3.  Use `uaa_url`, `clientid`, and `clientsecret` to request an access token using the following commands:

    > ### Sample Code:  
    > For Windows OS \(Password grant type\):
    > 
    > ```
    > curl -L -X POST "<uaa_url>/oauth/token" ^ 
    > -H "Content-Type: application/x-www-form-urlencoded" ^ 
    > -u "<clientid>:<clientsecret>" ^ 
    > -d "grant_type=password" ^ 
    > -d "username=<user email>" ^ 
    > -d "password=<password>" 
    > 
    > ```

    > ### Sample Code:  
    > For Windows OS \(Client Credentials grant type\):
    > 
    > ```
    > curl -L -X POST "<uaa_url>/oauth/token" ^ 
    > -H "Content-Type: application/x-www-form-urlencoded" ^ 
    > -u "<clientid>:<clientsecret>" ^ 
    > -d "grant_type=client_credentials" ^
    > 
    > ```

    > ### Sample Code:  
    > For Mac OS \(Password grant type\):
    > 
    > ```
    > curl -L -X POST '<uaa_url>/oauth/token' \ 
    > -H 'Content-Type: application/x-www-form-urlencoded' \ 
    > -u '<clientid>:<clientsecret>' \ 
    > -d 'grant_type=password' \ 
    > -d 'username=<user email>' \
    > -d 'password=<password>'
    > 
    > ```

    > ### Sample Code:  
    > For Mac OS \(Client Credentials grant type\):
    > 
    > ```
    > curl -L -X POST '<uaa_url>/oauth/token' \ 
    > -H 'Content-Type: application/x-www-form-urlencoded' \ 
    > -u '<clientid>:<clientsecret>' \ 
    > -d 'grant_type=client_credentials' \ 
    > 
    > ```

    > ### Note:  
    > The access token that you receive also contains the scopes that are granted for this access token. Therefore, only APIs that require one of these scopes can be used with this access token.
    > 
    > ```
    > {
    >   "access_token": "<access_token>",
    >   "token_type": "bearer",
    >   "expires_in": 43199,
    >   "scope": "<xsappname>.UAS.reporting.GA_Admin"
    > }
    > 
    > ```

4.  Using the *<access\_token\>* that you received in the previous step you can call the [Resource Consumption APIs](https://api.sap.com/api/APIUasReportingService/tryout) using bearer authentication or you can try them directly in the SAP Business Accelerator Hub using the following steps:

    1.  Got to [Resource Consumption APIs](https://api.sap.com/api/APIUasReportingService/tryout) in the SAP Business Accelerator Hub.
    2.  Choose *Select Environment* and select the *Add New Environment* option
    3.  In the *Authentication Type* field, select*OAuth 2.0 Application Flow*.
    4.  Provide the parameters that you have retrieved in the following fields: `clientid`, `clientsecret`, and `identityzone`.
    5.  Save your changes.


5.  Choose the API that you want to call, provide the relevant parameters, and choose *Run*.

To learn more about the SAP Business Accelerator Hub, see [What Is the SAP API Business Hub?](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/54871d308811444d8d84fbb3fb82cf4c.html)

