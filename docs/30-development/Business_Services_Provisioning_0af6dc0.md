<!-- loio0af6dc0a0d3c4accbfcee24a26166876 -->

# Business Services Provisioning



<a name="loio0af6dc0a0d3c4accbfcee24a26166876__section_pmh_ps4_n4b"/>

## Business Service

The ABAP development platform can act in the roles of a service provider and a service consumer. In the context of the ABAP RESTful Application Programming Model, a business service is a RESTful service which can be called by a consumer. It is defined by exposing its data model together with the associated behavior. It consists of a service definition and a service binding.



<a name="loio0af6dc0a0d3c4accbfcee24a26166876__section_ss4_ct4_n4b"/>

## Mandatory checks to be considered while defining and binding services via InA:

1.  An active version of the service definition must exist.

2.  An InA service binding can be created on only one service definition that has only one exposed artifact and the exposed artifact must be an analytical query.

3.  Only one InA service binding is allowed for one analytical query. This check is performed both during the creation of a new service binding and on the existing InA service.

4.  After an InA service has been activated, if the underlying service definition is modified \(i.e. the exposed artifact is changed\), a warning is thrown for the InA service and the service has to be activated again.




<a name="loio0af6dc0a0d3c4accbfcee24a26166876__section_ipy_rt4_n4b"/>

## Service Definition

A service definition represents the service model that is generically derived from the underlying CDS-based data model. You use a service definition to define which data is to be exposed as a business service using one or more business service bindings \(short form: service bindings\). A service definition itself is independent from the version or type of the protocol that is used for the business service.



<a name="loio0af6dc0a0d3c4accbfcee24a26166876__section_fvz_wx4_n4b"/>

## Service Binding

The business service binding \(short form: service binding\) is used to bind a service definition to a communication protocol. In our case, the protocol that enables web-based data access from ABAP environment systems is the Information Access \(InA\) protocol.



> ### Note:  
> For more information, see [Business Service Consumption](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/f2cbcacaf8b74540b0708fc143875bc3.html).

**Related Information**  


[Define a Service Definition and Binding via InA](Define_a_Service_Definition_and_Binding_via_InA_e8a5adb.md "Define and bind services via the SAP Information Access (InA) service.")

