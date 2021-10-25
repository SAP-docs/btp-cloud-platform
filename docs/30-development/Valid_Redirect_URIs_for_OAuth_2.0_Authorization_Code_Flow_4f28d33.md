<!-- loio4f28d335fa2543d7b24e27f7e8e399f7 -->

# Valid Redirect URIs for OAuth 2.0 Authorization Code Flow

After logging on to an application, you want to be redirected exactly to the page of the application in question. You don't want to use an open redirect, which takes you to the wrong page, for example, or worse, to a malicious page.

At runtime, the User Account and Authentication service checks the redirect URI for correctness and rejects access attempts to incompatible redirect URIs. This check is possible because the security descriptor file `xs-security.json` contains the correct redirect URI.

> ### Sample Code:  
> ```
> "oauth2-configuration": {
>         "redirect-uris": ["http://*<host\_name1\>*","http://*<host\_name2\>*"] 
> }
> ```

For more information, see the related links.

The User Account and Authentication service stores the correct redirect URIs in the OAuth client table. To avoid this kind of arbitrary redirect after a logon request, the UAA checks the redirect URI and thus makes sure that users access the correct page.

**Related Information**  


[Configure Redirect URLs for Browser Logout](Configure_Redirect_URLs_for_Browser_Logout_690931c.md "To avoid open redirect attacks, direct users to a safe and valid URL when they log out.")

[Browser Redirects Using Wildcards](Browser_Redirects_Using_Wildcards_88eb3e8.md "You want to configure browser redirect URLs for multiple external web sites of your company. We recommend that you specify absolute URLs and avoid using wildcards.")

[Listing Allowed Redirect URIs](../60-security/Security_Considerations_for_the_SAP_Authorization_and_Trust_Management_Service_f117cab.md#loio88b7d9d4c6ff4498b48dbc0b7be8a294 "The application security descriptor (xs-security.json) includes the redirect-uris parameter. This parameter contains a list of the redirect URIs that SAP BTP checks for when redirecting. If your landscape domain or custom domain isn't on this list, including wildcards, the SAP Authorization and Trust Management service won't redirect users there.")

