<!-- loioe3ac4f7c25a3442ca585950095eec599 -->

# Resilience, High Availability, and Disaster Recovery

SAP has a number of processes in place to support resilience in SAP BTP, and provides different offerings so that you can support the high availability of your applications.



<a name="loioe3ac4f7c25a3442ca585950095eec599__section_pxk_bqk_ylb"/>

## How SAP Provides Resilience

SAP applies resilience principles when developing, updating, and deploying our SAP BTP applications and services.

SAP BTP provides resilience through the following:


<table>
<tr>
<th valign="top">

Processes and Offerings

</th>
<th valign="top">

Description

</th>
<th valign="top">

Regional Availability

</th>
</tr>
<tr>
<td valign="top">

**Availability Zones** 

</td>
<td valign="top">

To achieve better fault-tolerance in the Cloud Foundry environment, we deploy our services across multiple AZs, which improves the availability of a service if there are issues with the infrastructure of one AZ. For more information, see [Availability Zones in the Cloud Foundry Environment](cloud-foundry-environment-9c7092c.md#loiob6a7e11c3a58416a9ab1175bba17193a).

</td>
<td valign="top">

All regions that support the Cloud Foundry runtime. See [Regions and API Endpoints Available for the Cloud Foundry Environment](regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md).

</td>
</tr>
<tr>
<td valign="top">

**Backups in Kyma runtime** 

</td>
<td valign="top">

Kyma runtime relies on managed Kubernetes clusters for periodic backups of Kubernetes objects. For more information, see [Kyma Environment Backup](../50-administration-and-ops/kyma-environment-backup-ab959cf.md).

</td>
<td valign="top">

All regions that support the Kyma runtime. See [Regions for the Kyma Environment](regions-for-the-kyma-environment-557ec3a.md).

</td>
</tr>
<tr>
<td valign="top">

**Backup and Recovery for SAP HANA Cloud** 

</td>
<td valign="top">

If you use SAP HANA Cloud, your SAP HANA Cloud instances are continually backed up to safeguard your database and ensure that it can be recovered speedily. For more information, see [Backup and Recovery](https://help.sap.com/viewer/db19c7071e5f4101837e23f06e576495/cloud/en-US/89d71f01daca4ecaaa069d6a060167f5.html).

</td>
<td valign="top">

All regions where SAP HANA Cloud is available. See [Availability of SAP HANA Cloud](https://help.sap.com/doc/aa1ccd10da6c4337aa737df2ead1855b/Cloud/en-US/3b642f68227b4b1398d2ce1a5351389a.html?scp-name=SAP%20HANA%20Cloud).

</td>
</tr>
<tr>
<td valign="top">

**Disaster Recovery** 

</td>
<td valign="top">

The SAP BTP Disaster Recovery \(DR\) Plan is part of the overall SAP BTP Business Continuity Plan, which includes crisis management and process continuity activities that are triggered by a declared disaster. For more information, see [Disaster Recovery as Part of the Business Continuity Plan](resilience-high-availability-and-disaster-recovery-e3ac4f7.md#loio001180644f8a428bb422cd41caebb95f).

</td>
<td valign="top">

All regions.

</td>
</tr>
</table>



<a name="loioe3ac4f7c25a3442ca585950095eec599__section_n1c_dqk_ylb"/>

## Best Practices for Resilient Applications

In addition to the services offered by SAP BTP, you can follow our best practices for developing and deploying applications, which allow you to make your application running on SAP BTP stable and highly available.

-   **Develop Resilient Applications**

    When developing your applications, apply the principles and patterns of resilient software design that fit your use case. For more information, see [Developing Resilient Apps on SAP BTP](https://help.sap.com/viewer/eadaa45871804b4a974be865f627e791/Cloud/en-US/d1fe5fd8ecfb46c193221ebb991af3d7.html). For situations where the load is highly available and where applications need to react by scaling, consider using Application Autoscaler. For more information, see [What Is Application Autoscaler?](https://help.sap.com/viewer/7472b7d13d5d4862b2b06a730a2df086/Cloud/en-US/45341f37cf6e4738a4b7cd20f18350de.html "Automatically scale your applications to meet their dynamic resource needs.") :arrow_upper_right: 

-   **Working with Availability Zones**

    To benefit from the high availability mechanisms in Cloud Foundry, set up your applications with multiple instances. For more information, see [Developing Resilient Applications](https://help.sap.com/docs/BTP/0c8c1db388f645159e134a005aaabbcf/b1b929a5aea64571b2f74e810b622568.html?locale=en-US&state=PRODUCTION&version=Cloud).


<a name="loio001180644f8a428bb422cd41caebb95f"/>

<!-- loio001180644f8a428bb422cd41caebb95f -->

## Disaster Recovery as Part of the Business Continuity Plan

The cloud platform disaster recovery \(DR\) plan is part of the overall cloud platform business continuity plan, which includes crisis management and process continuity activities that are triggered by a declared disaster.



<a name="loio001180644f8a428bb422cd41caebb95f__section_knl_qqp_j3b"/>

## Standard Disaster Recovery

SAP can restore productive tenants from backups as soon as practicable in case of a disaster resulting in the loss of the primary production data center.

As the magnitude of a disaster is unpredictable, a region might not be restored in a reasonable time. In addition, a new infrastructure might need to be set up at a different location, which might require the purchase and setup of new hardware. Therefore, we can't guarantee any fixed recovery timelines.

