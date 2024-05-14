<!-- loio14224d75f6c64b499d189e3ebd131ec2 -->

# Developing SAP HANA in the Cloud Foundry Environment

Find here selected information for SAP HANA database development and references to more detailed sources.



This section gives you information about database development and its surrounding tasks especially if you want to explore the SAP BTP, Cloud Foundry environment. To get more into detail, we have references to other guides and the SAP HANA Cloud service documentation. The context we’re looking at is multitarget application \(MTA\) development, whereby SAP HANA is the database module and you develop all artifacts in that module.

There are multiple scenarios when you start using SAP HANA Cloud in the SAP BTP, Cloud Foundry environment. For each of these scenarios, we give you a recommendation:


<table>
<tr>
<th valign="top">

Scenario

</th>
<th valign="top">

Recommendation

</th>
</tr>
<tr>
<td valign="top">

You're starting a new project and want to leverage SAP HANA capabilities in the cloud.

</td>
<td valign="top">

We recommend using the SAP Cloud Application Programming Model and SAP HANA Cloud.

See [SAP HANA Cloud](developing-sap-hana-in-the-cloud-foundry-environment-14224d7.md#loioa697b1b1b5ad4b598378ff0fa091fa35)

</td>
</tr>
<tr>
<td valign="top">

You're using SAP HANA service for SAP BTP and SAP HANA Platform 2.0 \(XS advanced\) on-premise.

</td>
<td valign="top">

Get to know the differences. Read about features that have been supported by other SAP HANA versions but aren’t supported by SAP HANA Cloud: [SAP HANA Cloud Compatibility Reference](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/cloud/en-US/3101cb652bb74739a3e39593ea969bc5.html) 

</td>
</tr>
<tr>
<td valign="top">

You're using SAP HANA Platform 2.0 \(XS advanced\) on-premise.

</td>
<td valign="top">

SAP HANA extended application services, advanced model, \(XS advanced\) as the runtime environment for SAP HANA Platform was built similar to the Cloud Foundry environment. It has been developed further and therefore contains features that aren’t available in Cloud Foundry. Some features aren’t supported from the SAP HANA versions in the cloud. So, there’s always some effort, at least when you reach a decent amount of complexity, to make an XS advanced application run in the cloud.

The new SAP HANA Cloud service made significant moves to reduce footprint and be cloud-ready. Therefore, previously deprecated features have been removed. Read about [SAP HANA Cloud Compatibility and Migration Information](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/9c8656d9c1a34c829fab426cb77b4639.html):

-   [High Level Feature Compatibility](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/e131e792973348d1ac072590fe3d137c.html)

-   [Design-time Content Compatibility](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/9c8656d9c1a34c829fab426cb77b4639.html)


You can find another collection of these features and elements in the following SAP Note:[2868742](https://me.sap.com/notes/2868742) 

</td>
</tr>
<tr>
<td valign="top">

You're using SAP HANA Platform 1.0 \(XS classic\) on-premise. This scenario also includes any usage of XS classic artifacts even if you use XS advanced \(compatibility\) or the Neo environment

</td>
<td valign="top">

This scenario is presumably a bigger project. The task isn’t only to use a different version of SAP HANA but also to make architectural changes: from monolithic applications to microservice-based applications. To give you an overview on things you need to consider, have a look at our guide: [Migrating from the Neo Environment to the Multi-Cloud Foundation for SAP BTP (Cloud Foundry and Kyma)](https://help.sap.com/viewer/b017fc4f944e4eb5b31501b3d1b6a1f0/Cloud/en-US/aae4e0ae1cdf434b908c3c8cf3ea942a.html "Learn why and how to migrate scenarios from the Neo environment to the multi-cloud foundation for SAP BTP. This guide is for SAP Business Technology Platform (SAP BTP) customers with scenarios in the Neo environment that need to move to the multi-cloud foundation, including the Cloud Foundry environment or the Kyma environment.") :arrow_upper_right: 

</td>
</tr>
</table>

<a name="loioa697b1b1b5ad4b598378ff0fa091fa35"/>

<!-- loioa697b1b1b5ad4b598378ff0fa091fa35 -->

## SAP HANA Cloud



This section is a quick introduction to the latest SAP HANA offering on SAP BTP, Cloud Foundry environment. In essence, you get to know the most important tools and information about data modeling. This content is meant to provide an overview. Please follow the links to the content you’re interested in and start your learning journey.



### Tools

There are two tools you need to know, SAP Business Application Studio and SAP HANA Cockpit.

-   SAP Business Application Studio

    SAP Business Application Studio is the recommended tool to develop your SAP HANA database artifacts.

    You can use an [SAP HANA Native Application](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/7eae9c5e799e4f70946114f74f413ae9.html?version=Cloud) dev space, which is preconfigured to support the creation of database artifacts.

    For SAP Cloud Application Programming Model projects, we recommend to create a [Full Stack Cloud Application](https://help.sap.com/products/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/de0af65a0d764bf3b40d2c2352c08393.html?version=Cloud) dev space and add the following extensions:

    -   SAP HANA Calculation View Editor

    -   SAP HANA Tools

    -   SAP HANA Smart Data Integration Tools


    With that configuration you have the editors and tools for the programming model and SAP HANA database artifacts.

-   SAP HANA Cockpit

    The SAP HANA Cockpit is used to monitor and administer your SAP HANA instances, see [Open the SAP HANA Cockpit](https://help.sap.com/viewer/9ae9104a46f74a6583ce5182e7fb20cb/hanacloud/en-US/18fde2ad1da742d79aebd943a1aa71cd.html)

    To learn how to access the SAP HANA Cockpit, see [Accessing SAP HANA Cockpit for SAP HANA Cloud](https://help.sap.com/viewer/9630e508caef4578b34db22014998dba/cloud/en-US/ef52446052e14f7ca0783113c08fd515.html)




### Data Modeling

To develop your data model, we recommend the SAP Cloud Application Programming Model.

-   The SAP Cloud Application Programming Model \(CAP\) provides a guide explaining the concepts and best practices of domain modeling using CAP CDS, see [Domain Modeling](https://cap.cloud.sap/docs/guides/domain-modeling)

-   To define your data models, queries and expressions, there’s a CAP CDS reference guide. It contains samples and best practices that support your learning journey. See [Core Data Services \(CDS\) - Language Reference Documentation for the application programming model](https://cap.cloud.sap/docs/cds).

-   You have existing database objects and want to use them with CAP CDS. Learn about facade entities in CAP CDS and how to design them. See [Native SAP HANA](https://cap.cloud.sap/docs/guides/databases-hana).


When you've created your data model with the SAP Cloud Application Programming Model, you want to leverage more of the SAP HANA power. The SAP HANA Cloud documentation provides an extensive library of guides. Find here selected links that make an easy start.

-   [SAP HANA Cloud Modeling Guide for SAP Web IDE Full-Stack](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/cloud/en-US/307c939cc3354280a257ed0fe2e40196.html)

-   [SAP HANA Cloud product page, development overview](https://help.sap.com/viewer/product/DRAFT/HANA_CLOUD/cloud/en-US?task=develop_task)




### References

-   [SAP HANA Cloud product page on the Help Portal](https://help.sap.com/viewer/product/HANA_CLOUD/cloud/en-US)

-   [Feature Scope Description for SAP HANA Cloud](https://help.sap.com/viewer/5b0a45d84713461084c26b6a31533fd0/cloud/en-US)


