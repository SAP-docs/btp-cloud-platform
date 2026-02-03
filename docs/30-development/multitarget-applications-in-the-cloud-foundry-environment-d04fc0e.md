<!-- loiod04fc0e2ad894545aebfd7126384307c -->

# Multitarget Applications in the Cloud Foundry Environment

A Multitarget application \(MTA\) is essentially a single application that consists of multiple parts. These parts are created using various technologies and share the same lifecycle.

The MTA developers outline the intended outcomes using the MTA model. This model consists of MTA modules, MTA resources, and the interdependencies between them. Afterward, the SAP Cloud Deployment service validates it, orchestrates the necessary actions, and automates the MTA deployment. The outcome is the formation of Cloud Foundry applications, services, and the generation of SAP specific content. For more information about the Multitarget Application model, see the official specification documents [The Multitarget Application Model v.2](https://help.sap.com/doc/multitarget-application-modelv2/Cloud/en-US/The%20Multitarget%20Application%20Model.pdf) and [The Multitarget Application Model v.3](https://help.sap.com/doc/multitarget-application-modelv3/Cloud/en-US/The%20Multitarget%20Application%20M%D0%BEdel.pdf).

You can create and deploy a Multitarget Application in the Cloud Foundry environment as described below by following different approaches that can yield the same result:

-   Using SAP Web IDE Full-Stack as described in [Developing Multitarget Applications](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/a71bf8281254489ea8be6e323199b304.html) - both the development descriptor `mta.yaml` and the deployment descriptor `mtad.yaml` are created automatically. The `mta.yaml` is generated when you create the application project, and the `mtad.yaml` file is created when you build the project.

    > ### Note:  
    > You may still need to edit the development descriptor.

    Development descriptors are used to generate MTA deployment descriptors, which define the required deployment data. That is, the MTA development descriptor data specifies what you want to build, how to build it, while the deployment descriptor data specifies as what and how to deploy it.

    ![](images/DevelopWithWebIDE_4d4b82d.png)

    -   [https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/a71bf8281254489ea8be6e323199b304.html](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/a71bf8281254489ea8be6e323199b304.html)
    -   [https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/3b533e3723674fad90f94510b92f10af.html](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/3b533e3723674fad90f94510b92f10af.html)
    -   [https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/1b0a7a0938944c7fac978d4b8e23a63f.html](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/1b0a7a0938944c7fac978d4b8e23a63f.html)

-   Using Business Application Studio - the flow is similar to WebIDE but the development is done from BAS.

    ![](images/Image_Map_DevelopWithBAS_286f9b2.png)

    -   [https://help.sap.com/docs/bas/sap-business-application-studio/mta-development/](https://help.sap.com/docs/bas/sap-business-application-studio/mta-development/)
    -   [https://help.sap.com/docs/bas/sap-business-application-studio/building-and-deploying-multitarget-applications](https://help.sap.com/docs/bas/sap-business-application-studio/building-and-deploying-multitarget-applications)
    -   [https://help.sap.com/docs/bas/sap-business-application-studio/building-and-deploying-multitarget-applications](https://help.sap.com/docs/bas/sap-business-application-studio/building-and-deploying-multitarget-applications)

-   Using the [Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/). Afterward, you deploy the MTA using the Cloud Foundry Command Line Interface.

    > ### Note:  
    > An MTA development descriptor `mta.yaml` is required. You have to create it manually.

    ![](images/DevelopWithoutWebIDE_13b1b8a.png)

    -   [https://sap.github.io/cloud-mta-build-tool/](https://sap.github.io/cloud-mta-build-tool/)
    -   [https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/65ddb1b51a0642148c6b468a759a8a2e.html](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/65ddb1b51a0642148c6b468a759a8a2e.html)
    -   [https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c2d31e70a86440a19e47ead0cb349fdb.html](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c2d31e70a86440a19e47ead0cb349fdb.html)

-   Manually - create the required files manually and deploy them using the Cloud Foundry Command Line Interface

    > ### Note:  
    > An MTA development descriptor `mta.yaml` is not explicitly required. In this case, a deployment descriptor is maintained instead.

    1.  Create the required files using an IDE of your choice.
    2.  To produce your custom artifacts, use a build technology of your choice.
    3.  Maintain your deployment descriptor document \(`mtad.yaml`\).
        1.  \(Optional\) If you want to have an MTA archive package, use the `mbt assemble`. For more information, see [Cloud MTA Build Tool \(MBT\)](https://sap.github.io/cloud-mta-build-tool/).

        2.  Use the `cf deploy` command to deploy the MTA package or directly from the build result directory.





<table>
<tr>
<th valign="top">

To learn more about

</th>
<th valign="top">

See

</th>
</tr>
<tr>
<td valign="top">

Multitarget Application deployment descriptor

</td>
<td valign="top">

[Defining Multitarget Application Deployment Descriptors for Cloud Foundry](defining-multitarget-application-deployment-descriptors-for-cloud-foundry-f48880b.md)

</td>
</tr>
<tr>
<td valign="top">

Multitarget Application archive

</td>
<td valign="top">

[Defining Multitarget Application Archives](defining-multitarget-application-archives-33a0e0e.md)

</td>
</tr>
<tr>
<td valign="top">

Multitarget Application extension descriptor

</td>
<td valign="top">

[Defining MTA Extension Descriptors](defining-mta-extension-descriptors-50df803.md)

</td>
</tr>
<tr>
<td valign="top">

Multitarget Application structure

</td>
<td valign="top">

[Multitarget Application Structure](multitarget-application-structure-f443b9f.md)

</td>
</tr>
<tr>
<td valign="top">

How to deploy the Multitarget Application

</td>
<td valign="top">

[Multitarget Application Plugin for Cloud Foundry Command Line Interface](../50-administration-and-ops/multitarget-application-plugin-for-cloud-foundry-command-line-interface-e93b231.md)

</td>
</tr>
</table>



<a name="loiod04fc0e2ad894545aebfd7126384307c__section_ub3_wjn_5jb"/>

## Terms and Concepts

**Terms and Concepts**


<table>
<tr>
<th valign="top">

Term

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Multitarget application \(MTA\)

</td>
<td valign="top">

An application comprised of multiple software modules, which are created with different technologies and deployed to different runtimes.

</td>
</tr>
<tr>
<td valign="top">

Development descriptor

</td>
<td valign="top">

A `YAML` file named `mta.yaml` that contains a list of all entities, such as modules, resources, and properties that belong to an application or are used by it at runtime, and the dependencies between them. It is automatically generated when an MTA project is created or modified, or when a module is added or removed. The developer needs to edit the descriptor manually to define resources, properties, and dependencies, as well as fill in missing information.

</td>
</tr>
<tr>
<td valign="top">

Deployment descriptor

</td>
<td valign="top">

A `YAML` file named `mtad.yaml` that contains a list of all entities which is created from either SAP Web IDE Full-Stack, SAP Business Application Studio, Cloud MTA Build Tool or manually. This file is similar to Development Descriptor but is used from the SAP Cloud Deployment service.

</td>
</tr>
<tr>
<td valign="top">

Module

</td>
<td valign="top">

A self-contained application of a certain type, which is developed, packaged and deployed.

</td>
</tr>
<tr>
<td valign="top">

Module type

</td>
<td valign="top">

A type that defines the structure and the development technology of a module. You can see a list of the module types at [Modules](modules-177d34d.md).

</td>
</tr>
<tr>
<td valign="top">

Resource

</td>
<td valign="top">

Any resource, such as an external service that is required by a module at runtime but not provided by the module itself.

</td>
</tr>
<tr>
<td valign="top">

Property

</td>
<td valign="top">

A property \(key-value pair\) of an application, module, or resource, that is used during deployment or at runtime.

</td>
</tr>
<tr>
<td valign="top">

Parameter

</td>
<td valign="top">

A reserved variable belonging to a module or resource, whose value is used during deployment or at runtime.

</td>
</tr>
<tr>
<td valign="top">

Dependency

</td>
<td valign="top">

A relationship between a module and another module, resource, or property, such as provides and requires.

-   `provides`: indicates the properties or parameters that are provided by a module or resource to other modules.

-   `requires`: indicates other modules or resources that are required by a module in order to run.




</td>
</tr>
<tr>
<td valign="top">

MTA archive \(MTAR\)

</td>
<td valign="top">

Archive containing a deployment descriptor, the module and resource binaries, and configuration files. The archive follows the JAR file specification.

</td>
</tr>
</table>



<a name="loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb"/>

## Prerequisites and Restrictions

You have to consider the following limits for the MTA artifacts, which can be handled by the SAP Cloud Deployment service:

-   Maximum size of the MTA archive: 4 GB
-   Maximum size of MTA module content: 1 GB
-   Maximum size of MTA resource content: 1 MB
-   Maximum size of MTA descriptors \(`mtad.yaml` and `MANIFEST.MF`\): 1 MB
-   Limitations for transport scenarios via SAP Cloud Transport Management, where one transport import with multiple transport requests results into a single deployment process in SAP Cloud Deployment service with multiple MTAs:
    -   The total size of all MTA archives in a single import request cannot exceed 20GB.
    -   The maximum number of MTA archives used in a single import request cannot exceed 100.

-   Limitations for transport scenarios via the Enhanced Change and Transport System \(CTS+\), where one transport import with multiple transport requests results into a single deployment process in SAP Cloud Deployment service with multiple MTAs:
    -   The total size of all MTA archives in multiple transport requests per one import cannot exceed 4GB.
    -   The maximum number of MTA archives used in a single import request cannot exceed 500.




### Unsupported Cloud Foundry Features

In addition to the features that are not supported by the Cloud Foundry environment on SAP BTP \(See [Supported and Unsupported Cloud Foundry Features](https://help.sap.com/docs/btp/sap-business-technology-platform/cloud-foundry-environment?version=Cloud#supported-and-unsupported-cloud-foundry-features)\), MTA deployment in Cloud Foundry currently does not support these features as well:

-   Sidecars. See [https://docs.cloudfoundry.org/devguide/sidecars.html](https://docs.cloudfoundry.org/devguide/sidecars.html).

-   Route services. See [https://docs.cloudfoundry.org/services/route-services.html](https://docs.cloudfoundry.org/services/route-services.html).

-   Health check interval. See [https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html](https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html).

-   Metadata. See [https://docs.cloudfoundry.org/adminguide/metadata.html](https://docs.cloudfoundry.org/adminguide/metadata.html).

-   Per-route options. See [https://docs.cloudfoundry.org/devguide/custom-per-route-options.html](https://docs.cloudfoundry.org/devguide/custom-per-route-options.html).

> ### Note:  
> These features might be implemented in the future. For the latest information, follow the release notes regarding Multitarget Applications for Cloud Foundry in [What’s New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Multitarget+Applications+for+Cloud+Foundry&locale=en-US&version=Cloud).

**Related Information**  


[JAR File Specification](http://docs.oracle.com/javase/7/docs/technotes/guides/jar/jar.html)

[Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/)

[Release Notes for Multitarget Applications for Cloud Foundry](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Multitarget%20Applications%20for%20Cloud%20Foundry&Valid_as_Of=2022-01-01%3A2050-12-31&locale=en-US)

