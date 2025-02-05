<!-- loio2a21055cc94b4a528a820f73e6fa7d69 -->

# Deploying to the Cloud Foundry Environment

Get an overview of available deployment options.

When deploying applications and services to the cloud, you can choose from a number of different approaches and tools, depending on your development setup.



<a name="loio2a21055cc94b4a528a820f73e6fa7d69__section_obf_tyj_qnb"/>

## Multitarget Applications

If you've decided to develop your application or service with the multitarget approach, you can deploy it to SAP BTP using a single `.mtar` archive file. For more information, see [Multitarget Applications in the Cloud Foundry Environment](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md).



<a name="loio2a21055cc94b4a528a820f73e6fa7d69__section_sm1_5yj_qnb"/>

## Continuous Integration and Delivery

Continuous Integration and Delivery \(CI/CD\) are two interrelated concepts that can enhance your development process by adding frequent integration, automated testing, and faster delivery. For more information, see [Continuous Integration and Delivery](continuous-integration-and-delivery-fdead30.md#loiofdead30953d24c0ca75768e2c3bcdd2c) .



<a name="loio2a21055cc94b4a528a820f73e6fa7d69__section_gg2_vyj_qnb"/>

## Cloud Foundry Command Line Interface

If you prefer to develop on your local machine, you can deploy your application from the folder on your computer directly to SAP BTP using the Cloud Foundry Command Line Interface \(CF CLI\). For more information, see [Deploy Business Applications in the Cloud Foundry Environment](deploy-business-applications-in-the-cloud-foundry-environment-4946ea5.md).



<a name="loio2a21055cc94b4a528a820f73e6fa7d69__section_zmb_v33_12c"/>

## SAP BTP Cockpit

You can also deploy your application with or without a `manifest.yml` file using the SAP BTP cockpit. For more information, see [Deploy an Application](../50-administration-and-ops/deploy-an-application-09fdb9b.md).



<a name="loio2a21055cc94b4a528a820f73e6fa7d69__section_gft_wyj_qnb"/>

## Docker Images

If you want a higher degree of freedom when realizing your project, you can also deploy your applications and services using Docker images and the Cloud Foundry Command Line Interface \(CF CLI\). Note that Docker images can't be used in combination with buildpacks. For more information, see [Deploy Docker Images in the Cloud Foundry Environment](deploy-docker-images-in-the-cloud-foundry-environment-c190ad6.md).

