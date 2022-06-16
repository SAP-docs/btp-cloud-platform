<!-- loioe623e372e6174f81af2b9b8ef8f6d6d3 -->

# Configuring Application URLs

By default, all applications running on SAP BTP are accessed on the **default landscape** domain. According to your needs, you can change the default application URL by configuring additional application domains.

The URL for an application deployed on SAP BTP in the Cloud Foundry environment is `https://<application>.cfapps.<region>.hana.ondemand.com`. The domain depends on your location, in the European region, for example, the domain is `cfapps.eu10.hana.ondemand.com`. So, if you're deploying an application with the name "myapp", the default application URL is `https://myapp.cfapps.eu10.hana.ondemand.com`.

Running on the China \(Shanghai\) region:

There’s no default URL available in China, therefore you can’t deploy an application without configuring a custom domain first. Please refer to the related information link on how to use custom domains.

> ### Note:  
> To check what domains are available in your Cloud Foundry organization, use the command `cf domains`.



## Custom Domains

Use custom domains to reach your applications on your own domain instead of the default domain, for example, `https://myapp.mydomain.com` instead of `https://myapp.cfapps.eu10.hana.ondemand.com`. When you use a custom domain, both the domain name and the TLS/SSL certificate of the server are owned by the customer.

You can configure custom domains using the Cloud Foundry command-line interface with the plugin for custom domains.

For more information, read the [Custom Domain service user guide](https://help.sap.com/viewer/387fdc36085944889eba422e191c887b/Internal/en-US/4414cc43db2d4229b27b232a5590e253.html "Configure and expose your application under your own domain.") :arrow_upper_right:.



<a name="loioe623e372e6174f81af2b9b8ef8f6d6d3__section_ljv_sq2_gjb"/>

## Application Routes

If you want to make your application reachable on another route, you can add additional routes using the Cloud Foundry CLI. If your application is available under the route `https://myapp.cfapps.eu10.hana.ondemand.com`, you could add a route that reads `https://expenses.cfapps.eu10.hana.ondemand.com` that leads to the same application.

**Related Information**  


[Using Custom Domains](using-custom-domains-2291aea.md "SAP BTP allows subaccount owners to make their SAP BTP applications reachable and secure via a custom domain that is different from the default domain – for example, subdomain.mydomain.com.")

[About Routes in the Cockpit](about-routes-in-the-cockpit-4af288c.md "Routes are the URLs that enable your end users to reach your application.")

[Configuring Application URLs (Neo environment)](https://help.sap.com/viewer/663f91a6573b49ae9fa5f0007abb4d18/Internal/en-US/7ceeaa5e528140c48ae53b68433293ba.html "By default, all applications running on SAP BTP are accessed on the hana.ondemand.com domain.") :arrow_upper_right:

