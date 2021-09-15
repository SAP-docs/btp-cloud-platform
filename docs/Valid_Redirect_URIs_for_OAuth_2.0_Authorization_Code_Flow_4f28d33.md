<!-- loio4f28d335fa2543d7b24e27f7e8e399f7 -->

# Valid Redirect URIs for OAuth 2.0 Authorization Code Flow

After logging on to an application, you want to be redirected exactly to the page of the application in question. It should therefore not be possible to use an open redirect, which might take you to the wrong page for example, or to a malicious page.

At runtime, the User Account and Authentication service checks the redirect URI for correctness and rejects access attempts to incompatible redirect URIs. This is possible because the security descriptor file `xs-security.json` contains the correct redirect URI.

> ### Sample Code:  
> ```
> "oauth2-configuration": {
>                                            "redirect-uris": ["http://<host_name1>","http://<host_name2>"] 
> 
> ```

For more information, see the related links.

The User Account and Authentication service stores the correct redirect URIs in the OAuth client table. To avoid this kind of arbitrary redirect after a logon request, the UAA checks the redirect URI and thus makes sure that users access the correct page.

**Related Information**  






