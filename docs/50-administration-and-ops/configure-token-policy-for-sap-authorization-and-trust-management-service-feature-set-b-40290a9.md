<!-- loio40290a93fb5c4603a65c48df71a38bf2 -->

# Configure Token Policy for SAP Authorization and Trust Management Service \[Feature Set B\]

Set the token policy for SAP Authorization and Trust Management service \(XSUAA\) by configuring the validity of the OpenID Connect \(OIDC\) tokens the service issues.



<a name="loio40290a93fb5c4603a65c48df71a38bf2__prereq_xfy_11q_qqb"/>

## Prerequisites

> ### Recommendation:  
> Review the security implications of token policies for SAP Authorization and Trust Management service.
> 
> For more information, see [Setting Token Policy](../60-security/security-considerations-for-the-sap-authorization-and-trust-management-service-f117cab.md#loioc8770b0b43084d838e475bd76eeb4715).



## Context

On request, SAP Authorization and Trust Management service issues access, ID, and refresh tokens. Access and ID tokens share a validity configuration. Refresh tokens have a separate validity configuration.

With a valid access or ID token, you can access a protected resource. Once an access or ID token expires, you can get new access and ID tokens with a refresh token. Once the refresh token expires, you must reauthenticate and request new access, ID, and refresh tokens.

> ### Recommendation:  
> Relaxing the token policy means that users reauthenticate less. However, increasing the token validity also means that if a malicious user manages to steal a token, that malicious user has access until the token expires. Keep token validity as short as possible, but not less than 30 minutes.



<a name="loio40290a93fb5c4603a65c48df71a38bf2__steps_ayn_dmx_qqb"/>

## Procedure

1.  Go to your subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Settings*.

2.  In the *Token Validity* section, set the required values.


    <table>
    <tr>
    <th valign="top">

    Token Setting


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *Access Token Validity*


    
    </td>
    <td valign="top">

    Sets the token lifetime in seconds for access and ID tokens issued by SAP Authorization and Trust Management service. The value ranges from 300 seconds to 99,999,999 seconds, in other words, from 5 minutes to more than 3 years.

    Default: 43200 seconds \(12 hours\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Refresh Token Validity*


    
    </td>
    <td valign="top">

    Sets the token lifetime in seconds for refresh tokens issued by SAP Authorization and Trust Management service. The value ranges from 600 seconds to 99,999,999 seconds, in other words, from 10 minutes to more than 3 years.

    Default: 24192000 seconds \(28 days\)


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The user interface limits the maximum validity for tokens. If you need maximum values beyond what the user interface offers, use the APIs.
    > 
    > For more information, see [Security Settings API](https://api.sap.com/api/SecuritySettingsAPI/resource) on *SAP API Business Hub*.

3.  Choose *Set Token Validity*.


