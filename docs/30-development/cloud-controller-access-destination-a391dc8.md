<!-- loioa391dc8f538d444bb8f2e742c5b1e4df -->

# Cloud Controller Access Destination



A destination called ASP\_CC needs to be created for ABAP Solution Service to be able to access the Cloud Foundry Cloud Controller API for creation and access to ABAP service instances.



### Prerequisites

-   You've created a user in SAP ID service.

-   The user has been added as a Cloud Foundry org member in the provider subaccount where the Cloud Foundy environment is enabled.

-   The User has been added with the role of a Space Developer, in the space where the multitenant application \(MTA\) is deployed.


> ### Note:  
> Please note that you should never set your own personal credentials in the User and Password fields. Always use a technical user instead.



### Process Steps

1.  In the provider subaccount navigate to Connectivity -\> Destinations
2.  Create a new destination as follows:


    <table>
    <tr>
    <th valign="top">

    Property


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name


    
    </td>
    <td valign="top">
    
    ASP\_CC


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Type


    
    </td>
    <td valign="top">
    
    HTTP


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description


    
    </td>
    <td valign="top">
    
    Access the Cloud Foundry Cloud Controller API


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    URL


    
    </td>
    <td valign="top">
    
    < API Endpoint domain of Cloud Foundry landscape\>

    You can find it under your subaccount \> Overview.

    > ### Example:  
    > https://api.cf.eu10.hana.ondemand.com


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Proxy Type


    
    </td>
    <td valign="top">
    
    Internet


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Authentication


    
    </td>
    <td valign="top">
    
    OAuth2Password


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    User


    
    </td>
    <td valign="top">
    
    <User ID/E-mail\>


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Password


    
    </td>
    <td valign="top">
    
    <Password\>


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client ID


    
    </td>
    <td valign="top">
    
    cf


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client Secret


    
    </td>
    <td valign="top">
    
    <needs to be left blank\>


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service URL


    
    </td>
    <td valign="top">
    
    http:// uaa.<landscape-host\>/oauth/token

    > ### Example:  
    > https://uaa.cf.eu10.hana.ondemand.com/oauth/token


    
    </td>
    </tr>
    </table>
    
    For more information on landscapes/regions, see [Regions and API Endpoints for the ABAP Environment.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html#879f37370d9b45e99a16538e0f37ff2c.html)


Instead of creating the ASP\_CC destination manually, you can also save the following as a text file instead and then import the destination as a template:

> ### Sample Code:  
> ```
> Type=HTTP
> clientId=cf
> Authentication=OAuth2Password
> Name=ASP_CC
> tokenServiceURL=https\://uaa.cf.eu10.hana.ondemand.com/oauth/token
> ProxyType=Internet
> URL=https\://api.cf.eu10.hana.ondemand.com
> 
> ```

