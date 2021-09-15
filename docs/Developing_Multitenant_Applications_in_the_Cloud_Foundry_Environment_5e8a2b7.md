<!-- loio5e8a2b74e4f2442b8257c850ed912f48 -->

# Developing Multitenant Applications in the Cloud Foundry Environment

 In the Cloud Foundry environment, you can develop and run multitenant applications, and share them with multiple consumers simultaneously on SAP BTP. 



<a name="loio5e8a2b74e4f2442b8257c850ed912f48__section_rss_gp2_rnb"/>

## What is Multitenancy?

SAP BTP provides a multitenant functionality that allows application providers to own, deploy, and operate tenant-aware applications for multiple consumers, with reduced costs. For example, the application provider can upgrade the application for all your consumers instead of performing each update individually, or can share resources across multiple consumers. The application consumers launch the applications using consumer-specific URLs, and can configure certain application features.

With tenant-aware applications, you can:

-   Separate data securely for each tenant

-   Save resources by sharing them among tenants

-   Update applications efficiently, in a single step


 ![](images/CF_Subscriptions_031f5cb.png) 

Consumers cannot see the data of other consumers; the multitenant application maintains data separation between tenants, and SAP Customer Identity and Access Management \(SAP CIAM\) is kept isolated. Each consumer accesses the multitenant application through a dedicated URL.



<a name="loio5e8a2b74e4f2442b8257c850ed912f48__section_wvn_z4n_s2b"/>

## Multitenancy Roles

The multitenancy concept involves two main user roles:


<table>
<tr>
<td>

Application provider



</td>
<td>

An SAP global account owner that uses SAP BTP to own, build, run, and offer custom-developed applications to its consumers.



</td>
</tr>
<tr>
<td>

Application consumer



</td>
<td>

A consumer of the application provider, such as a department or organizational unit, whose users use the multitenant application.



</td>
</tr>
</table>



<a name="loio5e8a2b74e4f2442b8257c850ed912f48__section_ek5_z42_rnb"/>

## How Does Multitenancy Work for the Application Consumer?

For a consumer to use a tenant-aware application on SAP BTP, the application owner must ensure that each consumer:

1.  Has a dedicated subaccount in the application provider's global account.

2.  Subscribes to the application using either the SAP BTP cockpit, SAP BTP command-line interface, or a dedicated REST API.

    A subscription means that there is a direct relationship between an application provider and the consumer's tenant. The application provider authorizes the consumer tenant to use the application.

3.  Receives a dedicated URL so that its business users can access the application

    As with any application running in SAP BTP, these multitenant applications consume platform resources, such as compute units, structured and unstructured storage, and outgoing bandwidth. The costs for these consumed resources, and those of the application consumer, are billed to the provider of the multitenant application.


For more information about these consumer-related steps, see [Providing Multitenant Applications to Consumers in the Cloud Foundry Environment](Providing_Multitenant_Applications_to_Consumers_in_the_Cloud_Foundry_Environment_7a013f1.md) and [Subscribe to Multitenant Applications Using the Cockpit](Subscribe_to_Multitenant_Applications_Using_the_Cockpit_7a3e396.md).

When a consumer accesses the application, the application environment identifies them by their unique tenant ID. The application distinguishes between requests from different consumer tenants based on the tenant ID, thus ensuring data isolation.

The following figure illustrates the relationship between the application provider's subaccount and consumer subaccounts \(tenants\) in the provider's global account. You deploy the multitenant application to the provider subaccount, and subsequently the consumer subaccounts subscribe to the deployed application. The application uses the tenant-aware `approuter` application and `xsuaa` service \(with the `application` plan\) to authenticate business users of the application at runtime. The application is then registered with the SAP Software-as-a-Service Provisioning service \(technical name: `saas-registry`\) with the `application` plan, which makes the application available for subscription to consumers.

 ![](images/CF_SaaS_-_Multitenancy_Diagram_for_Developer_Guide_ca302c3.png) 



<a name="loio5e8a2b74e4f2442b8257c850ed912f48__section_rlp_1p2_rnb"/>

## Workflow

This is the workflow and requirements for developing and deploying a multitenant application in the Cloud Foundry environment:

1.  [Develop the Multitenant Application](Develop_the_Multitenant_Application_ff54047.md)

    In the Cloud Foundry environment of SAP BTP, you can develop and run multitenant applications that can be accessed by multiple consumers \(tenants\) through a dedicated URL.

2.  [Deploy the Multitenant Application to the Provider Subaccount](Deploy_the_Multitenant_Application_to_the_Provider_Subaccount_2204416.md)

    After you have developed your multitenant application and authorizations, you need to deploy the application in a Cloud Foundry space in the provider's subaccount.

3.  [Configure the approuter Application](Configure_the_approuter_Application_5af9067.md)

    To authenticate business users of the application at runtime, use the tenant-aware approuter application and `xsuaa` service in SAP BTP.

4.  [Bind the Multitenant Application and Application Router to the xsuaa Service Instance](Bind_the_Multitenant_Application_and_Application_Router_to_the_xsuaa_Service_Instance_f56d74d.md)

    Bind your multitenant application and the approuter application to the `xsuaa` service instance, which acts as an OAuth 2.0 client to your application.

