<!-- loio01c5f9ba7d6847aaaf069d153b981b51 -->

# Application Router

The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.

The application router is a library that is available on npmjs.com \(NPM\). For more information, see [@sap/approuter](https://www.npmjs.com/package/@sap/approuter#overview).

You can set up an run your own application router or you can use the application router that is managed by SAP \(for more information see [Managed Application Router](Managed_Application_Router_589a239.md)\). We recommend running you own application router only in advanced cases, for example when application router extensibility is required.

-   **[Setting Up Your Own Application Router](Setting_Up_Your_Own_Application_Router_050d87a.md "This section describes how you can set up your own application router.")**  
This section describes how you can set up your own application router.
-   **[Resource Files](Resource_Files_e179c0c.md "The routing configuration for an application is defined in one or more
		destinations.")**  
The routing configuration for an application is defined in one or more destinations.
-   **[Application Router Configuration](Application_Router_Configuration_c19f165.md "A file that contains the configuration information used by the application router. ")**  
A file that contains the configuration information used by the application router.
-   **[Routing Configuration File](Routing_Configuration_File_c103fb4.md "The routing configuration defined in the xs-app.json file contains
    the properties used by the application router. ")**  
The routing configuration defined in the `xs-app.json` file contains the properties used by the application router.
-   **[Headers](Headers_9010419.md "")**  

-   **[Application Routes and Destinations](Application_Routes_and_Destinations_3cc788e.md "The application router is the single point of entry for an application.")**  
The application router is the single point of entry for an application.
-   **[User API Service](User_API_Service_b80abb0.md "The application router exposes a user API that returns the details of the users who are
		logged in to the application. ")**  
The application router exposes a user API that returns the details of the users who are logged in to the application.
-   **[Integration with HTML5 Application Repository](Integration_with_HTML5_Application_Repository_1e0424b.md " The application router is integrated with the HTML5 Application Repository service, to
		retrieve all the static content and routes (xs-app.json) of the HTML5
		applications stored in the repository.")**  
 The application router is integrated with the HTML5 Application Repository service, to retrieve all the static content and routes \(`xs-app.json`\) of the HTML5 applications stored in the repository.
-   **[Integration with Business Services](Integration_with_Business_Services_f6337cd.md "Application router supports integration with Business Services, which are a flavor of
		reuse-services.")**  
Application router supports integration with Business Services, which are a flavor of reuse-services.
-   **[Environment Variables](Environment_Variables_ba52705.md "A list of environment variables that can be used to configure the application
		router.")**  
A list of environment variables that can be used to configure the application router.
-   **[Multitenancy](Multitenancy_5310fc3.md)**  

-   **[Extending the Application Router](Extending_the_Application_Router_9d29c38.md "Configure application-specific extensions for the application router.")**  
Configure application-specific extensions for the application router.
-   **[Extension API of the Application Router](Extension_API_of_the_Application_Router_a36f409.md "A detailed list of the features and functions provided by the application router
		extension API.")**  
A detailed list of the features and functions provided by the application router extension API.

**Related Information**  


[Developing HTML5 Applications in the Cloud Foundry Environment](Developing_HTML5_Applications_in_the_Cloud_Foundry_Environment_11d77aa.md "SAP BTP enables you to access and run HTML5 applications in a cloud environment without the need to maintain your own runtime infrastructure.")

[Setting Up Your Own Application Router](Setting_Up_Your_Own_Application_Router_050d87a.md "This section describes how you can set up your own application router.")

[Resource Files](Resource_Files_e179c0c.md "The routing configuration for an application is defined in one or more destinations.")

[Application Router Configuration](Application_Router_Configuration_c19f165.md "A file that contains the configuration information used by the application router.")

[Routing Configuration File](Routing_Configuration_File_c103fb4.md "The routing configuration defined in the xs-app.json file contains the properties used by the application router.")

[Application Routes and Destinations](Application_Routes_and_Destinations_3cc788e.md "The application router is the single point of entry for an application.")

[Environment Variables](Environment_Variables_ba52705.md "A list of environment variables that can be used to configure the application router.")

[Multitenancy](Multitenancy_5310fc3.md)

[Extending the Application Router](Extending_the_Application_Router_9d29c38.md "Configure application-specific extensions for the application router.")

[Extension API of the Application Router](Extension_API_of_the_Application_Router_a36f409.md "A detailed list of the features and functions provided by the application router extension API.")

