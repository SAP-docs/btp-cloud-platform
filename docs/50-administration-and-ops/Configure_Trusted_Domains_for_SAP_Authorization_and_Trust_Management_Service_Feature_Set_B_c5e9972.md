<!-- loioc5e997235f724ec686dc5dc101a1ccfb -->

# Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]

By default, login pages of the SAP Authorization and Trust Management service \(XSUAA\) can’t be framed by other applications in different domains for security reasons.



<a name="loioc5e997235f724ec686dc5dc101a1ccfb__prereq_xfy_11q_qqb"/>

## Prerequisites

> ### Recommendation:  
> Review the security implications of using inline frames \(IFrames\) with SAP Authorization and Trust Management service.
> 
> For more information, see [Implications of Using IFrames](../60-security/Security_Considerations_for_the_SAP_Authorization_and_Trust_Management_Service_f117cab.md#loioea351dd76f8946c995145bc6a4b235f3).



## Context

To prevent clickjacking or overlay attacks, web browsers follow a same origin policy. The same origin policy means you can only embedded content in your web page if the content shares the same protocol, host, and port as your web page. If the origins don't match, you must maintain a list of origins that allows for exceptions to the same origin policy. The same origin policy also applies to cookies. Cookies enable single sign-on scenarios. If the cookies have a different origin, the browser rejects them like any other content.

> ### Recommendation:  
> Instead of configuring lists of trusted domains, ensure that your application runs under the same domain as the framing application.
> 
> For more information about SAP Custom Domain service, see the documentation of the [SAP Custom Domain Service](https://help.sap.com/viewer/product/CUSTOM_DOMAINS/Cloud/en-US).
> 
> If your custom identity provider runs under a different domain as the framing application, you must configure the identity provider to trust the domain of the framing application, too.



## Procedure

1.  Go to your subaccount \(see [Navigate in the Cockpit](Navigate_in_the_Cockpit_0874895.md)\) and choose *Security* \> *Settings*.

2.  Choose   \(Add\) .

3.  Enter the host name for the trusted domain.

    For example: `https://store.example.com`

4.  Save your entries.




<a name="loioc5e997235f724ec686dc5dc101a1ccfb__postreq_abw_tcq_qqb"/>

## Next Steps

Ensure that other component framed by the host application also trust the framing domain. Typical components include the application router and the identity provider.

**Related Information**  


[Application Router](../30-development/Application_Router_01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Configure Trust Domains \(in SAP Cloud Identity Services - Identity Authentication Documentation\)](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/08fa1fe816704d99a6bcab245158ebca.html)

