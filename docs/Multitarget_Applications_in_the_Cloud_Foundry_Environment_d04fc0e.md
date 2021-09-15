<!-- loiod04fc0e2ad894545aebfd7126384307c -->

# Multitarget Applications in the Cloud Foundry Environment

A Multitarget application \(MTA\) is logically a single application comprised of multiple parts created with different technologies, which share the same lifecycle.

The developers of the MTA describe the desired result using the MTA model, which contains MTA modules, MTA resources, and interdependencies between them. Afterward, the SAP Cloud Deployment service validates, orchestrates, and automates the deployment of the MTA, which results in Cloud Foundry applications, services and SAP specific contents. For more information about the Multitarget Application model, see the official [The Multitarget Application Model](https://www.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html) specification.

You can create and deploy a Multitarget Application in the Cloud Foundry environment as described below by following different approaches that can yield the same result:

-   Using the SAP Web IDE for Full-Stack Development as described in [Developing Multitarget Applications](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/a71bf8281254489ea8be6e323199b304.html) - both the development descriptor `mta.yaml` and the deployment descriptor `mtad.yaml` are created automatically. The `mta.yaml` is generated when you create the application project, and the `mtad.yaml` file is created when you build the project.

    > ### Note:  
    > You may still need to edit the development descriptor.

    Development descriptors are used to generate MTA deployment descriptors, which define the required deployment data. That is, the MTA development descriptor data specifies what you want to build, how to build it, while the deployment descriptor data specifies as what and how to deploy it.

    ![](images/DevelopWithWebIDE_4d4b82d.png)

    -   [https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/a71bf8281254489ea8be6e323199b304.html](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/a71bf8281254489ea8be6e323199b304.html)
    -   [https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/3b533e3723674fad90f94510b92f10af.html](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/3b533e3723674fad90f94510b92f10af.html)
    -   [https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/1b0a7a0938944c7fac978d4b8e23a63f.html](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/1b0a7a0938944c7fac978d4b8e23a63f.html)
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
        1.  \(Optional\) If you want to have an MTA archive package, use the ***mbt assemble***. For more information, see [Cloud MTA Build Tool \(MBT\)](https://sap.github.io/cloud-mta-build-tool/).

        2.  Use the `cf deploy` command to deploy the MTA package or directly from the build result directory.



<table>
<tr>
<th>

To learn more about



</th>
<th>

See



</th>
</tr>
<tr>
<td>

Multitarget Application deployment descriptor



</td>
<td>

[Defining Multitarget Application Deployment Descriptors for Cloud Foundry](Defining_Multitarget_Application_Deployment_Descriptors_for_Cloud_Foundry_f48880b.md)



</td>
</tr>
<tr>
<td>

Multitarget Application archive



</td>
<td>

[Defining Multitarget Application Archives](Defining_Multitarget_Application_Archives_33a0e0e.md)



</td>
</tr>
<tr>
<td>

Multitarget Application extension descriptor



</td>
<td>

[Defining MTA Extension Descriptors](Defining_MTA_Extension_Descriptors_50df803.md)



</td>
</tr>
<tr>
<td>

Multitarget Application module types and parameters



</td>
<td>





</td>
</tr>
<tr>
<td>

How to deploy the Multitarget Application



</td>
<td>

[Multitarget Application Plug-In for the Cloud Foundry Command Line Interface](Multitarget_Application_Plug-In_for_the_Cloud_Foundry_Command_Line_Interface_e93b231.md)



</td>
</tr>
</table>



<a name="loiod04fc0e2ad894545aebfd7126384307c__section_ub3_wjn_5jb"/>

## Terms and Concepts

<a name="loiod04fc0e2ad894545aebfd7126384307c__table_dcg_1kn_5jb"/>Terms and Concepts


<table>
<tr>
<th>

Term



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

Multitarget application \(MTA\)



</td>
<td>

An application comprised of multiple software modules, which are created with different technologies and deployed to different runtimes.



</td>
</tr>
<tr>
<td>

Development descriptor



</td>
<td>

A `YAML` file named `mta.yaml` that contains a list of all entities, such as modules, resources, and properties that belong to an application or are used by it at runtime, and the dependencies between them. It is automatically generated when an MTA project is created or modified, or when a module is added or removed. The developer needs to edit the descriptor manually to define resources, properties, and dependencies, as well as fill in missing information.



</td>
</tr>
<tr>
<td>

Deployment descriptor



</td>
<td>

A `YAML` file named `mtad.yaml` that contains a list of all entities which is created from the WEB IDE or from Multitarget Application Archive Builder tool or manually. This file is similar to Development Descriptor but is used from the MTA Deployer.



</td>
</tr>
<tr>
<td>

Module



</td>
<td>

A self-contained application of a certain type, which is developed, packaged, and deployed.



</td>
</tr>
<tr>
<td>

Module type



</td>
<td>

A type that defines the structure and the development technology of a module. You can see a list of the module types at [Modules](Modules_177d34d.md).



</td>
</tr>
<tr>
<td>

Resource



</td>
<td>

Any resource, such as an external service that is required by a module at runtime but not provided by the module itself.



</td>
</tr>
<tr>
<td>

Property



</td>
<td>

A property \(key-value pair\) of an application, module, or resource, that is used during deployment or at runtime.



</td>
</tr>
<tr>
<td>

Parameter



</td>
<td>

A reserved variable belonging to a module or resource, whose value is used during deployment or at runtime.



</td>
</tr>
<tr>
<td>

Dependency



</td>
<td>

A relationship between a module and another module, resource, or property, such as provides and requires.

-   `provides`: indicates the properties or parameters that are provided by a module or resource to other modules.

-   `requires`: indicates other modules or resources that are required by a module in order to run.




</td>
</tr>
<tr>
<td>

MTA archive \(MTAR\)



</td>
<td>

Archive containing a deployment descriptor, the module and resource binaries, and configuration files. The archive follows the JAR file specification.



</td>
</tr>
</table>



<a name="loiod04fc0e2ad894545aebfd7126384307c__section_ph2_r5h_1cb"/>

## Prerequisites and Restrictions

You have to consider the following limits for the MTA artifacts, which can be handled by the Cloud Foundry deploy service:

-   Maximum size of the MTA archive: 4 GB
-   Maximum size of MTA module content: 1 GB
-   Maximum size of MTA resource content: 1 GB
-   Maximum size of MTA descriptors \(`mtad.yaml` and `MANIFEST.MF`\): 1 MB

-   **[Benefits of the Multitarget Application Model \(MTA\) for the Cloud Foundry Environment](Benefits_of_the_Multitarget_Application_Model_(MTA)_for_the_Cloud_Foundry_Environment_8d2a68a.md "The benefits of the MTA approach can be related to the three “A”s that the MTA
		offers - Abstraction, Automation, and Assembly.")**  
The benefits of the MTA approach can be related to the three “A”s that the MTA offers - Abstraction, Automation, and Assembly.
-   **[Getting Started](Getting_Started_0ce9938.md "This section lists the example steps to deploy your first multitarget application. An
		mtar archive and an extension descriptor (optional) are used to execute the
		deployment.")**  
This section lists the example steps to deploy your first multitarget application. An mtar archive and an extension descriptor \(optional\) are used to execute the deployment.
-   **[Defining Multitarget Application Development Descriptors](Defining_Multitarget_Application_Development_Descriptors_c2d31e7.md "Multitarget Applications are defined in a development descriptor required for
		design-time purposes.")**  
Multitarget Applications are defined in a development descriptor required for design-time purposes.
-   **[Defining Multitarget Application Archives](Defining_Multitarget_Application_Archives_33a0e0e.md "You package the MTA deployment descriptor and module binaries in an MTA archive. You can
		manually do so as described below, or alternatively use the Cloud MTA Build
		tool.")**  
You package the MTA deployment descriptor and module binaries in an MTA archive. You can manually do so as described below, or alternatively use the Cloud MTA Build tool.
-   **[Defining Multitarget Application Deployment Descriptors for Cloud Foundry](Defining_Multitarget_Application_Deployment_Descriptors_for_Cloud_Foundry_f48880b.md)**  

-   **[Multitarget Application Structure](Multitarget_Application_Structure_f443b9f.md "The following chapter contains information about:")**  
The following chapter contains information about:
-   **[Defining MTA Extension Descriptors](Defining_MTA_Extension_Descriptors_50df803.md)**  

-   **[SAP Business Technology Platform Capabilities](SAP_Business_Technology_Platform_Capabilities_1d6f3ca.md "This section contains information about how to manage standard Cloud
                                Foundry entities
		with MTA modelling.")**  
This section contains information about how to manage standard Cloud Foundry entities with MTA modelling.
-   **[Features](Features_d50d040.md "The section describes multitarget application-specific features available in the Cloud
                                Foundry
		environment of the SAP Business Technology
                                Platform.")**  
The section describes multitarget application-specific features available in the Cloud Foundry environment of the SAP Business Technology Platform.
-   **[Transporting Multitarget Applications in Cloud Foundry using CTS+](Transporting_Multitarget_Applications_in_Cloud_Foundry_using_CTS+_c9a4069.md "You can enable transport of SAP BTP applications and
		application content that is available as Multitarget Applications (MTA) using the Enhanced
		Change and Transport System (CTS+).")**  
You can enable transport of SAP BTP applications and application content that is available as Multitarget Applications \(MTA\) using the Enhanced Change and Transport System \(CTS+\).
-   **[Frequently Asked Questions](Frequently_Asked_Questions_6062ecc.md "")**  

-   **[Troubleshooting](Troubleshooting_3530af7.md "This section contains information about the following problems that may occur during the
		Multitarget Application deployment:")**  
This section contains information about the following problems that may occur during the Multitarget Application deployment:

**Related Information**  


[JAR File Specification](http://docs.oracle.com/javase/7/docs/technotes/guides/jar/jar.html)

[Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/)

