<!-- loio22a7d69e35574ab082561acbcfa4cd3f -->

# Domain Checks at Browser Login and Logout

When a user logs in to a web application or logs out using a browser, the `xsuaa` component checks the domain in the URL of the application routes. To avoid open redirect attacks, `xsuaa` checks the URLs, which are defined in `xs-app.json`, against a list of allowed redirect URIs in the application security descriptor file \(`xs-security.json`\).



A web application in the Cloud Foundry environment of SAP BTP has application routes. These routes are URLs that point to the web application. At runtime, the `xsuaa` component checks whether the redirect URI for login and logout is correct and rejects any attempts to access incompatible redirect URIs. The `xsuaa` component checks the domains in these URLs during authentication and logout. A successful check ensures that users who log out are redirected to a URL that reflects the logout and thus makes sense for the users.



<a name="loio22a7d69e35574ab082561acbcfa4cd3f__section_rwl_fx1_tfb"/>

## Default Domain

Usually, the application uses the default domain in the application route URL. For this reason, enter the relevant application route.

> ### Example:  
> <code><i class="varname">&lt;application_hostname&gt;</i>.<i class="varname">&lt;landscape_domain&gt;</i></code>
> 
> Example for the `eu10` landscape:
> 
> `myapp.cfapps.eu10.hana.ondemand.com`

> ### Example:  
> For China \(Shanghai\) region:
> 
> <code><i class="varname">&lt;application_hostname&gt;</i>.<i class="varname">&lt;custom_domain&gt;</i></code>



<a name="loio22a7d69e35574ab082561acbcfa4cd3f__section_xwg_mx1_tfb"/>

## Custom Domain

See the SAP Note in the related link for information on how to set custom domains in the Cloud Foundry environment of SAP BTP.

As an application developer, if you use custom domains in the application routes of your web application, you must include the login and logout URLs in the `xs-security.json` of the `xsuaa` service instance. The configuration of the redirect URIs is located in the `oauth2-configuration` custom option of the security application descriptor file \(`xs-security.json`\). Here, you have to define the URLs in `redirect-uris` of the custom options in the OAuth 2. 0 configuration. You can also use wild cards \(`*`\) to allow multiple URLs that belong to one domain.

For more information, see the related links.

**Related Information**  




[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-517895a.md "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.")

[Configuring Application URLs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/7ceeaa5e528140c48ae53b68433293ba.html "By default, all applications running on SAP BTP are accessed on the hana.ondemand.com domain.") :arrow_upper_right:

[SAP Note 2668456 on setting custom domains](https://launchpad.support.sap.com/#/notes/2668456 on setting custom domains)

[Cloud Foundry documentation about redirect parameters for logout](https://docs.cloudfoundry.org/api/uaa/version/4.24.0/index.html#session-management)

