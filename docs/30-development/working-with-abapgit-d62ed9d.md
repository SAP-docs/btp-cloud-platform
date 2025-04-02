<!-- loiod62ed9d54a764c53990f25f0ab6c27f9 -->

# Working with abapGit

abapGit is an open source developed Git client for the ABAP server to import and export ABAP objects between ABAP systems.

With abapGit, you can export your ABAP objects from any system to another, typically from on-premise to cloud or from one cloud system to another. See [Use abapGit to Transfer Your On-Premise ABAP Source Code to the Cloud](https://developers.sap.com/tutorials/abap-environment-abapgit.html) and [Push Your ABAP Source Code from SAP BTP ABAP Environment to a GitHub Repository Using abapGit](https://developers.sap.com/tutorials/abap-environment-abapgit-transfer.html).

> ### Note:  
> While the ABAP environment comes with a preinstalled cloud version of abapGit, you can only use abapGit in an on-premise system if you have installed the [official community version](https://github.com/abapGit/abapGit) of abapGit. However, the official community version is not supported by SAP.

With the official SAP distribution of abapGit, you can use ABAP Development Tools \(ADT\) in combination with the abapGit feature for ADT, which allows easier access to the import/export functionality provided by abapGit. For more information on how to install and work with ABAP Development Tools, see [Installing ABAP Development Tools](https://help.sap.com/doc/2e9cf4a457d84c7a81f33d8c3fdd9694/Cloud/en-US/inst_guide_abap_development_tools.pdf) and [abapGit Repositories ADT Plug-In](https://eclipse.abapgit.org/updatesite/).



<a name="loiod62ed9d54a764c53990f25f0ab6c27f9__section_n3y_mbv_cbc"/>

## Use Cases

*Side-by-Side-Development*

abapGit can assist you in side-by-side development by enabling the transfer of source code between on-premise systems and SAP BTP ABAP Environment.

*Account Transfer*

abapGit can support you in transferring your development code assets from one Steampunk system to another, particularly across different BTP global accounts.

*Partner Code Transfer*

As a partner, you can utilize abapGit to export your development code assets from your development landscape and import them into your customers' development system.

*Demo Samples and Open Source Offerings*

You can use abapGit to distribute code as open source, e.g., Code Pal for ABAP - Cloud Edition or demo samples, such as the ABAP Flight Reference Scenario for the ABAP RESTful Application Programming Model.



<a name="loiod62ed9d54a764c53990f25f0ab6c27f9__section_emb_dgj_5tb"/>

## Restrictions and Errors

There are certain restrictions to the export and import functionality when using abapGit in the ABAP environment. This is due to the cloud-optimized set of supported ABAP object types that change with each release as new ABAP object types are added continuously. See [Released ABAP Object Types](released-abap-object-types-b31aa03.md). Depending on your application, you may face the following issues when using abapGit in cloud systems:

-   Export errors when pushing unsupported objects
-   Import errors when pulling unsupported objects
-   Activation errors when activating imported objects



### Export Errors

If you try to export objects that are not supported, you receive a warning during the push operation, and the unreleased object is skipped.

The only work-around for this is to manually copy the missing ABAP objects to the target system. First, you have to create these objects using the same name in the target system. Afterwards, you either have to manually copy the code or reconfigure the objects in the target system.

Some objects are deliberately not exported because they are considered as compiled or generated so that they can be regenerated when activating their originating objects in the target system. For example, certain service definitions \(SRVD\) are generated from service consumption models \(SRVC\) so that they are not exported to git.



### Import Errors

When importing objects with abapGit for ADT, you may get error messages in the import log. Possible reasons can be:

-   You are importing object types \(for example from an on-premise system\) that are not supported in the ABAP environment and the programming model of the ABAP environment. You may have to change your application in the cloud environment to work without these objects.
-   You are importing objects with missing dependencies. These dependent objects can't be exported because they are not on the list of Released ABAP Object Types. You must copy/recreate these missing dependent objects and restart the import.
-   You are importing objects using ABAP namespaces. Make sure these namespaces have been imported into the target system before importing your application with abapGit.
-   You are importing a software component relations object. Make sure that a software component with the same name has been created in the target system already. Please note that this object can be imported into the top-level structure package of the corresponding software component only.


> ### Note:  
> Local changes to ABAP objects that have not been saved are overwritten by the import. Open transport requests for any of the imported ABAP objects must be released before they can be changed. Otherwise, they get locked.



### Activation Errors

All objects imported with abapGit are imported in an inactive state, except the ones that do not offer an inactive state, to ensure that their consistency can be properly checked during activation. Hence, you have to activate all imported objects after importing them so that ABAP activation can verify that only released APIs have been used.

During the activation process, some objects may depend on other objects, which need to be activated beforehand. However, not all object types consider the objects they depend on during mass activation. For example:

-   Data dictionary \(DDic\) and core data service \(CDS\) objects do not always resolve their dependencies in the first mass activation attempt so that you have to activate them in multiple cycles.
-   Service bindings need to be activated after service definitions.

If activation issues occur, repeatedly try to activate objects in the right sequence. If that does not work, try reimporting and reactivating objects multiple times until all objects of your application are active.



> ### Tip:  
> If you face any issues with the official abapGit distribution of SAP, create an incident using component `BC-CP-ABA`.
> 
> For issues related to the community open-source distribution of abapGit, create an issue at [https://github.com/abapGit/abapGit/issues](https://github.com/abapGit/abapGit/issues).

> ### Note:  
> It is possible to define the external systems, the ABAP system is allowed to communicate with, by maintaining a list of trusted certificate authorities. Please use the Maintain Certificate Trust List app to do so. This app can be used by administrators, users with the SAP\_BR\_ADMINISTRATOR role. For further information, please go to [Maintain Certificate Trust List](../50-administration-and-ops/maintain-certificate-trust-list-2b3c3f1.md)



<a name="loiod62ed9d54a764c53990f25f0ab6c27f9__section_dsc_pgd_dbc"/>

## Working with UI Artifacts

As described in [Restrictions and Errors](https://help.sap.com/docs/btp/sap-business-technology-platform/working-with-abapgit?version=Cloud#restrictions-and-errors), the originating objects of the UI/SAP Fiori artifacts \(SMIM, UIAD, WAPA\) have their own lifecycle in a separate Git repository. The deployment to the target ABAP system will be done via SAP Business Application Studio / Visual Studio Code using SAP Fiori Tools.

For the case that one of the above-described use cases applies and you must transfer your application, remember that the UI artifacts have their own Git repository. This is important because abapGit does not take the UI objects into account.

Nevertheless, you have two different Git repositories. The Git repository with ABAP artefacts and the Git repository with the UI artefacts.



### Important to Know

Understanding the unique usage of the UI Git repository compared to the abapGit repository is crucial. The main difference lies in the fact that the user interface \(UI\) maintains its own lifecycle. This means any modifications or updates to the UI must be made within the Business Application Studio or Visual Studio Code and then pushed to the dedicated UI repository.

The abapGit repository is usually only used once to \(additionally\) save and share your code. The lifecycle happens in your ABAP system.



### Procedure

Depending on your needs, you might have to duplicate the repositories, create branches, or fork branches. For example, to transfer an application from a partner development system to a customer development system, you can use the export and import functionality of your Git provider. Alternatively, you can utilize Git functionality like branching or forking to "duplicate" the repository.

For additional information on how to duplicate the Git repositories, it may be helpful to consult the documentation provided by your Git provider.

*Import Steps*

-   You have read access to both Git repositories \(abapGit and UI\)

-   Link and pull the abapGit repository into your ABAP system.

-   Click onto the button *Activate All* to activate all objects.

    > ### Note:  
    > The activation might fail due to missing dependencies, e.g., missing UI artifacts.

-   Clone your UI repositories to Business Application StudioAS/Visual Studio and deploy the UI to your ABAP system.

-   Pull the abapGit repository again because some abapGit objects rely on the UI objects.

-   Click onto the button *Activate All* to activate all objects.

    > ### Note:  
    > Please be aware that it might be necessary to repeat the last two steps.


**Related Information**  


[Released ABAP Object Types](released-abap-object-types-b31aa03.md "")

