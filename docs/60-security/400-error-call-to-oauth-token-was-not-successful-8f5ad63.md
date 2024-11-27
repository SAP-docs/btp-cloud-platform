<!-- loio8f5ad63c3e8641ceb68b703313bb7277 -->

# 400 Error: Call to /oauth/token Was Not Successful



## Symptom

You tried to log on to your application and got an error related to the token size exceeding some limits \(for example, the HTTP header size\).



## Reason and Prerequisites

By default, access and refresh tokens include SAML groups and role collections. If you have a lot of SAML groups or role collections, the token size increases, and this can cause the JWT to exceed the size limit of 16 K. This results in a 400 error and the user not being able to log in.



## Solution



### Keep the JWT size to a minimum

Application security is maintained in the application security descriptor file \(`xs-security.json`\). In the syntax of the application security descriptor file, do the following to keep the JWT size to a minimum.

-   Set the value of the `system-attributes` parameter to an empty array, like this: `"system-attributes": []`


-   Configure only the required groups in the Identity Provider \(IdP\).



For more information regarding the `xs-security.json` file, see [Application Security Descriptor Configuration Syntax](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/517895a9612241259d6941dbf9ad81cb.html).

