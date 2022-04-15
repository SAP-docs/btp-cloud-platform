<!-- loio3670474a58c24ac2b082e76cbbd9dc19 -->

# Getting an Access Token for SAP Cloud Management Service APIs

The APIs of the SAP Cloud Management service for SAP BTP are protected with the OAuth 2.0 Password grant type and, in some cases, also the Client Credentials grant type. This procedure guides you through the steps to create an OAuth client and obtain an access token from SAP Authorization and Trust Management service \(`xsuaa`\) to call the APIs of the SAP Cloud Management service.



The Client Credentials grant type is currently available for the SAP Cloud Management service only when creating the instances of this service on a subaccount level by using the SAP Service Manager API, CLI, or when creating an instance of an SAP Cloud Management service using the SAP BTP cockpit.

For more information, see [Consuming Services in Other Environments Using the Service Management Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).

> ### Note:  
> For information about getting an application access token for the APIs of SAP Software-as-a-Service Provisioning service, see [Getting an Application Access Token](../30-development/getting-an-application-access-token-6391b5d.md).

The scopes included in the access token depend on the service plan you chose for the SAP Cloud Management service. For the list of the available service plans, see [SAP Cloud Management Service - Service Plans](sap-cloud-management-service-service-plans-a508b72.md).



<a name="loio3670474a58c24ac2b082e76cbbd9dc19__section_im4_f4d_k3b"/>

## Prerequisites

Your global account admin has entitled at least one of the plans of the SAP Cloud Management service in your subaccount. See [SAP Cloud Management Service - Service Plans](sap-cloud-management-service-service-plans-a508b72.md) and [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).

> ### Note:  
> The service plan for the SaaS Provisioning Service APIs is entitled by default to all subaccounts.



<a name="loio3670474a58c24ac2b082e76cbbd9dc19__section_xph_mcr_w3b"/>

## Procedure

