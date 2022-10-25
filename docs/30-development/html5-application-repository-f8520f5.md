<!-- loiof8520f572a6445a7bfaff4a1bbcbe60a -->

# HTML5 Application Repository

HTML5 application repository enables central storage of HTML5 applications' static content on the SAP BTP, Cloud Foundry environment. This service can be consumed from the SAP BTP, Cloud Foundry Runtime and the SAP BTP, Kyma runtime.

HTML5 applications consist of static content such as HTML, CSS, JavaScript, and other files, that run on a browser. For more information, see [Basic Template](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/14fdcc0a9d834090a07435cfef962b01.html) and [openui5-basic-template-app](https://github.com/SAP/openui5-basic-template-app).

HTML5 application repository allows application developers to manage the lifecycle of their HTML5 applications. In runtime, the repository enables the consuming application, typically the application router, to access HTML5 application static content in a secure and efficient manner. For more information, see [Configure Application Router](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/01c5f9ba7d6847aaaf069d153b981b51.html).



<a name="loiof8520f572a6445a7bfaff4a1bbcbe60a__section_ocr_rl1_1cb"/>

## Features

Zero Down-Time Enablement

-   The HTML5 applications are decoupled from the consuming application router. This enables updating the static content of the HTML5 applications without restarting the application router.


Versioning and Authorization

-   Exploration of HTML5 application content by version.

-   Access control that is based on private or public authorization.

    When the HTML5 application is public, the service enables sharing this content with consuming application routers from different spaces.


Availability and Performance

-   During runtime, the HTML5 application content is cached and optimized to provide high performance with minimal network load.

-   The service provides several instances for a runtime to serve a high load of application requests.




<a name="loiof8520f572a6445a7bfaff4a1bbcbe60a__section_jjv_12v_1cb"/>

## Restrictions

-   The size of an application deployed to the repository is limited to 100 MB per service instance of the *app-host* service plan.

-   Since the applications stored in HTML5 application repository can be shared, it is advised not to add personal data to them.




<a name="loiof8520f572a6445a7bfaff4a1bbcbe60a__section_mqn_54b_kdb"/>

## See Also

If you want to learn more about services in the SAP BTP, Cloud Foundry environment, see [Using Services in the Cloud Foundry Environment](using-services-in-the-cloud-foundry-environment-f22029f.md).

