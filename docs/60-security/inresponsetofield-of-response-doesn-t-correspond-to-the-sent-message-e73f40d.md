<!-- loioe73f40d4dc1347c9ae0533cc5df22921 -->

# InResponseToField of Response Doesn‘t correspond to the Sent Message



## Symptom

When the user tries to log on with SAML or by refreshing the session, they see the *InResponseToField of Response doesn‘t correspond to the sent message* error.



## Reason and Prerequisites

This error occurs when handling an authentication response without a known corresponding request; for example, as the consequence of a session timeout. The timeout is a safeguard for performance and security reasons.



## Solution



### Don't delay the logon action

Ensure that the user login is within the timeframe of 15 minutes.



### Check the identity provider

The identity provider may be out of sync; or if it consistently takes a long time to issue the authentication response, reduce this time and check.



### Check the audit log

Check the audit log for the *AuthnRequest expired - ID: <RequestId\> Destination: <IdPDestination\>* error. If you find this error message, refer to [AuthnRequest expired - ID: <RequestId\> Destination: <IdPDestination\>](authnrequest-expired-id-requestid-destination-idpdestination-01aee78.md).

For more information about the audit log, refer to [Auditing and Logging Information for SAP Authorization and Trust Management Service - SAP Help Portal](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/d8f4b7c7298a422183beddb4ad47c108.html).

