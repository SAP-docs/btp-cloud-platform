<!-- loio964054384acd445fae9e3a80278096a8 -->

# Overview



<a name="loio964054384acd445fae9e3a80278096a8__section_vtg_l2k_j4b"/>

## Develop, Test, Build


<table>
<tr>
<th valign="top">

Phase



</th>
<th valign="top">

Step



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="7">

[Prepare](Develop,_Test,_Build_3bf575a.md#loio4338854e3133407abb47d3a281dbd1e1)



</td>
<td valign="top">

Register a namespace. See [Register a Namespace](Develop,_Test,_Build_3bf575a.md#loiocc5a3c6f78cf4889960c314dd09a5060).



</td>
<td valign="top">

A namespace is mandatory and must be reserved at [https://support.sap.com/namespaces](https://support.sap.com/namespaces).

> ### Note:  
> You have to register a namespace before the first ABAP system is provisioned. For namespaces that are reserved after system provisioning, you have to create an incident.
> 
> Namespaces should have 5–8 characters due to length restrictions of certain objects. See SAP note [105132](https://launchpad.support.sap.com/#/notes/105132) and [395083](https://launchpad.support.sap.com/#/notes/395083)



</td>
</tr>
<tr>
<td valign="top">

Set up a development account. See [Set Up a Development Account](Develop,_Test,_Build_3bf575a.md#loio9f2150f2b15e414aacd46c1723ce48fb).



</td>
<td valign="top">

Get a partner development contract and a global development account

Required entitlements:

-   Services: abap/standard
-   Applications:
    -   Web access for testing
    -   SAP Business Application Studio for UI development


See [SAPPartnerEdge Test, Demo and Development Price List](https://partneredge.sap.com/en/library/assets/partnership/sales/order_license/pl_pl_part_price_list.html).



</td>
</tr>
<tr>
<td valign="top">

Set up a production account. See [Set Up a Production Account](Develop,_Test,_Build_3bf575a.md#loio2e7b4b631e814de1b8fe3959af4105bc).



</td>
<td valign="top">

Get a partner contract and a global production account.

Required entitlements:

-   Services:
    -   abap/saas\_oem
    -   Application runtime for approuter
    -   abap-solution \(ABAP Solution Provider\)
    -   saas-registry \(without entitlement\)
    -   xsuaa \(without entitlement\)

-   Applications:
    -   Landscape Portal
    -   Web access for ABAP


See [SAPPartnerEdge: Resources for OEM Partners](https://partneredge.sap.com/en/partnership/manage/op_resource/oem.html)



</td>
</tr>
<tr>
<td valign="top">

Create ABAP instance\(s\). See [Create ABAP Instances](Develop,_Test,_Build_3bf575a.md#loio17aa433273c24bd2b949c297513851fe).



</td>
<td valign="top">

Set up your development subaccount and ABAP system and create the following:

-   Development system with parameter `is_development_allowed = true`
-   Test system with parameter `is_development_allowed = false`
-   abap/abap\_compute\_unit \(standard: 1\)
-   abap/hana\_compute\_unit \(standard: 4\)
-   Subscriptions in DEV/TEST subaccount to ABAP Web Access

See [Getting Started with a Customer Account: Workflow in the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e34a329acc804c0e874496548183682f.html) and [Create an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f0163565eb554f009f990652ca41d1c6.html).



</td>
</tr>
<tr>
<td valign="top">

Set up UI development. See [Set Up UI Development](Develop,_Test,_Build_3bf575a.md#loio3f03dfe2f21b471ab98abc6f208c3762).



</td>
<td valign="top">

Configure SAP Business Application Studio for UI development. Decide on your UI/SAP SAP Fiori launchpad setup and deployment model: ABAP or Cloud Foundry



</td>
</tr>
<tr>
<td valign="top">

Transport \(DEV, TST\) with gCTS. See [Set Up Transport from Development to Test System via gCTS](Develop,_Test,_Build_3bf575a.md#loiobf557544f90f4bc88911c4865ec78207).



</td>
<td valign="top">

Plan and set up your test and maintenance system landscape and processes.

[Tutorial: Transport a Software Component Between two Systems](https://developers.sap.com/tutorials/abap-environment-gcts.html)

\[Optional\] Set up a CI server and pipeline for testing. See [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction/).



</td>
</tr>
<tr>
<td valign="top">

Set up add-on development. [Set Up Add-On Development](Develop,_Test,_Build_3bf575a.md#loio89a353151e534380a03b2a572a227731).



</td>
<td valign="top">

Create a new software component for add-on development and clone the main branch of the software component to the development and test system.



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

[Develop](Develop,_Test,_Build_3bf575a.md#loio9464e3af139d4e0581cb4e819886b0c8)



</td>
<td valign="top">

ABAP development. See [ABAP Development](Develop,_Test,_Build_3bf575a.md#loiofa5af4ecdf90496b8eec54fe0e22150c).



</td>
<td valign="top">

Follow the guidelines to enable multitenancy for applications built on the ABAP environment.

See [Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](Development_Guideline_to_Enable_Multitenancy_of_Products_Built_on_the_ABAP_Environment_9d994c8.md) and [Tutorials](https://developers.sap.com/tutorial-navigator.html?tag=products:technology-platform/sap-cloud-platform/sap-cloud-platform-abap-environment).



</td>
</tr>
<tr>
<td valign="top">

UI development. See [UI Development](Develop,_Test,_Build_3bf575a.md#loiof3be8246edc74be59c10779443f67793).



</td>
<td valign="top">

Develop UIs using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](Develop_an_SAP_Fiori_Application_UI_and_Deploy_it_to_ABAP_Using_SAP_Business_Application_Studio_eaaeba4.md).



</td>
</tr>
<tr>
<td valign="top">

\[Optional\] Code migration. See [\(Optional\) Code Migration from On-Premise](Develop,_Test,_Build_3bf575a.md#loiof438645cb5664399a6b21f8d9bd3d004).



</td>
<td valign="top">

Migrate your ABAP code from on-premise.

See [Blog: How to bring your ABAP custom to the ABAP Environment](https://blogs.sap.com/2019/11/11/how-to-bring-your-abap-custom-code-to-sap-cloud-platform-abap-environment/) and [Blog: How to check your custom ABAP code for the ABAP Environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

[Test](Develop,_Test,_Build_3bf575a.md#loio023cf9d301b1479484e70b17cd5cf587)



</td>
<td valign="top">

Test in cloud system. See [Test in the ABAP Environment SAP Fiori Launchpad](Develop,_Test,_Build_3bf575a.md#loio8c5b4d76a05b4bed8df01937f4d8d487).



</td>
<td valign="top">

Import the ABAP service \(with gCTS\) and the UI into your test system.

Create a role and assign it to users, then execute the service and UI.



</td>
</tr>
<tr>
<td valign="top">

ABAP Test Cockpit. See [Test in the ABAP Test Cockpit](Develop,_Test,_Build_3bf575a.md#loiof0b71a1c959842258772c27d292c43b0).



</td>
<td valign="top">

Run ATC checks in DEV and/or TST systems.

See [ABAP Test Cockpit in the Cloud – What is already possible](https://blogs.sap.com/2020/08/14/abap-test-cockpit-in-the-cloud-what-is-already-possible/) and [ABAP Test Cockpit Configurator](../50-administration-and-ops/ABAP_Test_Cockpit_Configurator_22c26ff.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

[Build](Develop,_Test,_Build_3bf575a.md#loio25049720bde447e395b3df0bc05e5a50)



</td>
<td valign="top">

Build your add-on. See [Set Up Add-On Build](Develop,_Test,_Build_3bf575a.md#loioccf0c1ef30ce4d6aa6e39bb583fb8ba1).



</td>
<td valign="top">

Set up a CI server and pipeline for the add-on build.

Create a technical communication user to access AAKaaS.

See [Build and Publish Add-on Products on SAP BTP, ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).

Register the add-on product/global production account by creating an incident under component `BC-CP-ABA` and provide the following information:

-   Add-on product name = `addonProduct` in `addon.yml` file,e.g. `/NAMESPACE/NAME`
-   Global account ID provider
    -   Feature Set A: Account ID in section *Global Account Info* on overview page in provider global account, e.g., 151b5fdc-58c1-4a55-95e1-467df2134c5
    -   Feature Set B: Account ID in *Usage Analytics*




</td>
</tr>
<tr>
<td valign="top">

Build your first add-on version. See [Build the First Add-On Version](Develop,_Test,_Build_3bf575a.md#loio96f9db9e6c784e5a89ede4d038daaa43).



</td>
<td valign="top">

Create a maintenance branch.

Configure the add-on yml.file.

Trigger the add-on product build/test/release.



</td>
</tr>
</table>



<a name="loio964054384acd445fae9e3a80278096a8__section_zxb_b4c_l4b"/>

## Order and Provide


<table>
<tr>
<th valign="top">

Phase



</th>
<th valign="top">

Step



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="5">

[Deploy](Order_and_Provide_975bd3e.md#loio4e35eb027f284b7fa6219bc70561fb4e)



</td>
<td valign="top">

Configure the sizing of the SaaS application. See [Sizing](Order_and_Provide_975bd3e.md#loio1782f253e102484dac378887b3d6d769).



</td>
<td valign="top">

Decide on the metric of your offering \(e.g. users, documents, space\) and map the metric of your offering to the service plan of the ABAP environment service plan.

Implement the sizing via `abap_compute_unit` and `hana_compute_unit` parameters in the ABAP Solution Provider.

See [Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md).

> ### Note:  
> For multitenancy offerings, there is no sizing/quota per customer \(client\). You must decide on an overall sizing depending on the expected load in a region \(e.g. Europe/Frankfurt\).



</td>
</tr>
<tr>
<td valign="top">

Set up multitenancy. See [Multitenancy](Order_and_Provide_975bd3e.md#loio6cb128101a6f40f3a8f234a1d9bb8b01).



</td>
<td valign="top">

As a DevOps engineer using parameter tenant\_mode in the ABAP Solution service, you can define whether a customer gets a tenant in a dedicated system \(single\) or a shared system \(multi\).



</td>
</tr>
<tr>
<td valign="top">

Runtime and persistence. See [Runtime and Persistence](Order_and_Provide_975bd3e.md#loiobb8bc1e3c99145c79106ecafc73f5a4f).



</td>
<td valign="top">

Determine the number of ABAP compute units and HANA compute units for the creation of an ABAP system by using parameters `size_of_runtime` and `size_of_persistence`.



</td>
</tr>
<tr>
<td valign="top">

SaaS registry. See [Multitenant Application](Order_and_Provide_975bd3e.md#loiof3305f65648248318028e02c84375323).



</td>
<td valign="top">

Create the multitenant application with SaaS registry, XSUAA and ABAP Solution Provider subscription.

See [Definition of the MTA Resources](Definition_of_the_MTA_Resources_1764436.md).



</td>
</tr>
<tr>
<td valign="top">

Access to Landscape Portal. See [Access to Landscape Portal](Order_and_Provide_975bd3e.md#loio195a685a71f84953813e7b3bd255e849).



</td>
<td valign="top">

Subscribe to the Landscape Portal application.

See [Accessing the Landscape Portal](Accessing_the_Landscape_Portal_2e1e393.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

[Commercialize](Order_and_Provide_975bd3e.md#loio57c19c7c4dfa4c3cbb846c1ac57e2095)



</td>
<td valign="top">

\[Optional\] SAP App Center registration. See [\(Optional\) Register SaaS Solution in SAP App Center](Order_and_Provide_975bd3e.md#loio607aa8614ea34ee7b366b01ad03bfc4c).



</td>
<td valign="top">

Register your SaaS solution in SAP App Center.

See [https://store.sap.com/en/](https://store.sap.com/en/).



</td>
</tr>
<tr>
<td valign="top">

\[Optional\] Certification. See [\(Optional\) Certification](Order_and_Provide_975bd3e.md#loioace3b22147eb40d3989c5525491eb729).



</td>
<td valign="top">

Get an optional certification for your product.

See [Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [Certified Solutions](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/partners)



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

[Order and Provide](Order_and_Provide_975bd3e.md#loioa24217a0d6fa434bbce97869dfb70dda)



</td>
<td valign="top">

Create a consumer subaccount. See [Create Consumer Subaccount](Order_and_Provide_975bd3e.md#loio8b92024cc5d44268bf4737551e4fa981).



</td>
<td valign="top">

Set the account structure for the consumer subaccount.



</td>
</tr>
<tr>
<td valign="top">

Subscribe to the SaaS solution. See [Subscribe to SaaS Solution](Order_and_Provide_975bd3e.md#loio477ea31394504182b2ea5ef9ce26802d).



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Configure consumer subaccount. See [Configure Consumer Subaccount \(Feature Set A\)](Order_and_Provide_975bd3e.md#loio3c44b19161d742a5a96576d64e70d505).



</td>
<td valign="top">

Configure customer subaccount.

-   Option A: Provider configures the subaccount
-   Option B: Customer configures subaccount



</td>
</tr>
<tr>
<td valign="top">

Initial User Onboarding. See [Initial User Onboarding](Order_and_Provide_975bd3e.md#loio4a9c5011922847ac91db165c78656149)



</td>
<td valign="top">

Create an initial administrator user for the customer.



</td>
</tr>
</table>



<a name="loio964054384acd445fae9e3a80278096a8__section_amh_p15_hrb"/>

## Configure and Implement a Customer Project


<table>
<tr>
<th valign="top">

Phase



</th>
<th valign="top">

Step



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

[Configure and Implement a Customer Project](Configure_and_Implement_a_Customer_Project_363d2ea.md#loio363d2ea033b14ecfa5c67cf8d3e7cb01)



</td>
<td valign="top">

Set up Identity and Access Management.



</td>
<td valign="top">

Create and assign business roles.

Create spaces and pages for business roles.



</td>
</tr>
<tr>
<td valign="top">

Integrate the customer project.



</td>
<td valign="top">

Create communication arrangements.



</td>
</tr>
<tr>
<td valign="top">

Configure the customer project.



</td>
<td valign="top">

Create business configuration.

Configure key user extemsibility.



</td>
</tr>
</table>



<a name="loio964054384acd445fae9e3a80278096a8__section_o2b_q1j_l4b"/>

## Maintain


<table>
<tr>
<th valign="top">

Phase



</th>
<th valign="top">

Step



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="4">

[Maintain](Maintain_9721f0f.md#loio9721f0fb92a84e2a95309acf445cb0a9)



</td>
<td valign="top">

Set up your test and maintenance system landscape and processes. See [Set Up Maintenance System Landscape](Maintain_9721f0f.md#loio44035458f01e4142a18d44f9c0301e62).



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Create an update. See [Create Update for SaaS Solution](Maintain_9721f0f.md#loioa35582346bff4914a5b4b0bcb776668c).



</td>
<td valign="top">

Create a new patch version, support package version, or release/product version.



</td>
</tr>
<tr>
<td valign="top">

Trigger the add-on product build. See [Trigger Add-On Product Build](Maintain_9721f0f.md#loio7f6988a9a9f94845825d8c7ff66990fb).



</td>
<td valign="top">

Trigger the execution of the configured ABAP environment pipeline for an add-on build.



</td>
</tr>
<tr>
<td valign="top">

Apply update for SaaS solution \(=add-on product\). See [Apply Update for SaaS Solution](Maintain_9721f0f.md#loio0a80d4c5c079435e9aca4eb9e6841de9).



</td>
<td valign="top">

Deploy your add-on update by using the Landscape Portal.

See [Landscape Portal](Landscape_Portal_5eb70fb.md).



</td>
</tr>
</table>



<a name="loio964054384acd445fae9e3a80278096a8__section_gdf_415_hrb"/>

## Dismantle


<table>
<tr>
<th valign="top">

Phase



</th>
<th valign="top">

Step



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

[Dismantle](Dismantle_35a5882.md)



</td>
<td valign="top">

Delete tenants.



</td>
<td valign="top">

Unsubscribe the SaaS solution. See [Consumer Offboarding](Consumer_Offboarding_c882a2a.md).



</td>
</tr>
<tr>
<td valign="top">

\(Optional\) Restore deleted tenants.



</td>
<td valign="top">

Restore the deleted tenants within a grace period of 30 days. See [Consumer Offboarding](Consumer_Offboarding_c882a2a.md).



</td>
</tr>
</table>

