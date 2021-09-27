<!-- loioe3c38ebaefc44523b679e7a0c375bc86 -->

# Developing and Operating SaaS Applications Using Add-Ons

Learn how to develop and operate SaaS applications by using add-ons in the ABAP environment.



<a name="loioe3c38ebaefc44523b679e7a0c375bc86__section_lkq_q35_rnb"/>

## Introduction

The ABAP environment allows you to leverage existing ABAP know-how to create custom add-ons directly in the cloud. This add-on build process is simplified by using the ABAP environment pipeline to orchestrate the build flow. Delivery tools, such as the Add-on Assembly Kit as a Service for the registration and publishing of the add-on as a software product, and deployment tools to carry out test installations and to make the add-on available for productive use, simplify this process. See [Delivery Tools](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#delivery-tools) and [Deployment Tools](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#deployment-tools).

> ### Note:  
> You should only consider using add-on delivery if you intend to offer a Software as a Service \(SaaS\) solution.

Following the add-on build process, you can develop a multitenant application to share the add-on with multiple consumers \(tenants\) simultaneously. See [Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md). The application is registered with the Software-as-a-Service provisioning service \(saas-registry\) to make the application available for subscription to consumers. See [Register the Multitenant Application to the SaaS Provisioning Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3971151ba22e4faa9b245943feecea54.html).

In this context, the [ABAP Solution Service](ABAP_Solution_Service_4370115.md) accounts for the provisioning of new ABAP service instances, including the installation of the add-on, and the creation of tenants whenever required for a new consumer subscription.

The way ABAP service instances and tenants are used for consumer subscription applications can be configured as follows:

-   **Single-tenant enabled**: With each new consumer, a new ABAP service instance is created
-   **Multi-tenant enabled**: For multiple consumers, the same ABAP service instance is used



<a name="loioe3c38ebaefc44523b679e7a0c375bc86__section_mcg_pgt_rnb"/>

## What Is This Guide About?

This guide describes the end-to-end process of developing and offering a SaaS solution using the ABAP environment. The following chapters cover all aspects of this scenario, from the initial setup and development tasks to the final productive use by consumers.

The [Concepts](Concepts_9482e7e.md#loio9482e7eef4634cb993a4ae296b2029fa) chapter gives you an overview about important concepts that are relevant throughout the end-to-end process.

[Develop, Test, Build](Develop,_Test,_Build_3bf575a.md#loio3bf575a3dc5043f895f8bd411d2a86a1) describes the actual development activities. This includes the setup of the required account structure and system landscape, as well as the recommended testing process and subsequent build of the add-on.

[Order and Provide](Order_and_Provide_975bd3e.md#loio975bd3e54cbe4e52af346740658d1a4a) illustrates how a developed add-on can be deployed and made available to consumers. It also shows how consumers order solutions and what steps you, as the provider, need to perform to provision said solution.

[Maintain](Maintain_9721f0f.md#loio9721f0fb92a84e2a95309acf445cb0a9) gives you an overview about the activities involved in maintaining an already commercialized product, as you usually continue to support the add-on, fix bugs, and potentially offer new functionalities as time goes on.

The [Glossary](Glossary_6e251fa.md) contains a list of all the technical terms and phrases used in this scenario.

> ### Tip:  
> To learn how to enable your SaaS application for customers, refer to the detailed step-by-step description in [Enabling SaaS Applications for Customers](Enabling_SaaS_Applications_for_Customers_72b0b11.md).

![](images/E2E_Guide_Introduction_3a1c720.png)

-   [Prepare](Develop,_Test,_Build_3bf575a.md#loio4338854e3133407abb47d3a281dbd1e1)
-   [Develop](Develop,_Test,_Build_3bf575a.md#loio9464e3af139d4e0581cb4e819886b0c8)
-   [Test](Develop,_Test,_Build_3bf575a.md#loio023cf9d301b1479484e70b17cd5cf587)
-   [Build](Develop,_Test,_Build_3bf575a.md#loio25049720bde447e395b3df0bc05e5a50)
-   [Deploy](Order_and_Provide_975bd3e.md#loio4e35eb027f284b7fa6219bc70561fb4e)
-   [Commercialize](Order_and_Provide_975bd3e.md#loio57c19c7c4dfa4c3cbb846c1ac57e2095)
-   [Order and Provide](Order_and_Provide_975bd3e.md#loioa24217a0d6fa434bbce97869dfb70dda)
-   [Order and Provide](Order_and_Provide_975bd3e.md#loioa24217a0d6fa434bbce97869dfb70dda)
-   [Maintain](Maintain_9721f0f.md#loio9721f0fb92a84e2a95309acf445cb0a9)
-   [Maintain](Maintain_9721f0f.md#loio9721f0fb92a84e2a95309acf445cb0a9)
-   [Order and Provide](Order_and_Provide_975bd3e.md#loio975bd3e54cbe4e52af346740658d1a4a)
-   [Develop, Test, Build](Develop,_Test,_Build_3bf575a.md#loio3bf575a3dc5043f895f8bd411d2a86a1)

-   **[Overview](Overview_9640543.md "")**  

-   **[Users and Roles](Users_and_Roles_4b4deee.md "")**  

-   **[Concepts](Concepts_9482e7e.md#loio9482e7eef4634cb993a4ae296b2029fa "Learn more about the system landscape/account model, ABAP
                                environment	 pipeline, as well as versioning
		and branches.")**  
Learn more about the system landscape/account model, ABAP environment pipeline, as well as versioning and branches.
-   **[Glossary](Glossary_6e251fa.md "")**  

-   **[Develop, Test, Build](Develop,_Test,_Build_3bf575a.md#loio3bf575a3dc5043f895f8bd411d2a86a1 "")**  

-   **[Order and Provide](Order_and_Provide_975bd3e.md#loio975bd3e54cbe4e52af346740658d1a4a "After the initial add-on version has been built, you have to deploy and provide it as a
		SaaS solution so that the add-on can be consumed by customers via a subscription in the SAP BTP
                                    cockpit.")**  
After the initial add-on version has been built, you have to deploy and provide it as a SaaS solution so that the add-on can be consumed by customers via a subscription in the SAP BTP cockpit.
-   **[Maintain](Maintain_9721f0f.md#loio9721f0fb92a84e2a95309acf445cb0a9 "")**  


**Related Information**  


[Enabling SaaS Applications for Customers](Enabling_SaaS_Applications_for_Customers_72b0b11.md "You can provide an application to multiple customers as a SaaS solution in the ABAP environment. This process comprises the following steps: the build of an add-on version, its deployment to the cloud with a multitarget application, its ordering and provisioning, and a possible updating process. The following concrete example guides you step by step through this process.")

