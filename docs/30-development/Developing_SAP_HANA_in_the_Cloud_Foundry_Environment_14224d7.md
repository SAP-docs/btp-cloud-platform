<!-- loio14224d75f6c64b499d189e3ebd131ec2 -->

# Developing SAP HANA in the Cloud Foundry Environment

Find here selected information for SAP HANA database development and references to more detailed sources.



This section gives you information about database development and its surrounding tasks especially if you want to explore the SAP BTP, Cloud Foundry environment. To get more into detail, we have references to other guides and the SAP HANA Cloud service documentation. The context we’re looking at is multitarget application \(MTA\) development, whereby SAP HANA is the database module and you develop all artifacts in that module.

There are multiple scenarios when you start using SAP HANA Cloud in the SAP BTP, Cloud Foundry environment. For each of these scenarios, we give you a recommendation:


<table>
<tr>
<th>

Scenario



</th>
<th>

Recommendation



</th>
</tr>
<tr>
<td>

You're starting a new project and want to leverage SAP HANA capabilities in the cloud.



</td>
<td>

We recommend using the SAP Cloud Application Programming Model and SAP HANA Cloud.

See [SAP HANA Cloud](Developing_SAP_HANA_in_the_Cloud_Foundry_Environment_14224d7.md#loioa697b1b1b5ad4b598378ff0fa091fa35)



</td>
</tr>
<tr>
<td>

You're using SAP HANA service for SAP BTP and SAP HANA Platform 2.0 \(XS advanced\) on-premise.



</td>
<td>

Get to know the differences. Read about features that have been supported by other SAP HANA versions but aren’t supported by SAP HANA Cloud: [SAP HANA Cloud Compatibility Reference](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/cloud/en-US/3101cb652bb74739a3e39593ea969bc5.html) 



</td>
</tr>
<tr>
<td>

You're using SAP HANA Platform 2.0 \(XS advanced\) on-premise.



</td>
<td>

SAP HANA extended application services, advanced model, \(XS advanced\) as the runtime environment for SAP HANA Platform was built similar to the Cloud Foundry environment. It has been developed further and therefore contains features that aren’t available in Cloud Foundry. Some features aren’t supported from the SAP HANA versions in the cloud. So, there’s always some effort, at least when you reach a decent amount of complexity, to make an XS advanced application run in the cloud.

The new SAP HANA Cloud service made significant moves to reduce footprint and be cloud-ready. Therefore, previously deprecated features have been removed. Read about features that have been supported by other SAP HANA versions but aren’t supported by SAP HANA Cloud: [SAP HANA Cloud Compatibility Reference](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/cloud/en-US/3101cb652bb74739a3e39593ea969bc5.html) 

You can find another collection of these features and elements in the following SAP Note:[2868742](https://launchpad.support.sap.com/#/notes/2868742) 

Have a look at the section *HDI features are not available with SAP HANA Cloud*, which is the most important part in this scenario.



</td>
</tr>
<tr>
<td>

You're using SAP HANA Platform 1.0 \(XS classic\) on-premise. This scenario also includes any usage of XS classic artifacts even if you use XS advanced \(compatibility\) or the Neo environment



</td>
<td>

This scenario is presumably a bigger project. The task isn’t only to use a different version of SAP HANA but also to make architectural changes: from monolithic applications to microservice-based applications. To give you an overview on things you need to consider, have a look at our guide: [Migrating from the Neo Environment to the Multi-Cloud Foundation (Cloud Foundry and Kyma)](https://help.sap.com/viewer/b017fc4f944e4eb5b31501b3d1b6a1f0/Cloud/en-US/aae4e0ae1cdf434b908c3c8cf3ea942a.html "Learn why and how to migrate your scenarios on SAP Business Technology Platform (SAP BTP) from the Neo environment to the multi-cloud foundation.") :arrow_upper_right: 



</td>
</tr>
</table>

 <a name="loio14224d75f6c64b499d189e3ebd131ec2 loioa697b1b1b5ad4b598378ff0fa091fa35__loioa697b1b1b5ad4b598378ff0fa091fa35"/>

<!-- loioa697b1b1b5ad4b598378ff0fa091fa35 -->

# SAP HANA Cloud



This section is a quick introduction to the latest SAP HANA offering on SAP BTP, Cloud Foundry environment. In essence, you get to know the most important tools and information about data modeling. This content is meant to provide an overview. Please follow the links to the content you’re interested in and start your learning journey.



### Tools

There are two tools you need to know, SAP Web IDE Full-Stack and SAP HANA Cockpit.

-   SAP Web IDE Full-Stack

    SAP Web IDE Full-Stack is the recommended tool to develop your SAP HANA database artifacts, see [SAP Web IDE Full-Stack \> Getting Started](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/995af3aa09074ceca20e59011ef78529.html)

    For an SAP Cloud Application Programming Model project, we recommend starting your project in SAP Web IDE Full-Stack and synchronize it with GitHub, see [SAP Web IDE Full-Stack \> Using Source Control \(Git\)](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/4eddb4cfc29946f6b059306cbdfcb392.html)

    That way, you leverage the power of SAP Web IDE for developing database artifacts. At the same time you can use the more mature tooling for service development, which resides in Visual Studio Code and SAP Business Application Studio.

-   SAP HANA Cockpit

    The SAP HANA Cockpit is used to monitor and administer your SAP HANA instances, see [Set Up SAP HANA Cockpit for the First Time](https://help.sap.com/viewer/afa922439b204e9caf22c78b6b69e4f2/2.12.0.0/en-US/3188e43e196c46e5a26989f22e18f130.html)

    To learn how to access the SAP HANA Cockpit from the SAP Cloud Cockpit, see [Accessing SAP HANA Cockpit for SAP HANA Cloud](https://help.sap.com/viewer/9630e508caef4578b34db22014998dba/cloud/en-US/ef52446052e14f7ca0783113c08fd515.html)




### Data Modeling

To develop your data model, we recommend the SAP Cloud Application Programming Model.

-   The SAP Cloud Application Programming Model \(CAP\) provides a guide explaining the concepts and best practices of domain modeling using CAP CDS, see [Domain Modeling](https://cap.cloud.sap/docs/guides/domain-models)

-   To define your data models, queries and expressions, there’s a CAP CDS reference guide. It contains samples and best practices that support your learning journey. See [Core Data Services \(CDS\) - Language Reference Documentation for the application programming model](https://cap.cloud.sap/docs/cds).

-   You have existing database objects and want to use them with CAP CDS. Learn about facade entities in CAP CDS and how to design them. See [Native SAP HANA](https://cap.cloud.sap/docs/advanced/hana).


When you've created your data model with the SAP Cloud Application Programming Model, you want to leverage more of the SAP HANA power. The SAP HANA Cloud documentation provides an extensive library of guides. Find here selected links that make an easy start.

-   [SAP HANA Cloud Modeling Guide for SAP Web IDE Full-Stack](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/cloud/en-US/307c939cc3354280a257ed0fe2e40196.html)

-   [SAP HANA Cloud product page, development overview](https://help.sap.com/viewer/product/DRAFT/HANA_CLOUD/cloud/en-US?task=develop_task)




### References

-   [SAP HANA Cloud product page on the Help Portal](https://help.sap.com/viewer/product/HANA_CLOUD/cloud/en-US)

-   [Feature Scope Description for SAP HANA Cloud](https://help.sap.com/viewer/5b0a45d84713461084c26b6a31533fd0/cloud/en-US)