1.  Create a service instance for the SAP Cloud Management service \(`cis`\).

    When you create the service instance, specify the following parameters:

    -   `PLAN:` The name of the service plan you want to use. See [SAP Cloud Management Service - Service Plans](sap-cloud-management-service-service-plans-a508b72.md).
    -   `SERVICE_INSTANCE:` Name of the service instance.

    There are several options available to create instances depending on the environment you use.

    -   To create a service instance in the Cloud Foundry environment using the SAP BTP cockpit or the cf CLI, see [Creating Service Instances](../30-development/creating-service-instances-8221b74.md).

    -   To create a service instance in other environments using the Service Manager Control \(SMCTL\) CLI or SAP Service Manager APIs, see [Consuming Services in Other Environments Using the Service Management Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).

        You can also create and manage service instances and bindings in other environments by using the following APIs in the Accounts service:


        <table>
        <tr>
        <th valign="top">

        URL


        
        </th>
        <th valign="top">

        Name


        
        </th>
        </tr>
        <tr>
        <td valign="top">

        `POST/accounts/v1/subaccounts/{subaccountGUID}/serviceManagementBinding`


        
        </td>
        <td valign="top">

        `Create a Service Management binding`


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        `GET/accounts/v1/subaccounts/{subaccountGUID}/serviceManagementBinding`


        
        </td>
        <td valign="top">

        `Get a Service Management binding`


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        `DELETE/accounts/v1/subaccounts/{subaccountGUID}/serviceManagementBinding`


        
        </td>
        <td valign="top">

        `Delete a Service Management binding`


        
        </td>
        </tr>
        </table>
        
        For more information about the APIs, see the `Subaccount Operations` section of the `Accounts` service in the [SAP API Business Hub](https://api.sap.com/api/APIAccountsService/resource) 

        > ### Note:  
        > If you use the SAP Service Manager API, CLI, or the SAP BTP cockpit to create the service instance of the SAP Cloud Management service \(`cis`\), you can get a Client Credentials grant type token by specifying the following parameter during the instance creation: `{"grantType": "clientCredentials"}`.
        > 
        > If you don't specify this parameter, the Password grant type is chosen by default.

    -   To create a service instance in Kyma using the Kyma dashboard, see [Create Service Instances Using the Kyma Dashboard](../30-development/create-service-instances-using-the-kyma-dashboard-0453ffb.md).

    > ### Recommendation:  
    > If you aren't working in Cloud Foundry, Kyma, or Kubernetes, use the SAP Service Manager to create and manage service instances. These instances are platform agnostic and can be deployed and integrated with any other environment of your choice.

2.  Create a service key.

    When you create the service key, specify the following parameters:

    -   `SERVICE_INSTANCE:` Name of the service instance for which to create the service key.
    -   `SERVICE_KEY:` Name for the service key.

    There are several options available to create service keys depending on the environment you use.

    -   To create a service key in the Cloud Foundry environment using the SAP BTP cockpit or the cf CLI, see [Creating Service Keys](../30-development/creating-service-keys-4514a14.md).

    -   To create bindings in other environments, see [Consuming Services in Other Environments Using the Service Management Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/0714ac254e83492281d95e25548b388c.html).

    -   To create credentials for calling the service and retrieving information in the Kyma environment, see [Creating Credentials](../30-development/creating-credentials-945498c.md).


    > ### Sample Code:  
    > The following example shows the service key information displayed in the Cloud Foundry environment:
    > 
    > ```
    > 
    > {
    >    "endpoints": {
    >       "external_provider_registry_url": <external provider registry URL>,
    >       "accounts_service_url": <accounts service URL>,
    >       "entitlements_service_url": <entitlements service URL>,
    >       "events_service_url": <events service URL>,
    >       "order_processing_url": <order processing service URL>,
    >       "provisioning_service_url": <provisioning service URL>,
    >       "saas_registry_service_url": <saas registry service URL>,
    >    },
    >  "grant_type": "user_token",
    >  "uaa": {
    >   ...
    >   "clientid": <client_id>,
    >   "clientsecret": <client_secret>,
    >   "url": <uaa_url>,
    >   ...
    >  }
    > }
    > ```

3.  Use the `uaa_url`, `clientid`, and `clientsecret` to request an access token using the following commands:

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
    > If two-factor authentication \(2FA\) is activated on the SAP BTP landscape, then you need to append the passcode generated by the SAP Authenticator to your password.
    > 
    > For example, if your password is `Abcd` and the authenticator-generated passcode is `1234`, enter the password as ***Abcd1234***.
    > 
    > Two-factor authentication is only relevant for Password grant type authorization.

    > ### Note:  
    > The access token received also contains the scopes that are granted for this access token. Therefore, only APIs that require one of these scopes can be used with this access token.
    > 
    > ```
    > {
    >   "access_token": "<access_token>",
    >   "token_type": "bearer",
    >   "expires_in": 43199,
    >   "scope": "<xsappname>.job.read <xsappname>.event.read"
    > }
    > 
    > ```

    See [Enable API Access to an XSUAA Configuration](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ebc9113a520e495ea5fb759b9a7929f2.html).

4.  Call the SAP Cloud Management service APIs using Swagger with the `access_token` that you received in the previous step:
    1.  Choose one of the endpoints of your instance. See step 2 and the sample code for a service instance in Cloud Foundry.
    2.  Browse to `<endpoint url>/swagger-ui.html`.
    3.  In Swagger, choose *Authorize*.
    4.  Enter the `api_key` and choose *Authorize*.

        > ### Note:  
        > Use the `<access_token>` that you received in the step 3to compose the `api_key` in the format: `bearer` *<access\_token\>*


5.  Choose the API that you want to call, provide the relevant parameters, and choose *Try it out!*



<a name="loio3670474a58c24ac2b082e76cbbd9dc19__section_bbm_fnw_tqb"/>

## Trying Out SAP Cloud Management Service API in SAP API Business Hub

To learn more about SAP API Business Hub, see [What Is the SAP API Business Hub?](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/54871d308811444d8d84fbb3fb82cf4c.html)

> ### Note:  
> In the Hub, you find SAP Cloud Management Service APIs under the **Core Services for SAP BTP** API Package.

To start working with SAP Cloud Management Service APIs in SAP API Business Hub, you'll need to configure an environment. See [Trying Out APIs in a Configured Environment](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/f7796baaef6a48e9867298827f5028ff.html).

> ### Note:  
> You configure an environment by populating all mandatory fields in the *Create New Environment* wizard.
> 
> Refer to steps 2 and 3 of this topic to see how to get the values for Client ID, Client Secret, and Token URL fields.

**Related Information**  


[Access UAA Admin APIs](access-uaa-admin-apis-ebc9113.md "To enable programmatic access to the XS user authentication and authorization (UAA) service in your subaccount of the Cloud Foundry environment, create an XSUAA service instance under the apiaccess plan.")

