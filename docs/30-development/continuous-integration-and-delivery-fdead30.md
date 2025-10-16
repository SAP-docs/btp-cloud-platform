<!-- loiofdead30953d24c0ca75768e2c3bcdd2c -->

# Continuous Integration and Delivery

Learn how to integrate CI/CD into your development with the SAP Cloud Application Programming Model \(CAP\).

<a name="loio31cbeccf367e465fa3fc83e367c9c6f1"/>

<!-- loio31cbeccf367e465fa3fc83e367c9c6f1 -->

## What Are Continuous Integration and Delivery?

**Continuous Integration \(CI\)** describes a software development process in which various team members frequently integrate their contributions into a single main line. Before each integration, the changes are verified through builds and automated testing. This allows you to detect errors as quickly as possible and prevent integration problems before completing the development.

  
  
**Continuous Integration Flow**

![Continuous Integration Flow](images/Image_Map_CI_CD_Basic_Flow_c205ab7.png "Continuous Integration Flow")

The basic flow of Continuous Integration comprises the following steps:

1.  The Developer writes code and pushes the code changes into a repository on a central source code management system \(SCM\).

2.  The Source Code Management System triggers the Continuous Integration \(CI\) server.

3.  The Continuous Integration server runs automated builds and tests and sends feedback about their outcome to the Developer.




As you can see from the figure above, Continuous Integration is a cycle: as soon as the CI server has sent its feedback to the developer, the flow starts over again. The developers either correct their previous code change, which must then be built and tested again, or start working on an entirely new one.

The **Continuous Delivery \(CD\)** concept expands on the one of continuous integration. It adds the aspect that any change that has successfully passed the tests is immediately ready to be deployed to production, both from a technical and qualitative point of view.

The following graphic shows the relation between Continuous Integration and Continuous Delivery:

  
  
**Relation Between CI and CD**

![Relation Between CI and CD](images/Continuous_Integration_vs_Continuous_Delivery_dd91996.png "Relation Between CI and CD")

The Continuous Delivery process ensures that the most current version is successfully built, tested, and provided in a shippable format. Based on the release decision by the development team or delivery manager, it can be shipped to customers or deployed to production at any time.

For more information about the concepts and principles of Continuous Integration and Continuous Delivery, see the [Continuous Integration and Delivery Introduction Guide](https://help.sap.com/viewer/Continuous-Integration-and-Delivery-Introduction-Guide/7fc38a80cda446ef856c01f748dbede8.html).

<a name="loio862ec834e72842a6b027d8d1518055dd"/>

<!-- loio862ec834e72842a6b027d8d1518055dd -->

## SAP Continuous Integration and Delivery

[**SAP Continuous Integration and Delivery**](https://help.sap.com/viewer/product/CONTINUOUS_DELIVERY/Cloud/en-US) is a service on SAP BTP that helps development teams collaborate more effectively, improve the quality of their software, and speed up their delivery process. It provides ready-made CI/CD pipelines for SAP-specific use cases that can be connected to a source repository to automatically build, test, and deploy code changes. This helps identify issues and prevent integration problems at an early stage in the development process.

The Continuous Integration & Delivery service focuses on two key benefits: **Simplicity** and **Flexibility**.



<a name="loio862ec834e72842a6b027d8d1518055dd__section_fbf_zr4_5nb"/>

## Simplicity

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines that can be used out of the box. Depending on the development scenario they are used for, they only require minimal configuration. This means that even users without expertise in CI/CD can easily leverage the service for their needs. Additionally, the service includes the necessary infrastructure, freeing you from having to manage it yourself.



<a name="loio862ec834e72842a6b027d8d1518055dd__section_xl4_2ww_jgc"/>

## Flexibility

By offering the ability to customize pipelines with additional commands, credentials, and variables, SAP Continuous Integration and Delivery provides a high degree of flexibility. With this option, the service does not only cover standard use cases, but also addresses more complex scenarios. Additional commands enable you to expand your pipelines with various tasks that are executed before or after a certain stage. Additionally, extra credentials and variables allow you to further customize your CI/CD jobs.



<a name="loio862ec834e72842a6b027d8d1518055dd__section_axb_qww_jgc"/>

## SAP Continuous Integration and Delivery for CAP

For how to configure a CI/CD pipeline for the development of applications that follow the SAP Cloud Application Programming Model, see [Get Started with an SAP Cloud Application Programming Model Project in SAP Continuous Integration and Delivery](https://developers.sap.com/tutorials/cicd-start-cap.html) \(tutorial\) and [Configure a Cloud Foundry Environment Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-job-editor?language=en-US) \(documentation\).

