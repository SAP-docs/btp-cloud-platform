<!-- loioca0cc10a2d1249ebbde41f778d1932be -->

# MTA-Based Approach \(Recommended\)

The previous steps can also be done in a descriptive way using a so called multitarget application \(MTA\).

A multitarget application \(MTA\) is logically a single application comprised of multiple parts created with different technologies, which share the same lifecycle.

The developers of the MTA describe the desired result using the MTA model which contains MTA modules, MTA resources and interdependencies between them. Afterwards, the MTA deployment service validates, orchestrates, and automates the deployment of the MTA, which results in Cloud Foundry \(CF\) applications, services and SAP-specific contents. For more information about the Multitarget Application model, see the official [The Multitarget Application Model](https://www.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html) specification. For more details on how to use it in the CF Environment, which is the case here, see [Multitarget Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d04fc0e2ad894545aebfd7126384307c.html).

The MTA model is defined in the descriptor file “**mta.yaml**”. In the following chapters, we'll explain how to transfer the manual steps from the previous chapters into a mta.yaml. The previous chapters were:

-   [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md)

-   [Create an XSUAA Instance](Create_an_XSUAA_Instance_2ce1a96.md)

-   [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md)

-   [Register the Multitenant Application to the SaaS Provisioning Service](Register_the_Multitenant_Application_to_the_SaaS_Provisioning_Service_2cd8913.md)

-   [Bind the approuter Application to the xsuaa and the ABAP Solution Service Instance](Bind_the_approuter_Application_to_the_xsuaa_and_the_ABAP_Solution_Service_Instance_04b9258.md)


An MTA descriptor starts with the following lines defining the schema-version, the ID of the MTA and the version of the MTA:

```
_schema-version: "3.1"
ID: abap-saas-reference-solution
version: 1.0.0

```

You can pick your own ID and version; the schema-version should be kept as is.

-   **[Mapping to MTA Structure](Mapping_to_MTA_Structure_b728ebf.md)**  

-   **[Definition of Parameters](Definition_of_Parameters_06c0c9b.md)**  

-   **[Definition of MTA Modules](Definition_of_MTA_Modules_af521ff.md)**  

-   **[Definition of the MTA Resources](Definition_of_the_MTA_Resources_1764436.md)**  

-   **[Full MTA Descriptor](Full_MTA_Descriptor_ea445c6.md "")**  

-   **[Using MTA Extension Descriptors](Using_MTA_Extension_Descriptors_383f3a3.md)**  

-   **[Build and Deploy](Build_and_Deploy_faf5106.md)**  


**Related Information**  


[Mapping to MTA Structure](Mapping_to_MTA_Structure_b728ebf.md)

