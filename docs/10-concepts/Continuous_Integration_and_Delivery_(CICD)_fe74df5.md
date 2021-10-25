<!-- loiofe74df55b0f54e99bf6e13a3b53e1db0 -->

# Continuous Integration and Delivery \(CI/CD\)

Depending on your use case, you can choose between different offerings for continuous integration and delivery.

> ### Note:  
> For links to all SAP solutions for CI/CD, blog posts, presentations, and tutorials, have a look at our [Continuous Integration and Delivery by SAP](https://help.sap.com/viewer/product/CICD_OVERVIEW/Cloud/en-US?task=discover_task) overview.

**Continuous integration \(CI\)** describes a software development process, in which various team members integrate their contributions frequently into a single main line. Before each integration, the changes are verified through builds and automated testing. Thereby, you can detect errors as quickly as possible and prevent integration problems before completing the development.

The following graphic shows the basic flow for continuous integration:

   
  
Continuous Integration Basic Flow

 ![Continuous Integration Basic Flow](images/Continuous_Integration_Basic_Flow_87a814e.png "Continuous Integration Basic Flow") 

The **continuous delivery \(CD\)** concept expands on the one of continuous integration. It adds the aspect that any change that has successfully passed the tests is immediately ready to be deployed to production, both from a technical and a qualitative point of view.

For more information about the continuous integration and continuous delivery concepts, see [What Are Continuous Integration and Continuous Delivery?](https://help.sap.com/viewer/8cacec64ed854b2a88e9a0973e0f97a2/Cloud/en-US/5ba483a2c97b4ad5ab0148f4a6c5a9ee.html).



<a name="loiofe74df55b0f54e99bf6e13a3b53e1db0__section_tlr_g4n_nkb"/>

## Use

At the moment, SAP offers three different solutions that help you apply CI/CD in your software development:

-   [**SAP Continuous Integration and Delivery**](https://help.sap.com/viewer/product/CONTINUOUS_DELIVERY/Cloud/en-US)

    SAP Continuous Integration and Delivery is a service on SAP BTP, which lets you configure and run predefined continuous integration and delivery pipelines that test, build, and deploy your code changes. At the moment, it supports the development of SAP Cloud Application Programming Model \(CAP\) and SAPUI5/SAP Fiori applications.

    For more information, see [Meet Our New Continuous Integration and Delivery Solution](https://blogs.sap.com/2020/08/17/meet-our-new-continuous-integration-and-delivery-solution/).

-   **[Project "Piper"](https://sap.github.io/jenkins-library/)**

    Project "Piper" is an open-source project that provides preconfigured Jenkins pipelines, which you can use in your own Jenkins master infrastructure and adapt according to your needs, if necessary. It consists of two components:

    -   A [shared library](https://github.com/SAP/jenkins-library), which contains the description of steps, scenarios, and utilities required to use Jenkins pipelines

    -   A [set of Docker images](https://github.com/SAP/devops-docker-images) that can be used to implement best practice processes


-   **[Continuous Integration and Delivery Best Practices Guide](https://help.sap.com/viewer/3324745951b44b578bd65221d2ff8f9a/Cloud/en-US)**

    The CI/CD Best Practices Guide provides best practice procedures to implement continuous delivery pipelines on any CI/CD stack and demonstrates how to apply the principles of CI/CD to SAP-specific technologies.

    For more information, see [We’ve Finished Our Renovations: Our New CI/CD Best Practices](https://blogs.sap.com/2020/02/20/weve-finished-our-renovations-our-new-ci-cd-best-practices/).


To find your appropriate SAP solution for applying CI/CD, see [Which SAP Solution for CI/CD Meets Your Needs?](https://help.sap.com/viewer/Continuous-Integration-and-Delivery-by-SAP/e9fa320181124fa9808d4446a1bf69dd.html#loioa49d1ba1ecef4e9d96deffd127c4522d).



<a name="loiofe74df55b0f54e99bf6e13a3b53e1db0__section_kl1_g4n_nkb"/>

## Learn and Get Certified

Depending on your learning goals and level of expertise, you can choose from the following offerings:

-   **[Continuous Integration and Continuous Delivery on Learning Journey](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/b76f0b2e5d534c449c1f3b0fa84ab697.html)**

    Our learning journey is a visual guide that helps you complete the learning path for CI/CD on SAP BTP. It makes you understand the practices and principles of continuous integration and delivery, provides the opportunity to gather hands-on experience, and helps you improve your skills in CI/CD.

    For more information about Learning Journeys, see [Jump-start your Learning](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/0d7dd0dc8f464586a187b9b6c27c6b23.html).

-   **[Continuous Integration and Delivery Introduction Guide](https://help.sap.com/viewer/ee5a61247061455ab232c19179fe4c3b/Cloud/en-US)**

    The CI/CD Introduction Guide provides you with basic knowledge for setting up and implementing continuous integration and delivery processes. It gives an overview of the concepts and principles of CI/CD, explains both procedures and their relation, and helps you plan your own CI/CD process.


