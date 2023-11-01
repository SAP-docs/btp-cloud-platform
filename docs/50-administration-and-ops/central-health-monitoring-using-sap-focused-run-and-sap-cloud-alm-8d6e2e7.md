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

**Metrics for the ABAP Environment in Health Monitoring \(Application Check\)**


<table>
<tr>
<th valign="top">

Area

</th>
<th valign="top">

Metric Label

</th>
<th valign="top">

Technical Metric Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

ABAP Runtime Errors

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

ABAP System

</td>
<td valign="top">

Current Unique Users

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

ABAP System

</td>
<td valign="top">

Locked Business Users

</td>
<td valign="top">

abap\_system\_locked\_bus\_usr\_count

</td>
<td valign="top">

The number of currently locked business users

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

Locked Communication Users

</td>
<td valign="top">

abap\_system\_locked\_com\_usr\_count

</td>
<td valign="top">

The number of currently locked communication users

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

Current Sessions

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

ABAP System

</td>
<td valign="top">

Captured ABAP Statistics Records

</td>
<td valign="top">

abap\_system\_ksr\_captured\_count\_5m

</td>
<td valign="top">

The number of ABAP statistics records that were captured by the *Capture Request Statistics* app during the last 5 minutes

In the *Capture Request Statistics* app, you can select the checkbox *Health Monitoring* for any capture profile that you create. The number of records that is shown in SAP Cloud ALM is the total number of captured ABAP statistics records during the last 5 minutes for profiles with the checkbox *Health Monitoring* selected.

For more information about one use case of this metric, see [Monitoring Expensive Outbound Communication](monitoring-expensive-outbound-communication-6869df1.md).

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

ABAP Compute Units

</td>
<td valign="top">

abap\_acu\_used\_count\_5m \(type: memory\)

</td>
<td valign="top">

Used quota for ABAP system memory during the last 5 minutes

A quota represents the available system size and therefore the maximum allowed consumption of a resource. A resource is measured against the quota independently. For ABAP system resources, the quota is measured in ABAP compute units \(ACUs\).

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

ABAP Compute Units

</td>
<td valign="top">

abap\_acu\_used\_count\_5m \(type: cpu\)

</td>
<td valign="top">

Used quota for ABAP CPU utilization during the last 5 minutes

A quota represents the available system size and therefore the maximum allowed consumption of a resource. A resource is measured against the quota independently. For ABAP system resources, the quota is measured in ABAP compute units \(ACUs\).

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

Expiry of Client Certificates

</td>
<td valign="top">

abap\_system\_client\_cert\_expiry\_d

</td>
<td valign="top">

Expiry of client certificates in days

With this metric, you can monitor whether any client certificates expire that you have uploaded to the ABAP system for the communication with systems or services outside the ABAP system, for example, BTP services. Make sure that your client certificates are valid, so that communication doesn't break off.

If the client certificate expires within 7 days, it's marked red. If it expires within 30 days, it's marked yellow.

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

Expiry of Communication System Certificates

</td>
<td valign="top">

abap\_system\_comsys\_cert\_expiry\_d

</td>
<td valign="top">

Expiry of communication system certificates in days

With this metric, you can monitor whether any communication system certificates uploaded to the ABAP system expire for the communication with systems or services outside the ABAP system. Make sure that your communication system certificates are valid, so that communication doesn't break off.

If the communication system certificate expires within 7 days, it's marked red. If it expires within 30 days, it's marked yellow.

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

Expiry of Trust List Certificates

</td>
<td valign="top">

abap\_system\_trusts\_cert\_expiry\_d

</td>
<td valign="top">

Expiry of trust list certificates in days

With this metric, you can monitor certificates from communication partners that you have added to the certificate trust list in your ABAP system. The metric shows whether any of these trusted certificates expire for the communication with systems or services outside the ABAP system. Make sure that your trusted certificates are valid, so that communication doesn't break off.

If the trusted certificate expires within 7 days, it's marked red. If it expires within 30 days, it's marked yellow.

</td>
</tr>
<tr>
<td valign="top">

ABAP System

</td>
<td valign="top">

Critical Number Range Intervals

</td>
<td valign="top">

abap\_system\_nr\_critical\_interval\_pct

</td>
<td valign="top">

Fill ratio of number range intervals

Only critical number range intervals are shown. When you create a number range interval, you can define the critical remaining fill ratio when a warning is generated.

If a critical number range was reported and is extended, it's reported once again with its now uncritical, good fill ratio to report the fixed state. After that, this number range is dropped from reported number range intervals because it's not critical anymore.

</td>
</tr>
<tr>
<td valign="top">

HANA

</td>
<td valign="top">

HANA Out-of-Memory Events

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

HANA

</td>
<td valign="top">

HANA Compute Units \(CPU\)

</td>
<td valign="top">

hana\_hcu\_used\_count\_5m \(type: cpu\)

</td>
<td valign="top">

Used quota for CPU utilization during the last 5 minutes

A quota represents the available system size and therefore the maximum allowed consumption of a resource. Each resource is measured against the quota independently. For SAP HANA database resources, the quota is measured in HANA compute units \(HCUs\).

</td>
</tr>
<tr>
<td valign="top">

HANA

</td>
<td valign="top">

HANA Compute Units \(Disk\)

</td>
<td valign="top">

hana\_hcu\_used\_count\_5m \(type: disk\)

</td>
<td valign="top">

Used quota for disk space consumption during the last 5 minutes

A quota represents the available system size and therefore the maximum allowed consumption of a resource. Each resource is measured against the quota independently. For SAP HANA database resources, the quota is measured in HANA compute units \(HCUs\).

</td>
</tr>
<tr>
<td valign="top">

HANA

</td>
<td valign="top">

HANA Compute Units \(Memory\)

</td>
<td valign="top">

hana\_hcu\_used\_count\_5m \(type: memory\)

</td>
<td valign="top">

Used quota for memory utilization during the last 5 minutes

A quota represents the available system size and therefore the maximum allowed consumption of a resource. Each resource is measured against the quota independently. For SAP HANA database resources, the quota is measured in HANA compute units \(HCUs\).

</td>
</tr>
<tr>
<td valign="top">

Application Jobs

</td>
<td valign="top">

Average Application Job Delay

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

Application Jobs

</td>
<td valign="top">

Maximum Application Job Delay

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

Application Jobs

</td>
<td valign="top">

Delayed Application Jobs

</td>
<td valign="top">

abap\_system\_appl\_jobs\_delayed\_count\_5m

</td>
<td valign="top">

The number of delayed application jobs during the last 5 minutes.

An application job is counted as delayed when its delay exceeds a certain threshold. The default configuration uses a threshold of 60 seconds.

</td>
</tr>
<tr>
<td valign="top">

Application Jobs

</td>
<td valign="top">

Failed Application Jobs

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

Application Jobs

</td>
<td valign="top">

Running Application Jobs

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

Application Jobs

</td>
<td valign="top">

Finished Application Jobs

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

Application Jobs

</td>
<td valign="top">

Application Logs

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

Application Jobs

</td>
<td valign="top">

Application Logs with Errors

</td>
<td valign="top">

abap\_system\_appl\_logs\_errors\_count\_5m

</td>
<td valign="top">

The number of application logs with errors during the last 5 minutes

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

[Monitoring the Health of the ABAP System in the Cloud](https://blogs.sap.com/2023/05/09/monitoring-the-health-of-the-abap-system-in-the-cloud/) \(blog post on SAP Community\)

