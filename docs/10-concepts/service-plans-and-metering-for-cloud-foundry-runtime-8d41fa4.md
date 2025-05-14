<!-- loio8d41fa40e47b45bf90d38e393a989c4c -->

# Service Plans and Metering for Cloud Foundry Runtime

This page explains the relationship between the service plans in the SAP Discovery Center and those in the SAP BTP cockpit, and provides information to help you understand how the service is billed.





<a name="loio8d41fa40e47b45bf90d38e393a989c4c__service"/>

## Service



### Overview

The diagram below shows how the service plans listed in the [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/cloud-foundry-runtime?region=all&tab=service_plan) correspond to the plans you choose in the SAP BTP cockpit, depending on the commercial model of your enterprise global account. For more information about the commercial models offered by SAP, see [Commercial Models](commercial-models-263d400.md).

![A diagram depicting the relationship between service plans in the SAP Discovery Center, service plans in the SAP BTP cockpit, environment plans in the SAP BTP cockpit, and the metric GB Memory. Consumption-based commercial model, line 1 of 2: Service Plan (SAP Discovery Center) - Standard; Service Plan (SAP BTP Cockpit) - not applicable; Environment Plan (SAP BTP Cockpit) - standard; Metrics - GB Memory; SKU - 8008837. Consumption-based commercial model, line 2 of 2: Service Plan (SAP Discovery Center) - Free; Service Plan (SAP BTP Cockpit) - free (Environment); Environment Plan (SAP BTP Cockpit) - free; Metrics - GB Memory; SKU - 8011138. Subscription-based commercial model, line 1 of 1: Service Plan (SAP Discovery Center) - Standard; Service Plan (SAP BTP Cockpit) - MEMORY, the plan is associated with a standalone service Cloud Foundry Runtime (technical name: APPLICATION_RUNTIME); Environment Plan (SAP BTP Cockpit) - standard; Metrics - GB Memory; SKU - 8008837.](images/SAP_BTP_Cloud_Foundry_Runtime_Commercial_Information_Plans_-_2024_V2_67db7c4.png)



### <sub>Diagram captions: Service plans and environment plans in SAP BTP cockpit \[Show/Hide\]</sub>


<dl>
<dt><b>

Service Plan \(SAP BTP Cockpit\)

</b></dt>
<dd>

The plan that the global account administrator can assign to a subaccount or a directory on the *Entitlements* page by choosing *Edit* \> *Add Service Plans*.  
  
**Screenshot: Assigning a service plan to a subaccount in SAP BTP cockpit \[Show/Hide\]**

> ### Tip:  
> Open image in new tab for the full-screen version.

