<!-- loio01aee78bd47345e79ece434a768b5dc1 -->

# AuthnRequest expired - ID: <RequestId\> Destination: <IdPDestination\>



## Symptom

When a SAML session is dropped, the audit log shows AuthnRequest expired - ID: <RequestId\> Destination: <IdPDestination\>. This particular error message can be found only in the audit log.



## Reason and Prerequisites

This error occurs when the identity provider takes more than 15 minutes to issue the authentication response or when the user waits with the logon action for more than 15 minutes on the identity provider side. After this time interval, the session information is dropped for performance and security reasons; and thus, the request and response do not match anymore.



## Solution



### Don't delay the logon action

Ensure that the user login is within the timeframe of 15 minutes.



### Check the identity provider

The identity provider may be out of sync; or if it consistently takes a long time to issue the authentication response, reduce this time and check.

