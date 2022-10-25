<!-- loio8d6e2e78f77540d6836cc63eea121966 -->

# Central Health Monitoring Using SAP Focused Run and SAP Cloud ALM

Learn more about how you can monitor the ABAP environment using SAP Focused Run and SAP Cloud ALM.



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_drl_ysr_jpb"/>

## Context

If you run SAP BTP, ABAP environment, as part of a hybrid landscape with on-premise and cloud systems, you might already have a central monitoring and alerting infrastructure in place. For example, the service offering SAP Focused Run is designed specifically for businesses that need high-volume system and application monitoring, alerting, and analytics, especially for hybrid landscapes including on-premise SAP solutions.

In addition, for cloud-centric customers, there's SAP Cloud ALM as an application lifecycle management offering.

![](images/ABAP_Environment_Integration_with_SAP_Focused_Run_0566bc8.png)

If you use SAP Focused Run or SAP Cloud ALM as monitoring and alerting infrastructure, you can integrate monitoring of the ABAP environment into your existing infrastructure. Using the health monitoring in SAP Focused Run or SAP Cloud ALM, you can watch whether your ABAP environment is still up and running and whether any exceptional situations occurred. In addition, you can use the real-user monitoring to monitor requests coming from business users and integration monitoring to watch the communication between integrated systems.



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_mkr_1tr_jpb"/>

## Available Metrics for the ABAP Environment

In the health monitoring of SAP Focused Run and SAP Cloud ALM, the following metrics for application checks are available for the ABAP environment:

<a name="loio8d6e2e78f77540d6836cc63eea121966__table_uhs_cwv_r5b"/>Metrics for the ABAP Environment in Health Monitoring \(Application Check\)


<table>
<tr>
<th valign="top">

Metric Type



</th>
<th valign="top">

Metric Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_core\_dump\_count\_5m



</td>
<td valign="top">

The number of ABAP runtime errors during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

hana\_db\_oom\_event\_count\_5m



</td>
<td valign="top">

The number of out-of-memory events on the SAP HANA index server during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_jobs\_avg\_delay\_s\_5m



</td>
<td valign="top">

Average application job delay in seconds during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_jobs\_max\_delay\_s\_5m



</td>
<td valign="top">

Maximum application job delay in seconds during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_jobs\_delayed\_count\_5m



</td>
<td valign="top">

The number of delayed application jobs during the last 5 minutes.

A job is counted as delayed when its delay exceeds a certain threshold. The default configuration uses a threshold of 60 seconds.



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_jobs\_failed\_count\_5m



</td>
<td valign="top">

The number of failed application jobs during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_jobs\_running\_count



</td>
<td valign="top">

The number of currently running application jobs



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_jobs\_success\_count\_5m



</td>
<td valign="top">

The number of successfully finished application jobs during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_logs\_count



</td>
<td valign="top">

The total number of application logs



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_appl\_logs\_errors\_count\_5m



</td>
<td valign="top">

The number of application logs with errors during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_ksr\_captured\_count\_5m



</td>
<td valign="top">

The number of ABAP statistics records that were captured by the *Capture Request Statistics* app during the last 5 minutes

In the *Capture Request Statistics* app, you can select the checkbox*Health Monitoring* for any capture profile that you create. The number of records that is shown in SAP Cloud ALM is the total number of captured ABAP statistics records for profiles with the checkbox *Health Monitoring* selected.



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_users\_count



</td>
<td valign="top">

The number of current unique users in the ABAP system



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_system\_sessions\_count



</td>
<td valign="top">

The number of current sessions in the ABAP system



</td>
</tr>
<tr>
<td valign="top">

Quota



</td>
<td valign="top">

abap\_acu\_used\_count\_5m \(type: memory\)



</td>
<td valign="top">

Used quota for ABAP system memory during the last 5 minutes

A quota represents the maximum allowed consumption of a resource. For ABAP system resources, it’s measured in ABAP compute units \(ACUs\).



</td>
</tr>
<tr>
<td valign="top">

Quota



</td>
<td valign="top">

hana\_hcu\_used\_count\_5m \(type: cpu\)



</td>
<td valign="top">

Used quota for CPU utilization during the last 5 minutes

A quota represents the maximum allowed consumption of a resource. For SAP HANA database resources, it’s measured in HANA compute units \(HCUs\).



</td>
</tr>
<tr>
<td valign="top">

Quota



</td>
<td valign="top">

hana\_hcu\_used\_count\_5m \(type: disk\)



</td>
<td valign="top">

Used quota for disk space consumption during the last 5 minutes

A quota represents the maximum allowed consumption of a resource. For SAP HANA database resources, it’s measured in HANA compute units \(HCUs\).



</td>
</tr>
<tr>
<td valign="top">

Quota



</td>
<td valign="top">

hana\_hcu\_used\_count\_5m \(type: memory\)



</td>
<td valign="top">

Used quota for memory utilization during the last 5 minutes

A quota represents the maximum allowed consumption of a resource. For SAP HANA database resources, it’s measured in HANA compute units \(HCUs\).



</td>
</tr>
</table>



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_yhb_y2h_3qb"/>

## Setup of ABAP Environment Monitoring with SAP Cloud ALM

For more information about setting up ABAP environment monitoring with SAP Cloud ALM, see the tutorial [Monitor An SAP BTP ABAP Environment Service Using SAP Cloud ALM](https://developers.sap.com/tutorials/abap-environment-monitoring-calm-health-monitoring.html) and the documentation [Setup for SAP BTP ABAP Environment](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/setup-managed-services/setup-scp_abap.html).



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_ezh_bly_2pb"/>

## More Information

[SAP Focused Run on SAP Support Portal](https://support.sap.com/en/alm/sap-focused-run.html)

[Health Monitoring in SAP Focused Run](https://help.sap.com/docs/FRUN/0a4e30bef4ec4b27862bc52a2dc1bed2/61d928f897a44171baa948412a7604d3.html)

[SAP Cloud ALM on SAP Support Portal](https://support.sap.com/en/alm/sap-cloud-alm.html)

[Health Monitoring in SAP Cloud ALM](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/health-monitoring/health-mon-content.html)

