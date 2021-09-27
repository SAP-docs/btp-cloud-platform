<!-- loiof70fcf1c2d0a4a979adfe44cebc93c20 -->

# Principal Propagation

Exchange user ID information between systems or environments in SAP BTP.

**In This Section**

-   [Principal Propagation from the Cloud Foundry to the Neo Environment](Principal_Propagation_from_the_Cloud_Foundry_to_the_Neo_Environment_391e9ed.md#loio391e9ed92ff448e0b4bacac69f853516)
-   [Principal Propagation from the Neo to the Cloud Foundry Environment](Principal_Propagation_from_the_Neo_to_the_Cloud_Foundry_Environment_6e194f8.md#loio6e194f8e919a40bab7e39cd992677cb7)

**Other Principal Propagation Scenarios**

-   [On-Premise User Store](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/04cbd0f30d524612aa438ed0b0eed217.html "If you already have an existing on-premise system with a populated user store, you can configure SAP BTP applications to use that on-premise user store. This approach is similar to implementing identity federation with a corporate identity provider. In that way, applications do not need to keep the whole user database, but request the necessary information from the on-premise system.") :arrow_upper_right:
-   [Principal Propagation to OAuth-Protected Applications](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/310f39e504024079933066db8b6c6d00.html "Propagate users from external applications with SAML identity federation to OAuth-protected applications running in the Neo environment of SAP BTP. Exchange the user ID and attributes from a SAML assertion for an OAuth access token, and use the access token to access the OAuth-protected application.") :arrow_upper_right:
-   [Connectivity in the Cloud Foundry Environment: Principal Propagation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e2cbb48def4342048362039cc157b12e.html)
-   [Connectivity in the Neo Environment: Principal Propagation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/d4d3e1e9b2dd44318b49a4812cd51383.html)

-   **[Principal Propagation from the Neo to the Cloud Foundry Environment](Principal_Propagation_from_the_Neo_to_the_Cloud_Foundry_Environment_6e194f8.md#loio6e194f8e919a40bab7e39cd992677cb7 "Enable an application in your subaccount in the Neo environment to access another
		application in a subaccount in the Cloud Foundry environment without user login (and user
		interaction) in the second application. For this scenario to work, the two subaccounts need
		to be in mutual trust, and in trust with the same Identity Authentication tenant. The second
		application will propagate its logged-in user to the first application using an
		OAuth2SAMLBearer destination. ")**  
Enable an application in your subaccount in the Neo environment to access another application in a subaccount in the Cloud Foundry environment without user login \(and user interaction\) in the second application. For this scenario to work, the two subaccounts need to be in mutual trust, and in trust with the same Identity Authentication tenant. The second application will propagate its logged-in user to the first application using an OAuth2SAMLBearer destination.
-   **[Principal Propagation from the Cloud Foundry to the Neo Environment](Principal_Propagation_from_the_Cloud_Foundry_to_the_Neo_Environment_391e9ed.md#loio391e9ed92ff448e0b4bacac69f853516 "Enable an application in your subaccount in the Cloud Foundry environment to access an
		OAuth-protected application in a subaccount in the Neo environment without user login (and
		user interaction) in the second application. For this scenario to work, the two subaccounts
		need to be in mutual trust, and in trust with the same identity provider. The first
		application will propagate its logged-in user to the second application using an
		OAuth2SAMLBearer destination. ")**  
Enable an application in your subaccount in the Cloud Foundry environment to access an OAuth-protected application in a subaccount in the Neo environment without user login \(and user interaction\) in the second application. For this scenario to work, the two subaccounts need to be in mutual trust, and in trust with the same identity provider. The first application will propagate its logged-in user to the second application using an OAuth2SAMLBearer destination.

**Related Information**  


[Propagate User Information Between Applications or Services](../30-development/Propagate_User_Information_Between_Applications_or_Services_7daed6d.md "When a business application communicates with a service, you must decide whether you want to propagate the identity of the user that called the business application, or if a call from machine-to-machine is sufficient.")

