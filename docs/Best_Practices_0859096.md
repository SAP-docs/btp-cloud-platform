<!-- loio0859096d340b45dfb39417a01870ad95 -->

# Best Practices

Choose the development environment, tools, APIs, and programming model that best suit your needs with recommendations from SAP.

Navigating the large portfolio of solutions, services, tools, and frameworks can be difficult. That's why we want to provide you with recommendations based on our years of experience in helping customers achieve their goals. The best practices listed here are targeted at developers. If you're looking for recommendations on general development planning and setting up SAP BTP, see [Best Practices for SAP BTP](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/9f2bb927464e4d1ba3d13b2d79ca9bd1.html "This document helps you plan and set up your landscape and your lifecycle management for running applications on SAP Business Technology Platform (SAP BTP). It contains best practices and recommendations for planning development projects – from setting up the correct organizational structure to creating an account and security model, to developing and operating applications.") :arrow_upper_right:. If you're interested in extending existing applications, see [Extensions](Extensions_08b1eff.md).

The following graphic offers an overview of the most important considerations to take when starting development on SAP BTP for the Cloud Foundry environment. The steps are recommendations, you're free to complete them in a different order if you feel it suits your needs better.



<a name="loio0859096d340b45dfb39417a01870ad95__section_iml_hwp_vnb"/>

## Development Options

![](images/Image_Map_Best_Practives_Overview_a356b5a.png)

-   [Developing Applications and Services](Developing_Applications_and_Services_68e2ece.md)
-   [Developing User Interface](Developing_User_Interface_a6ea5f0.md)
-   [Consuming APIs](Consuming_APIs_d4cae3e.md)
-   [Adding Authentication and Authorization](Adding_Authentication_and_Authorization_419ae2e.md)
-   [Setting Up Database Artifacts](Setting_Up_Database_Artifacts_3cd6954.md)
-   [Deploying to the Cloud Foundry Environment](Deploying_to_the_Cloud_Foundry_Environment_2a21055.md)
-   [Developing with the SAP Cloud Application Programming Model](Developing_with_the_SAP_Cloud_Application_Programming_Model_00823f9.md)
-   [SAP Business Application Studio](SAP_Business_Application_Studio_c736960.md)
-   [Developing SAPUI5](Developing_SAPUI5_839cb81.md)
-   [https://api.sap.com/](https://api.sap.com/)
-   [Protecting Your Application](Protecting_Your_Application_7c5c565.md)
-   [SAP HANA Cloud](Developing_SAP_HANA_in_the_Cloud_Foundry_Environment_14224d7.md#loioa697b1b1b5ad4b598378ff0fa091fa35)
-   [Continuous Integration and Delivery](Continuous_Integration_and_Delivery_fdead30.md#loiofdead30953d24c0ca75768e2c3bcdd2c)
-   [Multitarget Applications in the Cloud Foundry Environment](Multitarget_Applications_in_the_Cloud_Foundry_Environment_d04fc0e.md)



<a name="loio0859096d340b45dfb39417a01870ad95__section_t1s_4sr_4nb"/>

## The Recommended Path: The SAP Cloud Application Programming Model

We recommend using the SAP Cloud Application Programming Model \(CAP\) for full-stack development. CAP is a framework of languages, libraries, APIs, and tools that guide developers along a proven path of best practices. It was designed with a business domain focus in mind, relying on common patterns and reuse models for programming. With CAP you can develop multitarget applications or automate tasks such as authorization, integration, or localization to make applications and services easier to fix and maintain. CAP is compatible with any development environment, but we recommend SAP Business Application Studio.

For more information, see [Developing with the SAP Cloud Application Programming Model](Developing_with_the_SAP_Cloud_Application_Programming_Model_00823f9.md) and [SAP Business Application Studio](https://help.sap.com/viewer/product/SAP%20Business%20Application%20Studio/Cloud/en-US).



<a name="loio0859096d340b45dfb39417a01870ad95__section_uxs_rvm_pnb"/>

## Multitarget Applications

One of the challenges of programming in a cloud environment is the deployment and management of applications consisting of multiple, interdependent components. The agility, flexibility, and resilience of cloud applications brings with it an increased complexity. For example, your application could be targeted at multiple runtimes or consist of interconnected modules created in different tools and programming languages.

To reduce this complexity, we recommend programming multitarget applications \(MTA\). That means packaging all the components of your application into a single archive file. Doing so makes managing the application's lifecycle easier and enables you to automate processes, for example through the Continuous Integration and Delivery service.

For more information, see [Multitarget Applications in the Cloud Foundry Environment](Multitarget_Applications_in_the_Cloud_Foundry_Environment_d04fc0e.md).



<a name="loio0859096d340b45dfb39417a01870ad95__section_gtq_h24_ppb"/>

## SAP Alert Notification Service

Applications running in the Cloud Foundry environment are constantly monitored through health checks. If an application doesn't respond, for example because it crashed, it fails the health check and is automatically restarted. Because the system restarts applications quickly to avoid major disruptions, it can be difficult to identify underlying problems. For more information about configuring Health Checks, see [https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html](https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html)

To support the smooth operation of your applications and services, we recommend using the SAP Alert Notification Service. Using a standardized environment-agnostic model, the service collects any update from the application checks as well as crucial technical information from other services on SAP BTP. It also handles custom scenarios that only occur in your specific application and environment. Each piece of information is translated into a common event model.

You can subscribe to events that are of interest to you and use a delivery channel of your choice, for example email or a custom webhook allowing you to send events to any REST API endpoint in the public internet. SAP Alert Notification Service also natively supports integration with external systems, such as Slack, Microsoft Teams, VictorOps, ServiceNow. For more information on events, see [SAP Alert Notification Service Events](https://help.sap.com/viewer/5967a369d4b74f7a9c2b91f5df8e6ab6/Cloud/en-US/eaaa37e6ff62486ebb849507dc33abc6.html "") :arrow_upper_right:.

**Related Information**  


[What Is SAP Alert Notification Service for SAP BTP](https://help.sap.com/viewer/5967a369d4b74f7a9c2b91f5df8e6ab6/Cloud/en-US/086361cb02fb467993acd6f9515607d4.html "") :arrow_upper_right:

