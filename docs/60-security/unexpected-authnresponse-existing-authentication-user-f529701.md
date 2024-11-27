<!-- loiof5297011cd464b2ea35d9861023655b0 -->

# Unexpected AuthnResponse : Existing authentication - <User\>



## Symptom

After logging on to an application with SAML, the user presses the back button of the browser. This leads to the *Unexpected AuthnResponse : Existing authentication - <User\> error*.



## Reason and Prerequisites

Using the back button leads to a second authentication request to the identity provider, with the same ID used for the initial logon. As a result, the identity provider issues a second authentication response for the same ID, which is then rejected.



## Solution

The error message displayed is the correct outcome of this action. If you want to trigger a logout by pressing the back button, this needs to be handled on the application side.

