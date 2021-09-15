<!-- loio9ae3a7addcbf43d5b6568482e00506d5 -->

# Security and Data Privacy Configuration

This section provides information about security and data privacy.

-   Identity Provider and Identity Management

    You can use the User Account and Authentication \(UAA\) server for user authentication. In Cloud Foundry, a service is created for this configuration. By using the standard service binding mechanism, the content of this configuration is available in the `VCAP_SERVICES` environment variable.

    As an alternative to the User Account and Authentication \(UAA\) service , you can also use the Identity Authentication service of the SAP Cloud Identity Services for authentication.

-   Authorization Configuration

    To obtain the access token to authorize API requests, the client credentials authorization flow is used.

-   Data Protection and Data Privacy

    The HTML5 application repository service applies the legally required data protection and privacy measures to data that is stored on behalf of customers. These measures include, for example, the need to know principle during support processes, or data isolation between spaces.

    The HTML5 application repository runtime is a microservice responsible for providing read access to HTML5 applications during runtime. When the HTML5 application is public, the service enables sharing this content with consuming application routers from different spaces.


> ### Note:  
> The HTML5 application repository service does not provide the technical capabilities to support the collection, processing, and storage of personal data. The file names used for deploying the HTML5 applications are not intended for personal data.

-   **[Configure the Credential Type for HTML5 Application Repository Service Instances](Configure_the_Credential_Type_for_HTML5_Application_Repository_Service_Instances_d63930f.md "")**  


