<!-- loio11d77aa154f64c2e83cc9652a78bb985 -->

# Developing HTML5 Applications in the Cloud Foundry Environment

SAP BTP enables you to access and run HTML5 applications in a cloud environment without the need to maintain your own runtime infrastructure.

HTML5 applications consist of static content that runs on a browser. Then you develop your applications - either in SAP Business Application Studio, or in your own IDE \(integrated development environment\) - and deploy them to the [HTML5 application repository](html5-application-repository-f8520f5.md).

Depending on your backed application setup, you either configure the destinations during development, or define them after deploying the application. Finally, to consume the applications, you can create a site in SAP Launchpad, build the URL, and define custom domains.

On the Cloud Foundry environment of SAP BTP you can run an application that was uploaded to HTML5 application repository using one of the following options:

-   Use the application router that is managed by SAP.

    For more information, see [Managed Application Router](managed-application-router-589a239.md).

-   Set up and maintain your own application router in your own space.

    For more information, see [Application Router](application-router-01c5f9b.md).


Both options allow you to serve static content from HTML5 application repository, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information. However, the [managed application router](managed-application-router-589a239.md) brings many benefits, such as:

-   Simplify and speed up your development and deployment experience

-   Save resources by running a serverless HTML5 application, which doesn’t require any application runtime

-   Lower maintenance efforts by leveraging the most up-to-date routing capabilities

-   Meet the changing demand for HTML5 applications by automatically adjusting the service to maintain consistent and predictable performance


Therefore, we recommend running your own [application router](application-router-01c5f9b.md) only in advanced cases, for example when application router extensibility is required.

**Related Information**  


[HTML5 Application Repository](html5-application-repository-f8520f5.md "HTML5 application repository enables central storage of HTML5 applications' static content on the SAP BTP, Cloud Foundry environment. This service can be consumed from the SAP BTP, Cloud Foundry Runtime and the SAP BTP, Kyma runtime.")

[Application Router](application-router-01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Managed Application Router](managed-application-router-589a239.md "")

