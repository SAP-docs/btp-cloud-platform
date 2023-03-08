<!-- loio7f926eb79a7746fd996363118cd2c2aa -->

# Update a Service Instance

You can update a service instance from the `xsuaa` service using the service broker.



## Context

You are running a service instance that grants user access to an application. It uses the security descriptor file `xs-security.json`. If you change properties, for example, you want to reflect the compatible changes you made in the `xs-security.json` file in an existing service instance.

> ### Restriction:  
> If you define or update role templates and attributes in the `xs-security.json` file, observe the following configuration restrictions in [**Relationship Between ***default-values*** of ***attribute-references*** and ***valueRequired*****](https://help.sap.com/docs/btp/sap-business-technology-platform/application-security-descriptor-configuration-syntax#loio517895a9612241259d6941dbf9ad81cb__section_c1n_jfd_tkb).



## Procedure

1.  Edit the `xs-security.json` file and make your changes in the security descriptors.

2.  Update the service instance. During the update, you use the security descriptors you changed in the `xs-security.json` file.

    `cf update-service <service_instance_name> -c xs-security.json`

    > ### Example:  
    > `cf update-service authorizationtest-uaa -c xs-security.json`


