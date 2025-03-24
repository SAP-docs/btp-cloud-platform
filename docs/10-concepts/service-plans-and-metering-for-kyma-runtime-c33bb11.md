<!-- loioc33bb114a86e474a95db29cfd53f15e6 -->

# Service Plans and Metering for Kyma Runtime

This page explains the relationship between the service plans of the SAP Discovery Center and the service plans of the SAP BTP cockpit and provides information to help you understand how the service is billed.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_gwp_yyy_5zb"/>

## Service



### Overview

The following diagram shows how the service plans listed in the [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/kyma-runtime?tab=service_plan) correspond to the plans you choose in the SAP BTP cockpit. For more information about the commercial model, see [What is the Consumption-Based Commercial Model?](https://help.sap.com/docs/btp/sap-business-technology-platform/what-is-consumption-based-commercial-model?version=Cloud)

Note that there's no subscription-based commercial model for SAP BTP, Kyma runtime.

![Service Plans for Kyma Runtime: Free (SKU 8011146) and Standard (8008456), with Standard available for aws, gcp, and azure.](images/Service_Plans_Kyma_fa903de.png)



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

For SAP BTP, Kyma runtime, CUs are calculated for **workload** and for **storage**.

</td>
</tr>
</table>



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_o4b_bsz_5zb"/>

## Backward Calculation

> ### Tip:  
> If you use the Cloud Manager module, also see [Calculation with the Cloud Manager Module](service-plans-and-metering-for-kyma-runtime-c33bb11.md#loioc33bb114a86e474a95db29cfd53f15e6__section_cloud_manager).



### Formula

The relationship between consumed workload/storage and the respective CU is straightforward.

However, cost per monthly bill may vary because it depends on the size of the nodes that were used. There is no fixed formula because of Kyma's flexible scaling.



### Underlying Metrics

In the following tables, “CU” stands for “Capacity Unit”.

**Calculation for CPU**


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

0.48055555555555557 \* 0.75

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

0.48055555555555557 \* 2

</td>
</tr>
<tr>
<td valign="top">

16

</td>
<td valign="top">

0.48055555555555557 \* 4

</td>
</tr>
<tr>
<td valign="top">

32

</td>
<td valign="top">

0.48055555555555557 \* 8

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

**Calculation for Storage**


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

0.01805555552 \(= 0.00056423611 \* 32\)

</td>
</tr>
</table>



### Examples

-   Your bill for Nodes shows 1800 capacity units charged for 4vCPU Nodes in a month.

    This means that you were running roughly 1800 / 0.4806 = 3745.32 hours worth of 4vCPU nodes. Given that a month has 720 hours, this means you were running 3745.32/720 = 5.2 Nodes cluster for a full month.

    Due to Kyma’s automatic scaling, 5.2 does not mean actual size. It means that during some hours in the month, the cluster size was 4 nodes. At other times, there was more load, so the cluster autoscaled to 5 or 6 nodes, based on your configurations. So your average cluster size for the full month was 5.2 Nodes.

-   Your bill for storage shows 200 capacity units charged for storage \(32GB block\) for the month.

    This means that you used 200 / 0.0181 = 11049.72 hours of 32GB storage blocks. Given that a month has 720 hours, this means that you have used 11049.72/720 = 15,34 blocks of 32GB over the month. So, you used 15.34 \* 32 = 491GB of storage continuously during the month.

    This implies that as you started using Kyma, you deployed more applications that used storage of various sizes, such as 4GB or 8GB.

    Note that storage is provided in blocks of 32GB, so if you used 33 GB, you would be charged for 2 \* 32GB, that is 64 GB.




<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_cloud_manager"/>

## Calculation with the Cloud Manager Module



### Calculation with the Cloud Manager Module

Using the Cloud Manager module and enabling Redis or NFS storage or both, introduces additional costs.

-   The cost of NFS storage introduces factor 3 to the calculation.

    **Calculation for NFS Storage**


    <table>
    <tr>
    <th valign="top">

    Amount of NFS Storage
    
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
    
    0.00169271 \( = 0.00056423611 \* 3\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    32GB
    
    </td>
    <td valign="top">
    
    0.05416667 \(= 0.00169271 \* 32\)
    
    </td>
    </tr>
    </table>
    
-   Using Redis adds costs depending on the tier you choose.

    > ### Note:  
    > Even though the actual available size \(GiB\) might vary depending on the cloud provider, the tiers for Redis are standardized across cloud providers. Because of that, also the pricing is standardized across all available cloud providers.

    **Calculation for Redis Tiers**


    <table>
    <tr>
    <th valign="top">

    Tier
    
    </th>
    <th valign="top">

    Approx. Available Size \(GiB\)
    
    </th>
    <th valign="top">

    Number of CU per Hour
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    S1
    
    </td>
    <td valign="top">
    
    1
    
    </td>
    <td valign="top">
    
    0.1027777778
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S2
    
    </td>
    <td valign="top">
    
    3
    
    </td>
    <td valign="top">
    
    0.2055555556
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S3
    
    </td>
    <td valign="top">
    
    6
    
    </td>
    <td valign="top">
    
    0.5375000000
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S4
    
    </td>
    <td valign="top">
    
    12
    
    </td>
    <td valign="top">
    
    1.0805555556
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S5
    
    </td>
    <td valign="top">
    
    24
    
    </td>
    <td valign="top">
    
    2.1402777778
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S6
    
    </td>
    <td valign="top">
    
    48
    
    </td>
    <td valign="top">
    
    4.2833333333
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S7
    
    </td>
    <td valign="top">
    
    101
    
    </td>
    <td valign="top">
    
    8.5652777778
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    S8
    
    </td>
    <td valign="top">
    
    202
    
    </td>
    <td valign="top">
    
    17.1263888889
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    P1
    
    </td>
    <td valign="top">
    
    5
    
    </td>
    <td valign="top">
    
    1.0736111111
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    P2
    
    </td>
    <td valign="top">
    
    12
    
    </td>
    <td valign="top">
    
    2.1597222222
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    P3
    
    </td>
    <td valign="top">
    
    24
    
    </td>
    <td valign="top">
    
    4.2805555556
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    P4
    
    </td>
    <td valign="top">
    
    48
    
    </td>
    <td valign="top">
    
    8.5652777778
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    P5
    
    </td>
    <td valign="top">
    
    101
    
    </td>
    <td valign="top">
    
    17.1319444444
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    P6
    
    </td>
    <td valign="top">
    
    200
    
    </td>
    <td valign="top">
    
    34.2513888889
    
    </td>
    </tr>
    </table>
    



### Examples for Cloud Manager

-   Your bill for the NFS storage shows 200 capacity units charged for storage \(32GB block\) for the month.

    This means that you used 200 / 0.0542 = 3692.31 hours of 32GB storage blocks. Given that a month has 720 hours, this means that you have used 3692.31/720 = 5.13 blocks of 32GB over the month. So, you used 15.34 \* 32 = 164.10 GB of NFS storage continuously during the month.

-   Your bill for Redis shows 200 capacity units for storage for the month

    This means that you used 200 / 0.1027777778 = 1945.946 hours of the Redis S1 tier. Given that a month has 720 hours, this means that you have used 1945.946/720 = 2.703 tier S1 Redis instances continuously during the month.




<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_dnb_hsz_5zb"/>

## Calculator

Find the Kyma price calculator on [https://kyma-project.github.io/price-calculator/](https://kyma-project.github.io/price-calculator/) and use it to estimate the costs for your SAP BTP, Kyma runtime.

1.  Choose the base configuration for the size and minimum number virtual machines \(VM\) you need.

2.  Optionally, add more storage to the calculation.

3.  If needed, adjust the conversion rate.


Note that the result is an estimate, and the monthly bill may vary depending on the actual hours and size of the Kyma cluster \(workload and storage\) that was running in a month.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_egv_qcn_1bc"/>

## Supplemental Terms And Conditions

For more information, see [SAP Business Technology Platform Service Description Guide](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?%3Bpage=1&%3Bpdf-asset=82ce6fed-917e-0010-bca6-c68f7e60039b&%3Btag=language%3Aenglish&search=SAP%20Business%20Technology%20Platform%20Service%20Description%20Guide&sort=latest_desc&pdf-asset=9a48fd54-c97e-0010-bca6-c68f7e60039b&page=7), section “SAP BTP, KYMA RUNTIME”.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_bl4_4tz_5zb"/>

## Glossary

[Commercial Information Glossary](https://help.sap.com/docs/help/5d771150f8f547c6bc604c7d674cf30d/7014f9db099148f1897c1bda5db21f39.html?locale=en-US)



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_ypn_rtz_5zb"/>

## Service Specifics

As soon as you instantiate a Kyma cluster, the basic cost for the empty cluster incurs.

Cost may then vary depending on the actual workloads and storage you consume per month.

