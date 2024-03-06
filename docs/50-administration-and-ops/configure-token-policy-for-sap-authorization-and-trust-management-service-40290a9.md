<!-- loio40290a93fb5c4603a65c48df71a38bf2 -->

# Configure Token Policy for SAP Authorization and Trust Management Service

Set the token policy in the SAP BTP cockpit for SAP Authorization and Trust Management service by configuring the validity of the OpenID Connect \(OIDC\) tokens the service issues.



<a name="loio40290a93fb5c4603a65c48df71a38bf2__prereq_xfy_11q_qqb"/>

## Prerequisites

> ### Recommendation:  
> Review the security implications of token policies for SAP Authorization and Trust Management service.
> 
> For more information, see [Setting Token Policy](../60-security/security-considerations-for-the-sap-authorization-and-trust-management-service-f117cab.md#loioc8770b0b43084d838e475bd76eeb4715).



## Context

On request, SAP Authorization and Trust Management service issues access and refresh tokens.

With a valid access token, you can access a protected resource. Once an access token expires, you can get new access tokens with a refresh token. Once the refresh token expires, you must reauthenticate and request new access and refresh tokens.

> ### Recommendation:  
> Relaxing the token policy means that users reauthenticate less. However, increasing the token validity also means that if a malicious user manages to steal a token, that malicious user has access until the token expires. Keep token validity as short as possible, but not less than 30 minutes.

To change the token validity, access the security settings. The change applies to all service instances in the subaccount that haven't set a specific value in the application security descriptor \(`xs-security.json`\).



<a name="loio40290a93fb5c4603a65c48df71a38bf2__steps_rpv_4nw_k1c"/>

## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  Choose *Security* \> *Settings*.

4.  Choose the *Token Validity* tab.

    You see the setting of the current access token validity and of the current refresh token validity.

5.  Use the slider to set the validity for each token. The tooltip shows the selected value in seconds.

    > ### Example:  
    > -   Set the access token validity to 1800 seconds
    > 
    > -   Set the refresh token validity to 43200 seconds.


6.  To save the value, choose *Set Token Validity*.

    > ### Note:  
    > It is also possible to change the token validity in the Security Settings API.
    > 
    > For more information, see [Security Settings API](https://api.sap.com/api/SecuritySettingsAPI/resource) on [SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt?section=Artifacts).


**Related Information**  


[Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.")

