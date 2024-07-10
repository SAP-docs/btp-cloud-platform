<!-- loio40a8f8f6f1724e0ca0fd2a8777f45504 -->

# Development in the Cloud Foundry Environment

Learn more about developing applications on the SAP BTP, Cloud Foundry environment.



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_jms_z5d_53b"/>

## Overview

SAP BTP, Cloud Foundry environment is an open Platform-as-a-Service \(PaaS\) targeted at microservice development and orchestration.


<dl>
<dt><b>

Develop polyglot applications 

</b></dt>
<dd>

Build on open standards with SAP Java, Node.js, and Python buildpacks or bring your own language with community buildpacks for PHP, Ruby, Go.



</dd><dt><b>

Manage the lifecycle of applications 

</b></dt>
<dd>

Start, stop, scale, and configure distributed cloud applications using standard Cloud Foundry tools, our web-based administration user interface for SAP BTP, and dev-ops capabilities.



</dd><dt><b>

Optimize development and operations 

</b></dt>
<dd>

Use the rich set of SAP BTP services including messaging, persistence, and many other capabilities, such as built-in security, compliance, elastic scale, and high-availability setup.



</dd><dt><b>

Use the application programming model 

</b></dt>
<dd>

Use programming languages, libraries, and APIs tailored for full-stack application development.



</dd><dt><b>

Manage Cloud Foundry orgs and spaces 

</b></dt>
<dd>

Create and delete Cloud Foundry orgs and spaces and add members. Create, assign, and change space quota plans.



</dd><dt><b>

Use built-in cloud-native capabilities 

</b></dt>
<dd>

Utilize cloud-native principles built into the platform, such as containerization and multitenancy, to create resilient, portable, and efficient applications.



</dd>
</dl>



The following graphic is designed to help you find the information you need for your programming purposes. The bottom row represents the tools, frameworks, services, and deployment options recommended by SAP. If you want full flexibility you can also bring your own development tools and languages, as shown in the top row.



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_wqt_z5l_tnb"/>

## Development Options Overview

![](images/Development_Options_Overview_1_1_1f5671e.png)



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_ifw_4vl_tnb"/>

## The Recommended Path

This development approach offers guidance for important development decisions and features proven best practices recommended by SAP. You can follow a model path for application and service development that is based on the Cloud Application Programming Model \(CAP\). When working with CAP, we recommend using Java and Node.js because they receive the highest level of tool support and are well suited for most use cases. This path provides you with a list of key aspects to consider, but the order shown in these steps isn't mandatory. You can adapt the steps as you wish to better fit your use case.



<a name="loio40a8f8f6f1724e0ca0fd2a8777f45504__section_skx_qfs_4nb"/>

## Choose Your Own Path

Because of the polyglot nature of the Cloud Foundry environment, you're also free to choose your own approach. You're not forced to use one language exclusively, but can choose between Java, Node.js, and Python. Concerning tools you can either use the Cloud Foundry Command Line Interface \(CF CLI\) or other tools to develop and deploy your application. You're also free to decide if you want to develop and deploy your applications in the multitarget format \(MTA\).

For more information on the supported programming languages, see:

-   [Developing Java in the Cloud Foundry Environment](developing-java-in-the-cloud-foundry-environment-a3f9006.md)

-   [Developing Node.js in the Cloud Foundry Environment](developing-node-js-in-the-cloud-foundry-environment-3a7a0be.md)

-   [Developing Python in the Cloud Foundry Environment](developing-python-in-the-cloud-foundry-environment-acf8f49.md)




If you already have monolithic applications running on SAP BTP and are looking for a way to run them in the Cloud Foundry environment, read our migration best practice guide. See [Migrating from the Neo Environment to the Multi-Cloud Foundation for SAP BTP (Cloud Foundry and Kyma)](https://help.sap.com/viewer/b017fc4f944e4eb5b31501b3d1b6a1f0/Cloud/en-US/aae4e0ae1cdf434b908c3c8cf3ea942a.html "Learn why and how to migrate scenarios from the Neo environment to the multi-cloud foundation for SAP BTP. This guide is for SAP Business Technology Platform (SAP BTP) customers with scenarios in the Neo environment that need to move to the multi-cloud foundation, including the Cloud Foundry environment or the Kyma environment.") :arrow_upper_right:.

**Related Information**  


[Cloud Foundry Environment](../10-concepts/cloud-foundry-environment-9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18 "The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. It contains the SAP BTP, Cloud Foundry runtime service, which is based on the open-source application platform managed by the Cloud Foundry Foundation.")

[Troubleshooting App Deployment and Health](https://docs.cloudfoundry.org/devguide/deploy-apps/troubleshoot-app-health.html)

[SAP BTP, Cloud Foundry Runtime](https://help.sap.com/docs/CF_RUNTIME?version=Cloud)