![A screenshot of the Entitlements screen in the SAP BTP cockpit, showing the assignment of a service plan to a subaccount.](images/English_-_Entitlements_-_SAP_BTP_Cloud_Foundry_Runtime_94337c9.png "Screenshot: Assigning a service plan to a subaccount in
										SAP BTP
									cockpit [Show/Hide]")

For more information about the procedure, see [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/configure-entitlements-and-quotas-for-subaccounts-5ba357b.md) or [Configure Entitlements and Quotas for Directories](../50-administration-and-ops/configure-entitlements-and-quotas-for-directories-37f8871.md).

> ### Note:  
> The greyed out parts of the diagram indicate service plans that are automatically assigned to all subaccounts by default.



</dd><dt><b>

Environment Plan \(SAP BTP Cockpit\)

</b></dt>
<dd>

The plan that the subaccount administrator can select on the *Overview* page of a subaccount when choosing *Enable Cloud Foundry*.  
  
**Screenshot: Selecting an environment plan for the subaccount in SAP BTP cockpit \[Show/Hide\]**

> ### Tip:  
> Open image in new tab for the full-screen version.

![A screenshot of the Overview screen of a subaccount in the SAP BTP cockpit, showing the enablement of an environment plan.](images/English_-_Enable_Cloud_Foundry_-_SAP_BTP_Cloud_Foundry_Runtime_0377151.png "Screenshot: Selecting an environment plan for the subaccount
									in SAP BTP
									cockpit [Show/Hide]")



For more information about the procedure, see [Create Orgs](../50-administration-and-ops/create-orgs-a9b1f54.md).

> ### Note:  
> An environment plan is a service plan associated with an environment. For more information about services and service plans, see [Entitlements and Quotas](entitlements-and-quotas-00aa2c2.md).



</dd>
</dl>



### Service Plans

The tables below provide details about the plans for SAP BTP, Cloud Foundry runtime. They can give you more context for understanding the diagram in the **Overview** section.

**Table 1: Plans for Consumption-Based Commercial Model \[Show/Hide\]**


<table>
<tr>
<th valign="top" align="center">

Service Plan \(SAP Discovery Center\)

</th>
<th valign="top" align="center">

Service \(SAP BTP Cockpit: *Entitlements*\)

</th>
<th valign="top" align="center">

Service Plan \(SAP BTP Cockpit: *Entitlements*\)

</th>
<th valign="top" align="center">

Environment Plan \(SAP BTP Cockpit: *Enable Cloud Foundry*\)

</th>
<th valign="top" align="center">

Explanation

</th>
</tr>
<tr>
<td valign="top">

Standard

</td>
<td valign="top" align="center">

\-

</td>
<td valign="top" align="center">

\-

</td>
<td valign="top">

standard

</td>
<td valign="top">

This is a **paid** plan for productive use. In the consumption-based commercial model, you are charged based on how much runtime memory has been consumed by your applications running in the Cloud Foundry environment. For details, see [Service Specifics](service-plans-and-metering-for-cloud-foundry-runtime-8d41fa4.md#loio8d41fa40e47b45bf90d38e393a989c4c__service_specifics).

> ### Caution:  
> With this plan, you get a technical quota of 200 GB of runtime memory per Cloud Foundry org. This doesn't mean that you can use the runtime memory for free. The technical quota represents a **limit** on how much runtime memory all the spaces in the org can use at any given time. To increase this limit, create a case on the [SAP Support Portal](https://support.sap.com) using the component `BC-NEO-CIS`.

The plan is available for all subaccounts by default and can be enabled by a subaccount administrator.

</td>
</tr>
<tr>
<td valign="top">

Free

</td>
<td valign="top">

Cloud Foundry Environment \(`cloudfoundry`\)

</td>
<td valign="top">

free \(Environment\)

</td>
<td valign="top">

free

</td>
<td valign="top">

This is a **free tier** plan that allows you to try out and evaluate the service. For more information, see [Using Free Service Plans](using-free-service-plans-524e108.md).

With this plan, you get a free quota of runtime memory for your Cloud Foundry org. The amount of such free quotas per global enterprise account is limited.

The plan must be assigned to the subaccount by a global account administrator \(or a directory administrator\), before it can be enabled by a subaccount administrator.

> ### Note:  
> Only community support is available for free tier service plans and these are not subject to SLAs. Use of free tier service plans is subject to additional terms and conditions as provided in the [Business Technology Platform Supplemental Terms and Conditions](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?sort=latest_desc&search=Supplement%20Business%20Technology%20Platform&tag=language%3Aenglish&pdf-asset=c8e624f5-bc7e-0010-bca6-c68f7e60039b&page=1).



</td>
</tr>
<tr>
<td valign="top">

See [SAP Build Code](https://discovery-center.cloud.sap/serviceCatalog/sap-build-code?region=all&tab=service_plan)

</td>
<td valign="top">

Cloud Foundry Environment \(`cloudfoundry`\)

</td>
<td valign="top">

build-code

</td>
<td valign="top">

build-code

</td>
<td valign="top">

This plan is only for using the SAP BTP, Cloud Foundry runtime as part of SAP Build Code. For more information, see [What Is SAP Build Code](https://help.sap.com/docs/build_code/d0d8f5bfc3d640478854e6f4e7c7584a/504854f457cc4fbf9f79136dbc773618.html).

> ### Note:  
> The plan is not depicted on the diagram in the **Overview** section.



</td>
</tr>
</table>

**Table 2: Plans for Subscription-Based Commercial Model \[Show/Hide\]**


<table>
<tr>
<th valign="top" align="center">

Service Plan \(SAP Discovery Center\)

</th>
<th valign="top" align="center">

Service \(SAP BTP Cockpit: *Entitlements*\)

</th>
<th valign="top" align="center">

Service Plan \(SAP BTP Cockpit: *Entitlements*\)

</th>
<th valign="top" align="center">

Environment Plan \(SAP BTP Cockpit: *Enable Cloud Foundry*\)

</th>
<th valign="top" align="center">

Explanation

</th>
</tr>
<tr>
<td valign="top">

Standard

</td>
<td valign="top">

Cloud Foundry Runtime \(`APPLICATION_RUNTIME`\)

</td>
<td valign="top">

MEMORY 

</td>
<td valign="top">

standard

</td>
<td valign="top">

This is a **paid** plan for productive use. In the subscription-based commercial model, you pay for runtime memory quota in advance.

The runtime memory quota purchased with your subscription must be assigned to subaccounts through the service plan MEMORY. This service plan is associated with the service Cloud Foundry Runtime \(`APPLICATION_RUNTIME`\).

The plan **standard** is assigned to all subaccounts by default and can be enabled by a subaccount administrator. The runtime memory quota can be assigned to the subaccount only by a global account administrator \(or a directory administrator\). These steps are independent, but both of them are required to run applications in the Cloud Foundry environment.

</td>
</tr>
<tr>
<td valign="top" align="center">

\-

</td>
<td valign="top">

Cloud Foundry Environment \(`cloudfoundry`\)

</td>
<td valign="top">

build-runtime

</td>
<td valign="top">

build-runtime

</td>
<td valign="top">

This plan is only for using the SAP BTP, Cloud Foundry runtime as part of SAP Build. For more information, see [What Is SAP Build](https://help.sap.com/docs/build-service/build-service-guide/what-is-sap-build) and [Service Plans and Metering](https://help.sap.com/docs/build-service/build-service-guide/service-plans-and-metering).

> ### Note:  
> The plan is not depicted on the diagram in the **Overview** section.



</td>
</tr>
<tr>
<td valign="top">

See [SAP Build Code](https://discovery-center.cloud.sap/serviceCatalog/sap-build-code?region=all&tab=service_plan)

</td>
<td valign="top">

Cloud Foundry Environment \(`cloudfoundry`\)

</td>
<td valign="top">

build-code

</td>
<td valign="top">

build-code

</td>
<td valign="top">

This plan is only for using the SAP BTP, Cloud Foundry runtime as part of SAP Build Code. For more information, see [What Is SAP Build Code](https://help.sap.com/docs/build_code/d0d8f5bfc3d640478854e6f4e7c7584a/504854f457cc4fbf9f79136dbc773618.html).

> ### Note:  
> The plan is not depicted on the diagram in the **Overview** section.



</td>
</tr>
</table>



<a name="loio8d41fa40e47b45bf90d38e393a989c4c__metrics"/>

## Metrics

The table below provides details about the metrics for SAP BTP, Cloud Foundry runtime. It includes the names of services, with which the metrics are associated on the pages *Usage* \(accessed from the global account level\) and *Usage Analytics* \(accessed from the subaccount level\) in the SAP BTP cockpit.


<table>
<tr>
<th valign="top" align="center">

Metric

</th>
<th valign="top" align="center">

Service \(SAP BTP Cockpit\)

</th>
<th valign="top" align="center">

Metric \(SAP BTP Cockpit\)

</th>
<th valign="top" align="center">

Definition

</th>
<th valign="top" align="center">

Additional Information

</th>
</tr>
<tr>
<td valign="top">

GB Memory

</td>
<td valign="top">

Cloud Foundry Runtime

</td>
<td valign="top">

GB Memory

</td>
<td valign="top" rowspan="3">

Temporary memory bank where computers store data that needs to be retrieved and processed quickly.

The memory represents the size of the data that can be processed and CPU represents the speed at which the data can be retrieved.

</td>
<td valign="top">

For billing purposes, the GB Memory metric for the Cloud Foundry Runtime service is calculated as the total hourly usage of Cloud Foundry runtime memory across all spaces in the global account over a calendar month, divided by 730 hours and rounded up to the next full GB. For an example of such calculation, see [Consumption Monitoring](https://help.sap.com/docs/cf-runtime/cloud-foundry-runtime/monitoring-and-troubleshooting?version=Cloud#consumption-monitoring).

> ### Note:  
> In the Cloud Foundry environment, applications get a guaranteed CPU share of ¼ core per GB of runtime memory quota reserved for an application instance. For more information, see [SAP BTP-Specific Configurations](sap-btp-specific-configurations-9809fa4.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Capacity Units

</td>
<td valign="top">

SAP Build

</td>
<td valign="top">

GB Memory

</td>
<td valign="top">

In SAP Build, the usage of SAP BTP, Cloud Foundry runtime is measured in capacity units. The GB Memory metric for the SAP Build service in the SAP BTP cockpit is intended only for monitoring the approximate usage of SAP BTP, Cloud Foundry runtime in GB when it's consumed as part of SAP Build. For more information, see [What Is SAP Build](https://help.sap.com/docs/build-service/build-service-guide/what-is-sap-build?version=Cloud).

> ### Note:  
> The metric is not depicted on the diagram in [Service](service-plans-and-metering-for-cloud-foundry-runtime-8d41fa4.md#loio8d41fa40e47b45bf90d38e393a989c4c__service).



</td>
</tr>
<tr>
<td valign="top">

SAP Build Code

</td>
<td valign="top">

CF Runtime

</td>
<td valign="top">

In SAP Build Code, the usage of SAP BTP, Cloud Foundry runtime is measured in capacity units. The CF Runtime metric for the SAP Build Code service in the SAP BTP cockpit is intended only for monitoring the approximate usage of SAP BTP, Cloud Foundry runtime in GB when it's consumed as part of SAP Build Code. For more information, see [What Is SAP Build Code](https://help.sap.com/docs/build_code/d0d8f5bfc3d640478854e6f4e7c7584a/504854f457cc4fbf9f79136dbc773618.html) and [SAP Build Code Capacity Unit Calculator](https://build-code-calculator.cfapps.eu10-004.hana.ondemand.com/).

> ### Note:  
> The metric is not depicted on the diagram in [Service](service-plans-and-metering-for-cloud-foundry-runtime-8d41fa4.md#loio8d41fa40e47b45bf90d38e393a989c4c__service).



</td>
</tr>
</table>



<a name="loio8d41fa40e47b45bf90d38e393a989c4c__service_specifics"/>

## Service Specifics

In the context of SAP BTP, Cloud Foundry runtime, the terms **consumption** \(or **consume**\) and **usage** \(or **use**\) refer to the runtime memory quota **reserved** by the platform for each application instance. This quota serves as the basis for calculating the billable consumption, as explained in [Consumption Monitoring](https://help.sap.com/docs/cf-runtime/cloud-foundry-runtime/monitoring-and-troubleshooting?version=Cloud#consumption-monitoring).

> ### Caution:  
> From a billing standpoint, it doesn't matter how much of the reserved runtime memory quota is utilized when the application is running. Billable consumption is calculated based on the full amount of runtime memory reserved, regardless of how much runtime memory actually gets utilized.

> ### Note:  
> If an application is stopped, it doesn't reserve any runtime memory and, therefore, doesn't contribute to runtime memory consumption.

There are two application settings that define how much runtime memory an application uses at any given time:

-   Runtime memory quota reserved for each application instance \(default: 1024 MB\)

-   Number of running application instances \(default: 1\)


> ### Note:  
> The total amount of runtime memory that an application uses when all of its instances are running is displayed on the application's *Overview* page under *All Instances Memory*.

You can specify custom values for these settings when deploying an application in the Cloud Foundry environment. You can also change them for an application that has already been deployed without having to redeploy it.



### How to set runtime memory quota and number of instances when deploying applications

-   **Option 1:** Create a manifest YAML file and specify the following application attributes:

    -   <code><a href="https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html#memory">memory</a></code>: runtime memory quota per application instance
    -   <code><a href="https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html#instances">instances</a></code>: number of application instances

    For more information about the manifest formatting, see [https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html).

    You can then deploy your application with the manifest in one of two ways:

    -   Using the SAP BTP cockpit: [Deploy an Application](../50-administration-and-ops/deploy-an-application-09fdb9b.md)
    -   Using the Cloud Foundry CLI: [https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html)

-   **Option 2:** In the SAP BTP cockpit, choose *Deploy Application*, select *Custom Settings* and specify the following:

    -   *Memory per Instance \(MB\)*: runtime memory quota per application instance
    -   *Number of Instances*: number of application instances

    For more information about the procedure, see [Deploy an Application](../50-administration-and-ops/deploy-an-application-09fdb9b.md).

-   **Option 3:** In the Cloud Foundry CLI, use the command `cf push` with the following flags:

    -   `-m`: runtime memory quota per application instance
    -   `-i`: number of application instances

    For more information about the procedure, see [https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html\#custom-push](https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html#custom-push).




### How to change runtime memory quota and number of instances for already deployed applications

-   **Option 1:** In the SAP BTP cockpit, on the *Overview* page of the application you can:

    -   Change the runtime memory quota per application instance under *Change Instance Details* \> *Memory per Instance \(MB\)*
    -   Change the number of application instances as described in [Manage Application Instances](../50-administration-and-ops/manage-application-instances-75836f1.md)

-   **Option 2:** In the Cloud Foundry CLI, you can use the command `cf scale` with the following flags:

    -   `-m`: change the runtime memory quota per application instance
    -   `-i`: change the number of application instances

    For more information about the procedure, see [https://docs.cloudfoundry.org/devguide/deploy-apps/cf-scale.html](https://docs.cloudfoundry.org/devguide/deploy-apps/cf-scale.html).


You can use the **Application Autoscaler** to automatically increase or decrease the number of application instances based on the policies you have defined. For more information, see [What Is Application Autoscaler](https://help.sap.com/viewer/7472b7d13d5d4862b2b06a730a2df086/Cloud/en-US/45341f37cf6e4738a4b7cd20f18350de.html "Automatically scale your applications to meet their dynamic resource needs.") :arrow_upper_right:.

> ### Tip:  
> For tips on how to optimize the consumption of runtime memory, see the blog post [Optimise your SAP BTP, Cloud Foundry runtime costs](https://blogs.sap.com/2022/02/11/optimise-your-sap-btp-cloud-foundry-runtime-costs/). Note that while the general principles outlined in the blog post still apply, some of the UI texts and parameter names may have changed.



<a name="loio8d41fa40e47b45bf90d38e393a989c4c__supplemental_terms_and_conditions"/>

## Supplemental Terms and Conditions

For more information, see the section **SAP BTP, Cloud Foundry Runtime** in the [SAP Business Technology Platform Service Description Guide](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?%3Bpage=1&%3Bpdf-asset=82ce6fed-917e-0010-bca6-c68f7e60039b&%3Btag=language%3Aenglish&search=SAP%20Business%20Technology%20Platform%20Service%20Description%20Guide&sort=latest_desc&pdf-asset=9a48fd54-c97e-0010-bca6-c68f7e60039b&page=7).



<a name="loio8d41fa40e47b45bf90d38e393a989c4c__glossary"/>

## Glossary

[Commercial Information Glossary](https://help.sap.com/docs/help/5d771150f8f547c6bc604c7d674cf30d/7014f9db099148f1897c1bda5db21f39.html)

