<!-- loioca0cc10a2d1249ebbde41f778d1932be -->

# MTA-Based Approach \(Recommended\)

The previous steps can also be done in a descriptive way using a so called multitarget application \(MTA\).

A multitarget application \(MTA\) is logically a single application comprised of multiple parts created with different technologies, which share the same lifecycle.

The developers of the MTA describe the desired result using the MTA model which contains MTA modules, MTA resources and interdependencies between them. Afterwards, the MTA deployment service validates, orchestrates, and automates the deployment of the MTA, which results in Cloud Foundry \(CF\) applications, services and SAP-specific contents. For more information about the Multitarget Application model, see the official [The Multitarget Application Model](https://www.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html) specification. For more details on how to use it in the CF Environment, which is the case here, see [Multitarget Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d04fc0e2ad894545aebfd7126384307c.html).

The MTA model is defined in the descriptor file “**mta.yaml**”. In the following chapters, we'll explain how to transfer the manual steps from the previous chapters into a mta.yaml. The previous chapters were:

-   [Define Your ABAP Solution](define-your-abap-solution-1697387.md)

-   [Create an XSUAA Instance](create-an-xsuaa-instance-2ce1a96.md)

-   [Configure the Approuter Application](configure-the-approuter-application-3725815.md)

-   [Register the Multitenant Application to the SaaS Provisioning Service](register-the-multitenant-application-to-the-saas-provisioning-service-2cd8913.md)

-   [Bind the approuter Application to the xsuaa and the ABAP Solution Service Instance](bind-the-approuter-application-to-the-xsuaa-and-the-abap-solution-service-instance-04b9258.md)


An MTA descriptor starts with the following lines defining the schema-version, the ID of the MTA and the version of the MTA:

```
_schema-version: "3.1"
ID: abap-saas-reference-solution
version: 1.0.0

```

You can pick your own ID and version; the schema-version should be kept as is.

**Related Information**  


[Mapping to MTA Structure](mapping-to-mta-structure-b728ebf.md)

