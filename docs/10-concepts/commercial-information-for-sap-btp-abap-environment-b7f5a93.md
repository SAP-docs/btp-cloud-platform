<!-- loiob7f5a93ce3804963ab7fd547f3c4fdf9 -->

# Commercial Information for SAP BTP ABAP environment

This page explains the relationship between the service plans of the SAP Discovery Center and the service plans of the SAP BTP cockpit and provides information to help you understand how the service is billed.



<a name="loiob7f5a93ce3804963ab7fd547f3c4fdf9__section_gwp_yyy_5zb"/>

## Service



### Overview

![Image of Consumption-Based Models for SAP BTP ABAP environment. It shows the Free and Standard service plans containing the Hours of Runtime Memory in 16 GB blocks for the Free plan, and Hours of Persistent and Runtime Memory in 16 GB blocks for the Standard plan. It also shows the deprecated plan called 16 GB Runtime and 64 GB Persistence.](images/Commercial_Info_Page_Updated_e08278d.png)[**Discovery Center: SAP BTP ABAP environment**](https://discovery-center.cloud.sap/serviceCatalog/abap-environment?tab=service_plan&region=all)

> ### Note:  
> For more information about consumption-based models, please check [What is the Consumption-Based Commercial Model?](https://help.sap.com/docs/btp/sap-business-technology-platform/what-is-consumption-based-commercial-model?version=Cloud)



### SAP BTP Cockpit: Service Plans


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Service Plan

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

free

</td>
<td valign="top">

Free

</td>
<td valign="top">

Allows you to create small proof-of-concept development projects. Also can be used for the piloting of a remote ABAP test cockpit scenario against on-premise systems in the Custom Code Migration app. The instance will be stopped each night automatically and needs to be started again via the Landscape Portal. Only community support is available for free tier service plans and these are not subject to SLAs.

</td>
</tr>
<tr>
<td valign="top">

standard

</td>
<td valign="top">

Standard

</td>
<td valign="top">

Allows you to create projects for development, test, and productive ABAP systems. The minimum system size is 2 HANA Compute Units and 1 ABAP Compute Unit.

It is mandatory to assign a combination of three entitlement service plans: ABAP Compute Unit, HANA Compute Unit, and either the Free, Standard, or SaaS OEM plan.

</td>
</tr>
<tr>
<td valign="top">

abap\_compute\_unit

</td>
<td valign="top">

Standard

</td>
<td valign="top">

Allows you to configure runtime memory, which refers to volatile memory used during the execution of applications. This memory provides fast read and write access but loses all data when the system is restarted or shut down. The metric measures the amount of runtime memory used in 16 GB blocks on an hourly basis.

It is mandatory to assign a combination of three entitlement service plans: ABAP Compute Unit, HANA Compute Unit, and either the Free, Standard, or SaaS OEM plan.

</td>
</tr>
<tr>
<td valign="top">

hana\_compute\_unit

</td>
<td valign="top">

Standard

</td>
<td valign="top">

Allows you to configure persistent memory, which refers to storage that retains data even after the system is restarted or shut down. The metric measures the amount of persistent storage used in 16 GB blocks on an hourly basis.

It is mandatory to assign a combination of three entitlement service plans: ABAP Compute Unit, HANA Compute Unit, and either the Free, Standard, or SaaS OEM plan.

</td>
</tr>
<tr>
<td valign="top">

saas\_oem

</td>
<td valign="top">

SaaS OEM

</td>
<td valign="top">

Allows you to create projects for ABAP systems to run multitenancy SaaS applications. The minimum system size is 2 HANA Compute Units and 1 ABAP Compute Unit.

It is mandatory to assign a combination of three entitlement service plans: ABAP Compute Unit, HANA Compute Unit, and either the Free, Standard, or SaaS OEM plan.

</td>
</tr>
<tr>
<td valign="top">

16\_abap\_64\_db \(Deprecated\)

</td>
<td valign="top">

16 GB Runtime and 64 GB Persistence \(Deprecated\)

</td>
<td valign="top">

This ABAP runtime service plan provides a 16 GB ABAP runtime with a 64 GB database. No additional sizing is possible.

This service plan is deprecated. Please change the service plan to “standard”.

</td>
</tr>
</table>



<a name="loiob7f5a93ce3804963ab7fd547f3c4fdf9__section_x43_x1z_5zb"/>

## Metrics


<table>
<tr>
<th valign="top">

Metric

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

Memory

</td>
<td valign="top">

Temporary memory bank where computers store data that needs to be retrieve and processed quickly.

The memory represents the size of the data that can be processed , and CPU represents the speed at which the data can be retrieved.

</td>
</tr>
</table>



<a name="loiob7f5a93ce3804963ab7fd547f3c4fdf9__section_mjy_gbz_5zb"/>

## Supplemental Terms and Conditions

For more information, see the [SAP Business Technology Platform Service Description Guide](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?sort=latest_desc&tag=language%3Aenglish&pdf-asset=82ce6fed-917e-0010-bca6-c68f7e60039b&page=1).

