<!-- loio1503442f766145fd8cfe9caa0c087da3 -->

# Configure Principal Propagation from BTP Applications to On-Premise Systems Using Corporate IdP Tokens

In scenarios where your SAP BTP application, such as SAP Build Work Zone interacts with applications that don't support tokens issued by the SAP BTP cloud services, but require a token from a corporate identity provider, you can configure SAP BTP applications to include this token.



<a name="loio1503442f766145fd8cfe9caa0c087da3__prereq_dfq_qzt_xfc"/>

## Prerequisites

-   You have configured trust with an SAP Cloud Identity Services tenant with OpenID Connect \(OIDC\).

    For more information, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](../50-administration-and-ops/establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md).

-   You have configured trust with a corporate identity provider by your SAP Cloud Identity Services with OIDC.

    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/8ff83a12bbb8491c9558d635d6bbb287.html) in the SAP Cloud Identity Services documentation.

-   You have configured




## Context

In this scenario, the SAP BTP application passes the token of a corporate identity provider with the help of connectivity services to your on-premise SAP system. To configure this form of principal propagation, you must ensure SAP Cloud Identity Services and the relevant connectivity services are configured to support this scenario.

The following figure illustrates this scenario.

  
  
**Cloud Connector Using Embedded Tokens**



![](images/Simplified_Embedded_IDP_Token_997d0af.png)



## Procedure

1.  Subscribe to an application in your subaccount that supports this principal propagation scenario.

    Refer to the documentation of the application, which supports this scenario.

2.  Enable SAP Cloud Identity Services to forward tokens of the corporate identity provider.

    Enrich the `forward_corp_idp_token` claim with the `id_token` value.

    For more information, see [Enrich Token Claims Coming from Corporate IdP](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/enrich-token-claims-coming-from-corporate-idp?version=Cloud).

3.  Configure your new application to authenticate with the same corporate identity provider which your on-premise system uses.

    Set the corporate identity provider as the default identity provider.

    For more information, see [Choose Default Identity Provider for an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/choose-default-identity-provider-for-application?version=Cloud).

4.  Check if you need to configure a destination to connect your application to the Cloud Connector.

    The application you subscribed to may have provisioned this destination for you. Check the configuration documentation of the application to which you subscribed. If you need to create your own destination, set the following properties:

    **Required Destination Properties**


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
    
    `Type`
    
    </td>
    <td valign="top">
    
    `HTTP`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    `PrincipalPropagation`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    `OnPremise`
    
    </td>
    </tr>
    </table>
    
    For more information, see [Principal Propagation SSO Authentication for HTTP](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/principal-propagation-sso-authentication-for-http?version=Cloud).

5.  Decide if you want to ensure that Cloud Connector only authenticates with tokens from your corporate identity provider.

    If you don't want your on-premise system to trust cloud services like SAP Cloud Identity Services and SAP Authorization and Trust Management service, check that the Cloud Connector configuration doesn't trust these services.

    For more information, see [Configure Trusted Entities in the Cloud Connector](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/set-up-trust-for-principal-propagation?version=Cloud#configure-trusted-entities-in-the-cloud-connector).




<a name="loio1503442f766145fd8cfe9caa0c087da3__postreq_dyf_rcd_yfc"/>

## Next Steps

You can now test the application you subscribed to. If the principal propagation doesn't work as expected, try the following:

-   Troubleshooting logs of SAP Cloud Identity Services

    See [Logging OpenID Connect Tokens](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/logging-openid-connect-tokens?version=Cloud).

-   Logs of the Cloud Connector

    See [Monitoring, Logging, And Troubleshooting](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-troubleshooting?version=Cloud).


