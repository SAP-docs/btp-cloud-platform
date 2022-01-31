<!-- loio8d6e2e78f77540d6836cc63eea121966 -->

# Integration into Central Monitoring and Alerting

Learn more about how you can monitor the ABAP environment using SAP Focused Run.



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_drl_ysr_jpb"/>

## Context

If you run SAP BTP, ABAP environment, as part of a hybrid landscape with on-premise and cloud systems, you might already have a central monitoring and alerting infrastructure in place. For example, the service offering SAP Focused Run is designed specifically for businesses that need high-volume system and application monitoring, alerting, and analytics, especially for hybrid landscapes including on-premise SAP solutions. For cloud-centric customers, there's SAP Cloud ALM as an application lifecycle management offering.

![](images/ABAP_Environment_Integration_with_SAP_Focused_Run_0566bc8.png)

If you use SAP Focused Run or SAP Cloud ALM as monitoring and alerting infrastructure, you can integrate monitoring of the ABAP environment into your existing infrastructure. Using the health monitoring in SAP Focused Run or SAP Cloud ALM, you can also watch whether your ABAP environment is still up and running and whether any exceptional situations occurred. In addition, you can use the real-user monitoring to monitor requests coming from business users and integration monitoring to watch the communication between integrated systems.



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_mkr_1tr_jpb"/>

## Available Metrics for the ABAP Environment

In the health monitoring of SAP Focused Run and SAP Cloud ALM, the following metrics for application checks are available for the ABAP environment:

<a name="loio8d6e2e78f77540d6836cc63eea121966__table_zy2_3tr_jpb"/>Metrics for the ABAP Environment in Health Monitoring \(Application Check\)


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

The number of core short dumps during the last 5 minutes



</td>
</tr>
<tr>
<td valign="top">

Performance



</td>
<td valign="top">

abap\_core\_fail\_appl\_jobs\_ratio\_5m



</td>
<td valign="top">

The ratio of failed application jobs during the last 5 minutes



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

Quota



</td>
<td valign="top">

abap\_acu\_used\_count\_5m \(type: memory\)



</td>
<td valign="top">

Used quota of ABAP system memory \(in ABAP computing units\)



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

Used quota of CPU utilization for the SAP HANA database \(in HANA computing units\)



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

Used quota of disk space for the SAP HANA database \(in HANA computing units\)



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

Used quota of memory utilization for the SAP HANA database \(in HANA computing units\)



</td>
</tr>
</table>



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_gh4_v2h_3qb"/>

## Setup of ABAP Enviroment Monitoring with SAP Focused Run

For more information about setting up ABAP environment monitoring with SAP Focused Run, see the tutorial [Monitor an SAP BTP ABAP Environment Service Using SAP Focused Run \(FRUN\)](https://developers.sap.com/tutorials/abap-environment-monitoring-frun-healthmonitoring.html).



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_yhb_y2h_3qb"/>

## Setup of ABAP Enviroment Monitoring with SAP Cloud ALM

For more information about setting up ABAP enviroment monitoring with SAP Cloud ALM, see [Setup for SAP BTP ABAP Enviroment](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/setup-managed-services/setup-scp_abap.html).



<a name="loio8d6e2e78f77540d6836cc63eea121966__section_ezh_bly_2pb"/>

## More Information

[SAP Focused Run on SAP Support Portal](https://support.sap.com/en/alm/sap-focused-run.html)

[Health Monitoring in SAP Focused Run](https://help.sap.com/viewer/0a4e30bef4ec4b27862bc52a2dc1bed2/latest/en-US/61d928f897a44171baa948412a7604d3.html)

[SAP Cloud ALM on SAP Support Portal](https://support.sap.com/en/alm/sap-cloud-alm.html)

