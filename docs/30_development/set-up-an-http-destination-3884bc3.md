<!-- loio3884bc38209843ac900d92adb9c2a863 -->

# Set Up an HTTP Destination

Set up HTTP connectivity for the ABAP environment by configuring an HTTP destination.

To configure an HTTP destination in the SAP BTP cockpit, perform the following steps:

1.  Navigate to the relevant destination service instance.

    > ### Note:  
    > Instead of creating a destination from your own Destination service instance, you can configure destinations directly on subaccount level, in the subaccount in which the ABAP instance resides \(recommended\). See also [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md).

2.  In the menu, navigate to *Destinations*.
3.  Select *New Destination*.
4.  Enter a destination *<Name\>*.
5.  Use the value help to select ***HTTP*** as *<Type\>*.
6.  \(Optional\) Enter a description for the destination.
7.  Specify the destination *<URL\>*.
8.  For *<Proxy Type\>*, select ***Internet*** or ***OnPremise*** from the value help.
9.  For *<Authentication\>*, select one of these authentication methods for your proxy type:
    -    **Internet**:
        -   ***NoAuthentication***

        -   ***BasicAuthentication***

        -   ***Oauth2ClientCredentials***

        -   ***Oauth2SAMLBearerAssertion***

        -   ***Oauth2UserTokenExchange***

        -   ***ClientCertificateAuthentication*** 

            > ### Note:  
            > For client certificate authentication, you must upload the X.509 client certificate in P12 format in the ABAP environment, using the *Maintain Client Certificates* application \(for more information, see [Maintain Client Certificates](../50_administration_and_ops/maintain-client-certificates-7f6a8fb.md)\).


    -   **OnPremise**:
        -   ***BasicAuthentication*** or
        -   ***PrincipalPropagation***.


10. If you are using ***ClientCertificateAuthentication*** as authentication method, set the *<Use client-provided certificate\>* flag.

    > ### Note:  
    > This flag is only visible if the *<URL\>* field contains a URL string starting with *https://...*.

11. If you are using more than one Cloud Connector for on-premise connectivity in your subaccount, you must enter the *<Location ID\>* of the target Cloud Connector. See also [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html) \(section **Procedure**, step 4\).
12. Press *Save*.



<a name="loio3884bc38209843ac900d92adb9c2a863__section_onm_hvs_mnb"/>

## Next Step \(Optional\): Enable HTTP Communication in Your ABAP Code

1.  Open Eclipse, and create and execute a runnable class.
2.  To enable HTTP communication, see [Enable HTTP Communication in Your ABAP Code](enable-http-communication-in-your-abap-code-cef1ada.md).

> ### Note:  
> When using on-premise connectivity, make sure the called ICF service is exposed in Cloud Connector. See [Configure Access Control \(HTTP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e7d4927dbb571014af7ef6ebd6cc3511.html).



<a name="loio3884bc38209843ac900d92adb9c2a863__section_jwx_ypm_mnb"/>

## Related Information

[HTTP Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/42a0e6b966924f2e902090bdf435e1b2.html)

