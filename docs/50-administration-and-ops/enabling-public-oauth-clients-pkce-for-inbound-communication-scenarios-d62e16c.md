<!-- loiod62e16c461de4e09aaa5f50147a7eabb -->

# Enabling Public OAuth Clients \(PKCE\) for Inbound Communication Scenarios



<a name="loiod62e16c461de4e09aaa5f50147a7eabb__HowToEnable_PKCE_context"/>

## Context

Communication scenarios that support OAuth 2.0 as authentication method for inbound communication can now be consumed by public OAuth clients using PKCE \(Proof Key for Code Exchange\). This allows desktop applications \(acting as OAuth Clients\) to consume OAuth-protected OData services with the identity of a business user. The business user will be prompted for providing consent to this action once \(a web browser is required for this\).

To enable consumption by public OAuth clients using PKCE, proceed as follows:



<a name="loiod62e16c461de4e09aaa5f50147a7eabb__HowToEnable_PKCE_steps"/>

## Procedure

1.  In the *Communication Systems*app, enter the *Client Redirect URI* under Inbound OAuth 2.0 Client Settings. Thereby you define the URL to which the client will redirect the browser after authorization has been granted by the user.

2.  Under *Users for Inbound Communication*, click Add.

3.  In the *New User for Inbound Communication* pop-up that appears, select *OAuth 2.0* in the *Authentication Method* dropdown list, enter the *OAuth 2.0 Client ID* and click *OK*.


**Related Information**  


[How to Create a Communication Arrangement](how-to-create-a-communication-arrangement-a0771f6.md "")

