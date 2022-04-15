<!-- loio40290a93fb5c4603a65c48df71a38bf2 -->

# Configure Token Policy for SAP Authorization and Trust Management Service

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

-   To change token validity, access the Security Settings API.

    ```json
    "tokenPolicySettings": {
      …
      "accessTokenValidity": 1800,
      "refreshTokenValidity": 43200,
      …
    }
    ```

    For more information, see [Security Settings API](https://api.sap.com/api/SecuritySettingsAPI/resource) on *SAP API Business Hub*.


