<!-- loioacb7d65cd83a4e29b3d817b1ec69f4ea -->

# Response Issue Time is Either too Old or with Date in the Future. Sync IdP to Match Skew <skew\>



## Symptom

SAML logon doesn't work and the *Response issue time is either too old or with date in the future. Sync IdP to match skew <skew\>* error message is displayed.



## Reason and Prerequisites

This error occurs when the time skew between the SAP Authorization and Trust Management service and the identity provider is larger than 60 seconds in either direction, or when after being issued, the authentication response takes more than 60 seconds to reach the SAP Authorization and Trust Management service.



## Solution

Check the time skew between the identity provider and the SAP Authorization and Trust Management service, and then sync the clock of the identity provider.

