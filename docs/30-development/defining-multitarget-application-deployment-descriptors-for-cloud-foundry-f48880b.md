<!-- loiof48880b0295d4e9d859658244da84201 -->

# Defining Multitarget Application Deployment Descriptors for Cloud Foundry

The Multitarget Application \(MTA\) deployment descriptor is a YAML file that defines the relations between you as a provider of deployable artifacts and the SAP Cloud Deployment service in SAP BTP as a deployer tool.

Using the YAML data serialization language you describe the MTA in an MTA deployment descriptor \(`mtad.yaml`\) file following the [Multitarget Application Structure](multitarget-application-structure-f443b9f.md).

> ### Note:  
> As there are technical similarities between SAP HANA XS Advanced and Cloud Foundry, you can adapt application parameter for operation in either platform. Note that each environment supports its own set of module types, resource types, and configuration parameters. For more information, see the official specification documents [The Multitarget Application Model v.2](https://help.sap.com/doc/multitarget-application-modelv2/Cloud/en-US/The%20Multitarget%20Application%20Model.pdf) and [The Multitarget Application Model v.3](https://help.sap.com/doc/multitarget-application-modelv3/Cloud/en-US/The%20Multitarget%20Application%20M%D0%BEdel.pdf).



<a name="loiof48880b0295d4e9d859658244da84201__section_wjc_5tn_5jb"/>

## Schema Store

Writing `YAML` descriptors in plain text is often hard, so we have contributed a schema to the public Schema Store. This would provide you with an almost out-of-the-box support when writing MTA deployment descriptors in some of the more popular IDEs. The schema would provide you with auto-completion as well as suggestions and syntax checking.

For more information, see [Editor Schema Support](https://github.com/cloudfoundry-incubator/multiapps-controller/wiki/Deployment-Descriptor#editor-schema-support).

