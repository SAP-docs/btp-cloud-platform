<!-- loioc33bb114a86e474a95db29cfd53f15e6 -->

# Commercial Information for Kyma Runtime



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_rkn_4pz_5zb"/>

## Service Description

SAP BTP, Kyma runtime is a fully managed Kubernetes runtime based on the open-source project "Kyma". This cloud-native solution allows the developers to extend SAP solutions with serverless Functions and combine them with containerized microservices. The offered functionality ensures smooth consumption of SAP and non-SAP applications, running workloads in a highly scalable environment, and building event- and API-based extensions.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_gwp_yyy_5zb"/>

## Service Plans



### Service Overview

![](images/Service_Plans_Kyma_3b88103.png)



### SAP BTP Cockpit Service Plan Descriptions

**SAP BTP Cockpit Service Plan Descriptions**


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

Subscribe to the 30-day free plan provided on Amazon Web Services. This plan uses Kyma on a limited size cluster \(4CPU - 16GB RAM\). The upgrade to the paid plan is not yet supported. Only best-effort support is available for free tier service plans and these are not subject to SLAs. The services you plan to use must be available in the same region as the subaccount for the Kyma runtime.

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

**For Storage**


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

3.  Estimate the **hours per month** you expect to run them.

4.  Optionally, add more Nodes and more storage to the calculation.


Note that the result is an estimate, and the monthly bill may vary depending on the actual hours and size of the Kyma cluster \(workload and storage\) that was running in a month.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_egv_qcn_1bc"/>

## Supplemental Terms And Conditions

For additional information, please refer to the [SAP Business Technology Platform Service Description Guide](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?sort=latest_desc&search=SAP%20Business%20Technology%20Platform%20Service%20Description%20Guide&tag=language:english), section “SAP BUSINESS TECHNOLOGY PLATFORM, KYMA RUNTIME”.



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_bl4_4tz_5zb"/>

## Glossary

[Commercial Information Glossary](https://help.sap.com/docs/help/5d771150f8f547c6bc604c7d674cf30d/7014f9db099148f1897c1bda5db21f39.html?locale=en-US)



<a name="loioc33bb114a86e474a95db29cfd53f15e6__section_ypn_rtz_5zb"/>

## Service Specifics

As soon as you instantiate a Kyma cluster, the basic costs for the empty cluster incurs.

Cost may then vary depending on the actual workloads and storage you consume per month.

