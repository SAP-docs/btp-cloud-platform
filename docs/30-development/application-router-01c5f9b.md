<!-- loio01c5f9ba7d6847aaaf069d153b981b51 -->

# Application Router

The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.

You can set up and run your own application router or you can use the application router that is managed by SAP \(for more information see [Managed Application Router](managed-application-router-589a239.md)\).

We recommend running you own application router only in advanced cases, for example when application router extensibility is required. The application router is available on the following sites:

-   As a library on npmjs.com \(NPM\), see [@sap/approuter](https://www.npmjs.com/package/@sap/approuter#overview)

-   As a container image on Docker Hub, see [https://hub.docker.com/r/sapse/approuter](https://hub.docker.com/r/sapse/approuter)


**Related Information**  


[Developing HTML5 Applications in the Cloud Foundry Environment](developing-html5-applications-in-the-cloud-foundry-environment-11d77aa.md "SAP BTP enables you to access and run HTML5 applications in a cloud environment without the need to maintain your own runtime infrastructure.")

[Setting Up Your Own Application Router](setting-up-your-own-application-router-050d87a.md "This section describes how you can set up your own application router.")

[Resource Files](resource-files-e179c0c.md "The routing configuration for an application is defined in one or more destinations.")

[Application Router Configuration](application-router-configuration-c19f165.md "A file that contains the configuration information used by the application router.")

[Routing Configuration File](routing-configuration-file-c103fb4.md "The routing configuration defined in the xs-app.json file contains the properties used by the application router.")

[Application Routes and Destinations](application-routes-and-destinations-3cc788e.md "The application router is the single point of entry for an application.")

[Environment Variables](environment-variables-ba52705.md "A list of environment variables that can be used to configure the application router.")

[Multitenancy](multitenancy-5310fc3.md)

[Extending the Application Router](extending-the-application-router-9d29c38.md "Configure application-specific extensions for the application router.")

[Extension API of the Application Router](extension-api-of-the-application-router-a36f409.md "A detailed list of the features and functions provided by the application router extension API.")

