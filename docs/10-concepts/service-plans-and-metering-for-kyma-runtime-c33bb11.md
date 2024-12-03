<!-- loioc33bb114a86e474a95db29cfd53f15e6 -->

# Service Plans and Metering for Kyma Runtime

This page explains the relationship between the service plans of the SAP Discovery Center and the service plans of the SAP BTP cockpit and provides information to help you understand how the service is billed.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_gwp_yyy_5zb"/>

## Service



### Overview

![Service Plans for Kyma Runtime: Free (SKU 8011146) and Standard (8008456), with Standard available for aws, gcp, and azure.](images/Service_Plans_Kyma_fa903de.png)

[**SAP Discovery Center: Kyma Runtime**](https://discovery-center.cloud.sap/serviceCatalog/kyma-runtime?tab=service_plan)

> ### Note:  
> For more information, see [What is the Consumption-Based Commercial Model?](https://help.sap.com/docs/btp/sap-business-technology-platform/what-is-consumption-based-commercial-model?version=Cloud)



### SAP BTP Cockpit: Service Plans


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Service Plan \(Discovery Center\)

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

Subscribe to the 30-day free plan provided on Amazon Web Services. This plan uses Kyma on a limited-size cluster \(4 CPU—16 GB RAM\). You can use the free plan only once in a global account for up to 30 days. The upgrade to the paid plan is not yet supported. Only best-effort support is available for free tier service plans, and these are not subject to SLAs. The services you plan to use must be available in the same region as the subaccount for the Kyma runtime.

</td>
</tr>
<tr>
<td valign="top">

aws

</td>
<td valign="top">

Standard 

</td>
<td valign="top">

Select Amazon Web Services as the cloud provider where your Kyma cluster is deployed.

</td>
</tr>
<tr>
<td valign="top">

gcp

</td>
<td valign="top">

Standard 

</td>
<td valign="top">

Select Google Cloud as the cloud provider where your Kyma cluster is deployed.

</td>
</tr>
<tr>
<td valign="top">

azure

</td>
<td valign="top">

Standard 

</td>
<td valign="top">

Select Microsoft Azure as the cloud provider where your Kyma cluster is deployed.

</td>
</tr>
</table>



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_x43_x1z_5zb"/>

## Metrics

The usage metric for the Cloud Service is a Capacity Unit \(CU\) per month.


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

Capacity Unit

</td>
<td valign="top">

Number of units consumed by the usage of the services as outlined in the solution-specific product supplement.

For SAP BTP, Kyma runtime, there are two capacity units: one to measure the workload, the second to measure the storage.

</td>
</tr>
</table>



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_o4b_bsz_5zb"/>

## Backward Calculation



### Formula

The relationship between consumed workload/storage and the respective CU is straightforward.

However, cost per monthly bill may vary because it depends on the size of the nodes that were used. There is no fixed formula because of Kyma's flexible scaling.



### Underlying Metrics

In the following tables, “CU” stands for “Capacity Unit”.

**For CPU**


<table>
<tr>
<th valign="top">

Amount of CPU/CPU Nodes

</th>
<th valign="top">

Number of CU per Hour

</th>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

0.48055555555555557 x 0.75

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

0.48055555555555557

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

0.48055555555555557 x 2

</td>
</tr>
<tr>
<td valign="top">

16

</td>
<td valign="top">

0.48055555555555557 x 4

</td>
</tr>
<tr>
<td valign="top">

32

</td>
<td valign="top">

0.48055555555555557 x 8

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

**For Standard Storage**


<table>
<tr>
<th valign="top">

Amount of Storage

</th>
<th valign="top">

Number of CU per Hour

</th>
</tr>
<tr>
<td valign="top">

1GB

</td>
<td valign="top">

0.00056423611

</td>
</tr>
<tr>
<td valign="top">

32GB

</td>
<td valign="top">

0.01805555552 \(0.00056423611 x 32\)

</td>
</tr>
</table>

### Additional Costs

Certain features of Cloud Manager may initiate additional hardware resources in the cloud provider account. These features could potentially incur extra costs based on the resources you implement.
All additional costs are calculated using a baseline formula, which is a combination of the two metrics used to compute other Kyma costs: **CPU** and **Storage**.

#### Premium Storage

Premium storage can be enabled using Cloud Manager and will create storage using NFS technology.
The pricing for premium storage is based on the storage metrics and is scaled up by a factor of **3** compared to standard storage.

<table>
<tr>
<th valign="top">

Amount of Storage

</th>
<th valign="top">

Number of CU per Hour

</th>
</tr>
<tr>
<td valign="top">

1GB

</td>
<td valign="top">

0.00169271 ( = 3 * 0.00056423611)

</td>
</tr>
<tr>
<td valign="top">

32GB

</td>
<td valign="top">

0.05416667 \(0.00169271 x 32\)

</td>
</tr>
</table>

#### Cloud-managed Redis

When deployed with the Cloud Manager module, Redis creates a cluster in the Kyma's cloud provider account and begins consuming new, dedicated machines.
Generally, a cache is defined by its size, measured in GiB, which is then used to determine metering and billing using storage metrics as the basis.
As the price is standardized across all available cloud providers, Redis is offered in several different tiers that are essentially equivalent across all cloud providers. This applies to both the standard and the premium plans.

| **Tier** 	| **Approx. Available  Size (GiB)** | **Cost expressed in Storage size** 	| **Cost in CU** 	|
|:--------:	|:--------------------------------:	|-----------------------------------:	|---------------:	|
|    S1    	|                 1                	|                                182 	|             74 	|
|    S2    	|                 3                	|                                364 	|            148 	|
|    S3    	|                 6                	|                                953 	|            387 	|
|    S4    	|                12                	|                               1915 	|            778 	|
|    S5    	|                24                	|                               3793 	|           1541 	|
|    S6    	|                48                	|                               7591 	|           3084 	|
|    S7    	|                101               	|                              15180 	|           6167 	|
|    S8    	|                202               	|                              30353 	|          12331 	|
|    P1    	|                 5                	|                               1903 	|            773 	|
|    P2    	|                12                	|                               3828 	|           1555 	|
|    P3    	|                24                	|                               7586 	|           3082 	|
|    P4    	|                48                	|                              15180 	|           6167 	|
|    P5    	|                101               	|                              30363 	|          12335 	|
|    P6    	|                200               	|                              60704 	|          24661 	|

NB: **Approx. Available  Size (GiB)** might vary depending on the cloud provider.

### Examples

-   Your bill for Nodes shows 1800 capacity units charged for 4vCPU Nodes in a month.

    This means that you were running roughly 1800 / 0.4806 = 3745.32 hours worth of 4vCPU nodes. Given that a month has 720 hours, this means you were running 3745.32/720 = 5.2 Nodes cluster for a full month.

    Due to Kyma’s automatic scaling, 5.2 does not mean actual size. It means that during some hours in the month, the cluster size was 4 nodes. At other times, there was more load, so the cluster autoscaled to 5 or 6 nodes, based on your configurations. So your average cluster size for the full month was 5.2 Nodes.

-   Your bill for storage shows 200 capacity units charged for storage \(32GB block\) for the month.

    This means that you used 200 / 0.0181 = 11049.72 hours of 32GB storage blocks. Given that a month has 720 hours, this means that you have used 11049.72/720 = 15,34 blocks of 32GB over the month. So, you used 15.34 \* 32 = 491GB of storage continuously during the month.

    This implies that as you started using Kyma, you deployed more applications that used storage of various sizes, such as 4GB or 8GB.

    Note that storage is provided in blocks of 32GB, so if you used 33 GB, you would be charged for 2 \* 32GB, that is 64 GB.




<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_dnb_hsz_5zb"/>

## Calculator

Find the Kyma price calculator on [https://kyma-project.github.io/price-calculator/](https://kyma-project.github.io/price-calculator/) and use it to estimate the costs for your SAP BTP, Kyma runtime.

1.  Choose the **size of virtual machine** \(VM\).

2.  Choose the **minimum of VMs** you need.

3.  Optionally, add more storage and additional capabilities to the calculation.

4.  You can also change the **Conversion rate from Capacity Units to €** to estimate the eventual discount applicable with your contract.


Note that the result is an estimate, and the monthly bill may vary depending on the actual hours and size of the Kyma cluster \(workload and storage\) that was running in a month.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_egv_qcn_1bc"/>

## Supplemental Terms And Conditions

For more information, see [SAP Business Technology Platform Service Description Guide](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?%3Bpage=1&%3Bpdf-asset=82ce6fed-917e-0010-bca6-c68f7e60039b&%3Btag=language%3Aenglish&search=SAP%20Business%20Technology%20Platform%20Service%20Description%20Guide&sort=latest_desc&pdf-asset=9a48fd54-c97e-0010-bca6-c68f7e60039b&page=7), section “SAP BTP, KYMA RUNTIME”.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_bl4_4tz_5zb"/>

## Glossary

[Commercial Information Glossary](https://help.sap.com/docs/help/5d771150f8f547c6bc604c7d674cf30d/7014f9db099148f1897c1bda5db21f39.html?locale=en-US)



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_ypn_rtz_5zb"/>

## Service Specifics

As soon as you instantiate a Kyma cluster, the basic costs for the empty cluster incurs.

Cost may then vary depending on the actual workloads and storage you consume per month.

