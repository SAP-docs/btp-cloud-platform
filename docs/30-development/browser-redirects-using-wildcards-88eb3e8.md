<!-- loio88eb3e851c5f4dca92c3e64979fabb94 -->

# Browser Redirects Using Wildcards

You want to configure browser redirect URLs for multiple external web sites of your company. We recommend that you specify absolute URLs and avoid using wildcards.



> ### Caution:  
> When using wildcards in the redirect URLs, you open up the redirect for multiple web sites. Using wildcards increases the risk of redirecting to malicious web sites.

You want to allow multiple redirect URLs, for example in the `sap.com` domain. Use wildcards in the redirect URIs of the OAuth 2.0 configuration of `xs-security.json`. In this example, the configuration in `xs-security.json` allows external redirect URLs that contain `sap.com`.



<a name="loio88eb3e851c5f4dca92c3e64979fabb94__section_qj2_2ky_yfb"/>

## Configuration of `xs-app.json`

In the following example, you configure a logout page, which is a static external URL. Define the external URL in `xs-app.json`.

> ### Example:  
> > ### Sample Code:  
> > ```
> > "logout": {
> >         "logoutEndpoint": "/my/logout",
> >         "logoutPage": "https://support.sap.com"
> > ```



<a name="loio88eb3e851c5f4dca92c3e64979fabb94__section_ddg_rky_yfb"/>

## Configuration of xs-security.json

The following example allows redirects to all web sites with `sap.com` as domain. It allows secure pages. Define redirect URLs with wildcards.

> ### Example:  
> ```
> "oauth2-configuration": {
>                        "token-validity": 900, 
>                        "redirect-uris": ["https*://*.sap.com/**",
>                                          "https://<application_hostname>.<landscape_domain>/**"
>                                          ]
> ```

> ### Example:  
> For China \(Shanghai\) region:
> 
> ```
> "oauth2-configuration": {
>                        "token-validity": 900, 
>                        "redirect-uris": ["https*://*.sap.com/**",
>                                          "https://<application_hostname>.<custom_domain>/**"
>                                          ]
> ```

**Related Information**  




