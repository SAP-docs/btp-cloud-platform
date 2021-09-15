<!-- loio40a8f8f6f1724e0ca0fd2a8777f45504 -->

# Development in the Cloud Foundry Environment

Learn more about developing applications on the SAP BTP, Cloud Foundry environment.



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_jms_z5d_53b"/>

## Overview

SAP BTP, Cloud Foundry environment is an open Platform-as-a-Service \(PaaS\) targeted at microservice development and orchestration.

  Develop polyglot applications 
 :   Build on open standards with SAP Java, Node.js, and Python buildpacks or bring your own language with community buildpacks for PHP, Ruby, Go.

   Manage the lifecycle of applications 
 :   Start, stop, scale, and configure distributed cloud applications using standard Cloud Foundry tools, our web-based administration user interface for SAP BTP, and dev-ops capabilities.

   Optimize development and operations 
 :   Use the rich set of SAP BTP services including messaging, persistence, and many other capabilities.

   Use the application programming model 
 :   Use programming languages, libraries, and APIs tailored for full-stack application development.

 

The following graphic is designed to help you find the information you need for your programming purposes. The bottom row represents the tools, frameworks, services, and deployment options recommended by SAP. If you want full flexibility you can also bring your own development tools and languages, as shown in the top row.



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_wqt_z5l_tnb"/>

## Development Options Overview

![](images/Image_Map_Development_Options_Overview_d716bab.png)

-   [Development Languages](Development_Languages_2d0ff22.md)
-   [Developing HTML5 Applications in the Cloud Foundry Environment](Developing_HTML5_Applications_in_the_Cloud_Foundry_Environment_11d77aa.md)
-   [Developing SAP HANA in the Cloud Foundry Environment](Developing_SAP_HANA_in_the_Cloud_Foundry_Environment_14224d7.md#loio14224d75f6c64b499d189e3ebd131ec2)
-   [Deploy Docker Images in the Cloud Foundry Environment](Deploy_Docker_Images_in_the_Cloud_Foundry_Environment_c190ad6.md)
-   [Deploy Business Applications in the Cloud Foundry Environment](Deploy_Business_Applications_in_the_Cloud_Foundry_Environment_4946ea5.md)
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



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_ifw_4vl_tnb"/>

## The Recommended Path

This development approach offers guidance for important development decisions and features proven best practices recommended by SAP. You can follow a model path for application and service development that is based on the Cloud Application Programming Model \(CAP\). When working with CAP, we recommend using Java and Node.js because they receive the highest level of tool support and are well suited for most use cases. This path provides you with a list of key aspects to consider, but the order shown in these steps isn't mandatory. You can adapt the steps as you wish to better fit your use case.



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_skx_qfs_4nb"/>

## Choose Your Own Path

Because of the polyglot nature of the Cloud Foundry environment, you're also free to choose your own approach. You're not forced to use one language exclusively, but can choose between Java, Node.js, and Python. Concerning tools you can either use the Cloud Foundry Command Line Interface \(CF CLI\) or other tools to develop and deploy your application. You're also free to decide if you want to develop and deploy your applications in the multitarget format \(MTA\).

For more information on the supported programming languages, see:

-   [Developing Java in the Cloud Foundry Environment](Developing_Java_in_the_Cloud_Foundry_Environment_a3f9006.md)

-   [Developing Node.js in the Cloud Foundry Environment](Developing_Node.js_in_the_Cloud_Foundry_Environment_3a7a0be.md)

-   [Developing Python in the Cloud Foundry Environment](Developing_Python_in_the_Cloud_Foundry_Environment_acf8f49.md)




If you already have monolithic applications running on SAP BTP and are looking for a way to run them in the Cloud Foundry environment, read our migration best practice guide. See [Migrating from the Neo Environment to the Multi-Cloud Foundation (Cloud Foundry and Kyma)](https://help.sap.com/viewer/b017fc4f944e4eb5b31501b3d1b6a1f0/Cloud/en-US/aae4e0ae1cdf434b908c3c8cf3ea942a.html "Learn why and how to migrate your scenarios on SAP Business Technology Platform (SAP BTP) from the Neo environment to the multi-cloud foundation.") :arrow_upper_right:.

-   **[Best Practices](Best_Practices_0859096.md "Choose the development environment, tools, APIs, and programming model that best suit your needs with recommendations from SAP. ")**  
Choose the development environment, tools, APIs, and programming model that best suit your needs with recommendations from SAP.
-   **[Developing Your First Application](Developing_Your_First_Application_bc8d5c0.md "Follow any of these tutorials to develop your first application on SAP BTP. Choose your
			preferred programming model and technology.")**  
Follow any of these tutorials to develop your first application on SAP BTP. Choose your preferred programming model and technology.
-   **[Developing Applications and Services](Developing_Applications_and_Services_68e2ece.md "Get started with developing applications and services in the Cloud
                                Foundry environment.")**  
Get started with developing applications and services in the Cloud Foundry environment.
-   **[Developing User Interface](Developing_User_Interface_a6ea5f0.md "Get information on user interface development in the SAP BTP, Cloud Foundry
                                    environment.")**  
Get information on user interface development in the SAP BTP, Cloud Foundry environment.
-   **[Consuming APIs](Consuming_APIs_d4cae3e.md "Discover APIs available on SAP BTP.")**  
Discover APIs available on SAP BTP.
-   **[Adding Authentication and Authorization](Adding_Authentication_and_Authorization_419ae2e.md "Developers create authorization information for business users in their environment and deploy this information in an application. They
		make this available to administrators, who complete the authorization setup and assign the authorizations to business users.")**  
Developers create authorization information for business users in their environment and deploy this information in an application. They make this available to administrators, who complete the authorization setup and assign the authorizations to business users.
-   **[Setting Up Database Artifacts](Setting_Up_Database_Artifacts_3cd6954.md "Learn how to set up database artifacts using SAP HANA. ")**  
Learn how to set up database artifacts using SAP HANA.
-   **[Deploying to the Cloud Foundry Environment](Deploying_to_the_Cloud_Foundry_Environment_2a21055.md "Get an overview of available deployment options.")**  
Get an overview of available deployment options.

**Related Information**  


[Cloud Foundry Environment](Cloud_Foundry_Environment_9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18 "The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. It contains the SAP BTP, Cloud Foundry runtime service, which is based on the open-source application platform managed by the Cloud Foundry Foundation.")

[Troubleshooting App Deployment and Health](https://docs.cloudfoundry.org/devguide/deploy-apps/troubleshoot-app-health.html)



