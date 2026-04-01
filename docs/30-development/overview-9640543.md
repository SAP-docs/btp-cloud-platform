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
<th valign="top">

User/Role

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

[Prepare](prepare-4338854.md)

</td>
<td valign="top">

Register a namespace. See [Register a Namespace](register-a-namespace-cc5a3c6.md).

</td>
<td valign="top">

A namespace is mandatory and must be reserved at [https://support.sap.com/namespaces](https://support.sap.com/namespaces).

> ### Note:  
> You have to register a namespace before the first ABAP system is provisioned. To create namespaces after system provisioning, see [Maintain Namespaces](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/59e9ddee17ee496fa14e2760c78bf9da.html?locale=en-US).
> 
> Namespaces should have 5–8 characters due to length restrictions of certain objects. See SAP note [105132](https://me.sap.com/notes/105132) and [395083](https://me.sap.com/notes/395083).



</td>
<td valign="top">

S-user

</td>
</tr>
<tr>
<td valign="top">

Set up a global account for development. See [Set Up a Global Account for Development](set-up-a-global-account-for-development-9f2150f.md).

</td>
<td valign="top">

Get a partner development license for discounted systems used for development, test, or demo purposes. These systems are provisioned in the global account for development.

Required entitlements:

-   Services:
    -   `abap/standard` and `abap/saas_oem`
    -   Application runtime for approuter
    -   abap-solution \(ABAP Solution Provider\)

-   Applications:
    -   Landscape Portal
    -   Web access for ABAP
    -   SAP Business Application Studio for UI development


The `saas-registry` and `xsuaa` service are available without entitlement. See [SAPPartnerEdge Test, Demo and Development Price List](https://partneredge.sap.com/en/library/assets/partnership/sales/order_license/pl_pl_part_price_list.html).

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Set up a global account for production. See [Set Up a Global Account for Production](set-up-a-global-account-for-production-2e7b4b6.md).

</td>
<td valign="top">

Get a partner production license for systems used for production purposes. These systems are provisioned in the global account for production.

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


See [SAPPartnerEdge: Resources for OEM Partners](https://partneredge.sap.com/en/partnership/manage/op_resource/oem.html).

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Create ABAP instance\(s\). See [Create ABAP Instances](create-abap-instances-17aa433.md).

</td>
<td valign="top">

Set up your development/test subaccounts and ABAP system and create the following:

-   Development system DEV with parameter `is_development_allowed = true`
    -   abap/abap\_compute\_unit \(standard: 1\)
    -   abap/hana\_compute\_unit \(standard: 4\)

-   Test system TST with parameter `is_development_allowed = false`
    -   abap/abap\_compute\_unit \(standard: 1\)
    -   abap/hana\_compute\_unit \(standard: 4\)

-   Subscriptions in development/test subaccount to ABAP Web Access

See [Getting Started with a Customer Account: Workflow in the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e34a329acc804c0e874496548183682f.html) and [Create an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f0163565eb554f009f990652ca41d1c6.html).

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Set up UI development. See [Set Up UI Development](set-up-ui-development-3f03dfe.md).

</td>
<td valign="top">

Configure SAP Business Application Studio for UI development.

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Set up add-on development. [Set Up Add-On Development](set-up-add-on-development-89a3531.md).

</td>
<td valign="top">

Create a new software component for add-on development and clone the main branch of the software component to the development and test system.

</td>
<td valign="top">

Add-on administrator

</td>
</tr>
<tr>
<td valign="top">

Transport from development to test system. See [Set Up Transport from Development to Test System](set-up-transport-from-development-to-test-system-bf55754.md).

</td>
<td valign="top">

Plan and set up the transport of software components from development to test systems.

[Tutorial: Transport a Software Component Between two Systems](https://developers.sap.com/tutorials/abap-environment-gcts.html)

> ### Note:  
> A CI/CD server that is running the ABAP Environment Pipeline is required. See [ABAP Environment Pipeline](abap-environment-pipeline-2398b87.md).



</td>
<td valign="top">

Add-on administrator

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

[Develop](develop-9464e3a.md)

</td>
<td valign="top">

ABAP development. See [ABAP Development](abap-development-fa5af4e.md).

</td>
<td valign="top">

Follow the guidelines to enable multitenancy for applications built on the ABAP environment.

See [Multitenancy Development Guideline](multitenancy-development-guideline-9d994c8.md) and [Tutorials](https://developers.sap.com/tutorial-navigator.html?tag=products:technology-platform/sap-cloud-platform/sap-cloud-platform-abap-environment).

</td>
<td valign="top">

Developer

</td>
</tr>
<tr>
<td valign="top">

UI development. See [UI Development](ui-development-f3be824.md).

</td>
<td valign="top">

Develop UIs using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).

</td>
<td valign="top">

Developer

</td>
</tr>
<tr>
<td valign="top">

\[Optional\] Code migration. See [\(Optional\) Code Migration from On-Premise](optional-code-migration-from-on-premise-f438645.md).

</td>
<td valign="top">

Migrate your ABAP code from on-premise.

See [Blog: How to bring your ABAP custom to the ABAP Environment](https://blogs.sap.com/2019/11/11/how-to-bring-your-abap-custom-code-to-sap-cloud-platform-abap-environment/) and [Blog: How to check your custom ABAP code for the ABAP Environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/).

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

[Test](test-023cf9d.md)

</td>
<td valign="top">

Test in cloud system. See [Test in the ABAP Environment SAP Fiori Launchpad](test-in-the-abap-environment-sap-fiori-launchpad-8c5b4d7.md).

</td>
<td valign="top">

Import the ABAP service and the UI into your test system.

Create a role and assign it to users, then test the service and UI.

</td>
<td valign="top">

Test user

</td>
</tr>
<tr>
<td valign="top">

Test in the ABAP Test Cockpit. See [Test in the ABAP Test Cockpit](test-in-the-abap-test-cockpit-f0b71a1.md).

</td>
<td valign="top">

Run ABAP Test Cockpit checks in DEV and/or TST systems.

See [ABAP Test Cockpit in the Cloud – What is already possible](https://blogs.sap.com/2020/08/14/abap-test-cockpit-in-the-cloud-what-is-already-possible/) and [Configure ABAP Test Cockpit](../50-administration-and-ops/configure-abap-test-cockpit-22c26ff.md).

Request exemptions for false-positives and approve or reject the same.

</td>
<td valign="top">

Developer runs ATC checks and requests exemptions.

Quality manager approves or rejects exemptions

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

[Build](build-2504972.md)

</td>
<td valign="top">

Prepare your add-on build. See [Set Up Add-On Build](set-up-add-on-build-ccf0c1e.md).

</td>
<td valign="top">

Set up a CI/CD server and pipeline for the add-on build.

Create a technical communication user to access AAKaaS.

See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).

Register the add-on product in the global account for development and production as described in [Register Add-on Product for a Global Account](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#register-add-on-product-for-a-global-account) and [Register Product](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/7b5e33f3e62e4cf2984385759dfc61f8.html).

</td>
<td valign="top">

-   Jenkins administrator for access to CI/CD Server
-   S-user to create technical communication user
-   Operator to assign technical platform user as space developer
-   DevOps engineer to configure the pipeline



</td>
</tr>
<tr>
<td valign="top">

Build your first add-on version. See [Build the First Add-On Version](build-the-first-add-on-version-96f9db9.md).

</td>
<td valign="top">

Create a maintenance branch.

Download API snapshot from add-on build system to upload in other systems.

Configure the addon.yml file.

Trigger the add-on product build/test/release.

</td>
<td valign="top">

Add-on administrator: create maintenance branch, configure addon.yml file, and trigger build pipeline

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
<th valign="top">

User/Role

</th>
</tr>
<tr>
<td valign="top" rowspan="5">

[Deploy](deploy-4e35eb0.md)

</td>
<td valign="top">

Configure the sizing of the SaaS application. See [Sizing](sizing-1782f25.md).

</td>
<td valign="top">

Decide on the metric of your offering \(for example users, documents, space\) and map the metric of your offering to the service plan of the ABAP environment service.

> ### Note:  
> For multitenancy offerings, there is no sizing/quota per customer \(client\). You must decide on an overall sizing depending on the expected load in a region \(for example Europe/Frankfurt\).
> 
> As a DevOps engineer using parameter t`enant_mode` in the ABAP Solution service, you can define whether a customer gets a tenant in a dedicated system \(single\) or a shared system \(multi\).
> 
> Determine the number of ABAP compute units and HANA compute units for the creation of an ABAP system by using parameters `size_of_runtime` and `size_of_persistence`.



</td>
<td valign="top">

DevOps engineer

</td>
</tr>
<tr>
<td valign="top">

Implement a multitenant application and deploy it to the provider subaccount in the global account for development. See [Multitenant Applications](multitenant-applications-195031f.md).

</td>
<td valign="top">

Create the multitenant application with SaaS registry, XSUAA, and ABAP Solution Provider. Deploy to the provider subaccount with parameters used for development phase.

</td>
<td valign="top">

DevOps engineer

</td>
</tr>
<tr>
<td valign="top">

Access the Landscape Portal. See [Access to Landscape Portal](access-to-landscape-portal-195a685.md).

</td>
<td valign="top">

Subscribe to the Landscape Portal application in the global accounts for development and production.

See [Accessing the Landscape Portal](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d9e865ad47204b80816b6f62af57b823.html).

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Test the multitenant application deployed to the global account for development.

</td>
<td valign="top">

Subscribe to the SaaS solution from the consumer subaccount.

</td>
<td valign="top">

DevOps engineer

</td>
</tr>
<tr>
<td valign="top">

Deploy the multitenant application to the provider subaccount in the global account for production.

</td>
<td valign="top">

Deploy to the provider subaccount with parameters used for production phase.

</td>
<td valign="top">

DevOps engineer

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

[Commercialize](commercialize-57c19c7.md)

</td>
<td valign="top">

\[Optional\] SAP Store registration. See [\(Optional\) Register SaaS Solution in SAP Store](optional-register-saas-solution-in-sap-store-607aa86.md).

</td>
<td valign="top">

Register your SaaS solution in SAP Store.

See [https://store.sap.com/dcp/en/](https://store.sap.com/dcp/en/).

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

\[Optional\] Certification. See [\(Optional\) Certification](optional-certification-ace3b22.md).

</td>
<td valign="top">

Get an optional certification for your product.

See [Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [Certified Solutions](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/partners).

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

[Subscribe](subscribe-a24217a.md)

</td>
<td valign="top">

Create a consumer subaccount. See [Create Consumer Subaccount](create-consumer-subaccount-8b92024.md).

</td>
<td valign="top">

Set the account structure for the consumer subaccount.

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Subscribe to the SaaS solution. See [Subscribe to SaaS Solution](subscribe-to-saas-solution-477ea31.md).

</td>
<td valign="top">

 

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Configure consumer subaccount. See [Configure Consumer Subaccount](configure-consumer-subaccount-6301a27.md).

</td>
<td valign="top">

Configure customer subaccount.

-   Option A: provider configures the subaccount
-   Option B: customer configures subaccount



</td>
<td valign="top">

Consumer subaccount administrator

</td>
</tr>
<tr>
<td valign="top">

Initial user onboarding. See [Initial User Onboarding](initial-user-onboarding-4a9c501.md)

</td>
<td valign="top">

Create an initial administrator user for the customer.

</td>
<td valign="top">

Consumer subaccount administrator

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
<th valign="top">

User/Role

</th>
</tr>
<tr>
<td valign="top" rowspan="3">

[Configure and Implement a Customer Project](configure-and-implement-a-customer-project-363d2ea.md)

</td>
<td valign="top">

Set up Identity and Access Management in the consumer tenant of the customer.

</td>
<td valign="top">

Create and assign business roles.

Create spaces and pages for business roles.

</td>
<td valign="top">

Business user

</td>
</tr>
<tr>
<td valign="top">

Integrate the customer project in the consumer tenant of the customer.

</td>
<td valign="top">

Create communication arrangements.

</td>
<td valign="top">

Business user

</td>
</tr>
<tr>
<td valign="top">

Configure the customer project in the consumer tenant of the customer.

</td>
<td valign="top">

Create business configuration.

Configure key user extemsibility.

</td>
<td valign="top">

Business user

</td>
</tr>
</table>



<a name="loio964054384acd445fae9e3a80278096a8__section_o2b_q1j_l4b"/>

## Maintain, Monitor, Support


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
<th valign="top">

User/Role

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

[Maintain](maintain-9721f0f.md)

</td>
<td valign="top">

Set up your test and maintenance system landscape and processes. See [Set Up Maintenance System Landscape](set-up-maintenance-system-landscape-4403545.md).

</td>
<td valign="top">

 

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Create an update. See [Create Add-On Update](create-add-on-update-a355823.md).

</td>
<td valign="top">

Create a new patch version, support package version, or release/product version. See[Deploy Product](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/c4da7bba8b5a46b9ae08986d9399046d.html).

</td>
<td valign="top">

-   Developer: implement update and double-maintenance
-   Test user: verify changes in test systems
-   Add-on administrator: check out maintenance branch, download API snapshots from the add-on build system as well as upload them to other systems, set the uploaded API snapshot as check-relevant, import software components into test systems, and configure the addon.yml file



</td>
</tr>
<tr>
<td valign="top">

Trigger the add-on product build. See [Trigger Add-On Build Pipeline](trigger-add-on-build-pipeline-7f6988a.md).

</td>
<td valign="top">

Trigger the execution of the configured ABAP environment pipeline for an add-on build. See[Operations Dashboard](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/66d17ae222254fd08ca2e5498fd41f60.html).

</td>
<td valign="top">

Add-on administrator

</td>
</tr>
<tr>
<td valign="top">

Apply update for SaaS solution \(=add-on product\). See [Deploy Add-On Update](deploy-add-on-update-0a80d4c.md).

</td>
<td valign="top">

Deploy your add-on update by using the Landscape Portal.

See [Landscape Portal](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/6aa0a773510e4c82b167fcca4c755327.html).

</td>
<td valign="top">

Operator

</td>
</tr>
<tr>
<td valign="top">

Troubleshoot and debug. See [Troubleshoot and Debug](troubleshoot-and-debug-3687b52.md).

</td>
<td valign="top">

-   Identify ABAP system and consumer tenant
-   Access the consumer tenant of the ABAP system
-   Troubleshoot



</td>
<td valign="top">

 

</td>
<td valign="top">

Operator

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
<th valign="top">

User/Role

</th>
</tr>
<tr>
<td valign="top" rowspan="2">

[Dismantle](dismantle-35a5882.md)

</td>
<td valign="top">

Delete tenants.

</td>
<td valign="top">

Unsubscribe the SaaS solution. See [Dismantle](dismantle-35a5882.md).

</td>
<td valign="top">

Consumer subaccount administrator or operator using Subscription Management Dashboard

</td>
</tr>
<tr>
<td valign="top">

\(Optional\) Restore deleted tenants.

</td>
<td valign="top">

Restore the deleted tenants within a grace period of 30 days. See [Dismantle](dismantle-35a5882.md).

</td>
<td valign="top">

Operator

</td>
</tr>
</table>

