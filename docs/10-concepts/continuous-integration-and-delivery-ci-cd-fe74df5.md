<!-- loiofe74df55b0f54e99bf6e13a3b53e1db0 -->

# Continuous Integration and Delivery \(CI/CD\)

Configure and run predefined continuous integration and delivery \(CI/CD\) pipelines that automatically build, test, and deploy your code changes to speed up your development and delivery cycles.

> ### Note:  
> For links to all SAP solutions for CI/CD, blog posts, presentations, and tutorials, have a look at our [Continuous Integration and Delivery by SAP](https://help.sap.com/viewer/product/CICD_OVERVIEW/Cloud/en-US?task=discover_task) overview.

**Continuous integration \(CI\)** describes a software development process, in which various team members integrate their contributions frequently into a single main line. Before each integration, the changes are verified through builds and automated testing. Thereby, you can detect errors as quickly as possible and prevent integration problems before completing the development.

The **continuous delivery \(CD\)** concept expands on the one of continuous integration. It adds the aspect that any change that has successfully passed the tests is immediately ready to be deployed to production, both from a technical and a qualitative point of view.

The following graphic shows the basic flow for continuous integration and delivery:

   
  
Continuous Integration Basic Flow

 ![](images/ci-basic-flow-copy_b835ff9.png "Continuous Integration Basic Flow") 

For more information about the continuous integration and continuous delivery concepts, see [What Are Continuous Integration and Continuous Delivery?](https://help.sap.com/viewer/8cacec64ed854b2a88e9a0973e0f97a2/Cloud/en-US/5ba483a2c97b4ad5ab0148f4a6c5a9ee.html).



<a name="loiofe74df55b0f54e99bf6e13a3b53e1db0__section_tlr_g4n_nkb"/>

## Use

Depending on your use case, you can choose between different CI/CD pipelines to help you implement continuous integration and delivery in your software development.

SAP Continuous Integration and Delivery lets you configure and run predefined pipelines for the development of the following applications:

-   [SAP Cloud Application Programming Model](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/7c2a049670f64993b9d67c8f84ba0969.html) 

    Configure a CI/CD pipeline for the development of applications that follow the SAP Cloud Application Programming Model in the Cloud Foundry environment.

-   [SAP Fiori in the Cloud Foundry Environment](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/8887fe3c5445442b915d3c066c010d75.html)

    Configure a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications in the Cloud Foundry environment.

-   [SAP Fiori in the Neo environment](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/1302e9ae408b4dc38d7109c75db9aa75.html)

    Configure a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications in the Neo environment.

-   [SAP Integration Suite Artifacts](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/019ed685a19b4efab4f7df0e108d1697.html)

    Configure a CI/CD pipeline for the development of SAP Cloud Integration artifacts in the Cloud Foundry environment.

-   [Container-Based Applications](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/10970393828c46498806d1b322cf05a4.html)

    Configure a CI/CD pipeline for the development of container-based applications.


To learn more about the CI/CD pipelines supported by SAP Continuous Integration and Delivery and the stages each pipeline can comprise, see[Supported Pipelines](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/e293286b06df426ab1cfa235332a2606.html).



<a name="loiofe74df55b0f54e99bf6e13a3b53e1db0__section_bq2_rvv_gsb"/>

## Get Started with CI/CD

SAP Continuous Integration and Delivery provides an easy, UI-guided way to set up the service and configure and run your pipelines, without hosting your own Jenkins instance.

To set up SAP Continuous Integration and Delivery:

1.  Enable the service in the SAP BTP cockpit.
2.  Assign either the *Administrator* or *Developer* role to your user.
3.  Enable the API usage to connect SAP Continuous Integration and Delivery to other services, if necessary.

To configure SAP Continuous Integration and Delivery:

> ### Note:  
> Only administrators of SAP Continuous Integration and Delivery can configure the service.

1.  Configure credentials for connecting SAP Continuous Integration and Delivery to other services \(for example, GitHub, GitLab or Bitbucket Server to clone your sources, and SAP BTP to deploy your built application\).

2.  Add your repository.


Now you can create and modify your CI/CD jobs and monitor their outcome. If you want to automate your builds, you can configure a webhook between your repository and the service. You can create and modify timed triggers for your jobs, if necessary.

For more information, see [Initial Setup](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/719acaf61e4b4bf0a496483155c52570.html) and [Configuration](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/39d0c2f0626f4303872e49b627b5c616.html), or follow the tutorial [Configure and Run a Predefined SAP Continuous Integration and Delivery \(CI/CD\) Pipeline](https://developers.sap.com/tutorials/btp-app-ci-cd-btp.html).



<a name="loiofe74df55b0f54e99bf6e13a3b53e1db0__section_kl1_g4n_nkb"/>

## Learn and Get Certified

Depending on your learning goals and level of expertise, you can choose from the following offerings:

-   **[Continuous Integration and Continuous Delivery on Learning Journey](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/b76f0b2e5d534c449c1f3b0fa84ab697.html)**

    Our learning journey is a visual guide that helps you complete the learning path for CI/CD on SAP BTP. It makes you understand the practices and principles of continuous integration and delivery, provides the opportunity to gather hands-on experience, and helps you improve your skills in CI/CD.

    For more information about Learning Journeys, see [Jump-start your Learning](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/0d7dd0dc8f464586a187b9b6c27c6b23.html).

-   **[Continuous Integration and Delivery Introduction Guide](https://help.sap.com/viewer/ee5a61247061455ab232c19179fe4c3b/Cloud/en-US)**

    The CI/CD Introduction Guide provides you with basic knowledge for setting up and implementing continuous integration and delivery processes. It gives an overview of the concepts and principles of CI/CD, explains both procedures and their relation, and helps you plan your own CI/CD process.