5.  [Register the Multitenant Application to the SAP SaaS Provisioning Service](Register_the_Multitenant_Application_to_the_SAP_SaaS_Provisioning_Service_3971151.md)

    To make a multitenant application available for subscription to SaaS consumer tenants, you \(the application provider\) must register the application in the Cloud Foundry environment via the SAP Software-as-a-Service Provisioning service \(`saas-registry`\).

6.  [Providing Multitenant Applications to Consumers in the Cloud Foundry Environment](Providing_Multitenant_Applications_to_Consumers_in_the_Cloud_Foundry_Environment_7a013f1.md)

    Create a subaccount in your global account for each application consumer, subscribe each consumer subaccount to the hosted application deployed in the provider account, and then set up application roles and assign users.


-   **[Develop the Multitenant Application](Develop_the_Multitenant_Application_ff54047.md "In the Cloud
                                Foundry environment of SAP BTP, you can develop and run multitenant applications that can be accessed
		by multiple consumers (tenants) through a dedicated URL.")**  
In the Cloud Foundry environment of SAP BTP, you can develop and run multitenant applications that can be accessed by multiple consumers \(tenants\) through a dedicated URL.
-   **[Deploy the Multitenant Application to the Provider Subaccount](Deploy_the_Multitenant_Application_to_the_Provider_Subaccount_2204416.md "After you have developed your multitenant application and authorizations, you need to deploy the application in a Cloud
                                Foundry space in the provider's subaccount.")**  
After you have developed your multitenant application and authorizations, you need to deploy the application in a Cloud Foundry space in the provider's subaccount.
-   **[Configure the approuter Application](Configure_the_approuter_Application_5af9067.md "To authenticate business users of the application at runtime, use the tenant-aware
			approuter application and SAP Authorization and Trust
                                    Management service (technical
		name: xsuaa) in SAP BTP.")**  
To authenticate business users of the application at runtime, use the tenant-aware `approuter` application and SAP Authorization and Trust Management service \(technical name: `xsuaa`\) in SAP BTP.
-   **[Bind the Multitenant Application and Application Router to the xsuaa Service Instance](Bind_the_Multitenant_Application_and_Application_Router_to_the_xsuaa_Service_Instance_f56d74d.md "Bind your multitenant application and the
			approuter application to the SAP Authorization and Trust
                                    Management service (technical
		name: xsuaa) instance, which acts as an OAuth 2.0
		client to your application.")**  
Bind your multitenant application and the `approuter` application to the SAP Authorization and Trust Management service \(technical name: `xsuaa`\) instance, which acts as an OAuth 2.0 client to your application.
-   **[Register the Multitenant Application to the SAP SaaS Provisioning Service](Register_the_Multitenant_Application_to_the_SAP_SaaS_Provisioning_Service_3971151.md "To make a multitenant application available for subscription to SaaS consumer tenants,
		you (the application provider) must register the application in the Cloud
                                Foundry
		environment via the SAP Software-as-a-Service
                                    Provisioning service (technical
		name: saas-registry).")**  
To make a multitenant application available for subscription to SaaS consumer tenants, you \(the application provider\) must register the application in the Cloud Foundry environment via the SAP Software-as-a-Service Provisioning service \(technical name: `saas-registry`\).
-   **[Providing Multitenant Applications to Consumers in the Cloud Foundry Environment](Providing_Multitenant_Applications_to_Consumers_in_the_Cloud_Foundry_Environment_7a013f1.md "Once you have built a multitenant application in the Cloud
                                Foundry environment using SAP BTP, you can then share the application with
			multiple consumers, such as business units in your organization.")**  
Once you have built a multitenant application in the Cloud Foundry environment using SAP BTP, you can then share the application with multiple consumers, such as business units in your organization.
-   **[Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications](Using_SAP_SaaS_Provisioning_Service_APIs_to_Manage_Multitenant_Applications_ed08c7d.md "You can use the SAP Software-as-a-Service
                                    Provisioning service (technical
		name: saas-registry) APIs to manage your
		multitenant application.")**  
You can use the SAP Software-as-a-Service Provisioning service \(technical name: `saas-registry`\) APIs to manage your multitenant application.
-   **[Using the Subscription Management Dashboard](Using_the_Subscription_Management_Dashboard_434be69.md "Learn how to use
		the
		SAP
		BTP subscription management dashboard to manage your multitenant
		applications through a user interface.")**  
Learn how to use the SAP BTP subscription management dashboard to manage your multitenant applications through a user interface.

**Related Information**  


[Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications](Using_SAP_SaaS_Provisioning_Service_APIs_to_Manage_Multitenant_Applications_ed08c7d.md "You can use the SAP Software-as-a-Service Provisioning service (technical name: saas-registry) APIs to manage your multitenant application.")

[Data Protection and Privacy](Data_Protection_and_Privacy_7e513d3.md "Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries.")

[Using the Subscription Management Dashboard](Using_the_Subscription_Management_Dashboard_434be69.md "Learn how to use the SAP BTP subscription management dashboard to manage your multitenant applications through a user interface.")

