<!-- loiof48880b0295d4e9d859658244da84201 -->

# Defining Multitarget Application Deployment Descriptors for Cloud Foundry

The Multitarget Application \(MTA\) deployment descriptor is a YAML file that defines the relations between you as a provider of deployable artifacts and the SAP Cloud Deployment service in SAP BTP as a deployer tool.

Using the YAML data serialization language you describe the MTA in an MTA deployment descriptor \(`mtad.yaml`\) file following the [Multitarget Application Structure](multitarget-application-structure-f443b9f.md).

> ### Note:  
> As there are technical similarities between SAP HANA XS Advanced and Cloud Foundry, you can adapt application parameter for operation in either platform. Note that each environment supports its own set of module types, resource types, and configuration parameters. For more information, see the official [Multitarget Application Model v.2](https://www.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html) and [Mulitarget Application Model v.3](https://www.sap.com/documents/2021/09/66d96898-fa7d-0010-bca6-c68f7e60039b.html) specification documents.



<a name="loiof48880b0295d4e9d859658244da84201__section_wjc_5tn_5jb"/>

## Schema Store

Writing `YAML` descriptors in plain text is often hard, so we have contributed a schema to the public Schema Store. This would provide you with an almost out of the box support when writing MTA deployment descriptors in some of the more popular IDEs. The schema would provide you with auto-completion as well as suggestions and syntax checking.

For more information, see [Editor Schema Support](https://github.com/cloudfoundry-incubator/multiapps-controller/wiki/Deployment-Descriptor#editor-schema-support).

