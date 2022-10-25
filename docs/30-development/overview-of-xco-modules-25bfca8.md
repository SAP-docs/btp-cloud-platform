<!-- loio25bfca890eec4b0d8cfc8be995ae7c64 -->

# Overview of XCO Modules

The Cloud Platform \(CP\) edition of the XCO library is comprised of the following modules:

-   ABAP \(XCO\_CP\_ABAP\)

    Provides access to conceptual abstractions for classes and interfaces as well as to representations of ABAP built-in and generic types.

-   Application log object \(XCO\_CP\_APPLICATION\_LOG\_OBJECT\)

    Provides access to text attributes specific to application log objects.

-   ABAP Dictionary \(XCO\_CP\_ABAP\_DICTIONARY\)

    Provides access to conceptual abstractions for ABAP Dictionary elements \(Database tables, data elements, structures, table types and domains\) as well as to representations of ABAP Dictionary built-in types and their corresponding reference types.

-   ABAP Objects \(XCO\_CP\_ABAP\_OBJECTS\)

    Provides access to enumerations specific to ABAP Objects, e.g. the visibility of class or interface components, as well as to supported origins for the XCO Read APIs for classes and interfaces.

-   ABAP Repository \(XCO\_CP\_ABAP\_REPOSITORY\)

    Provides APIs and abstractions for retrieving and filtering development objects of the ABAP Repository in a strongly typed manner.

-   ABAP SQL \(XCO\_CP\_ABAP\_SQL\)

    Provides ways to build ABAP SQL constraints to be used in conjunction with the filtering offerings of the XCO ABAP Repository module.

-   AMDP \(XCO\_CP\_AMDP\)

    Provides access to enumerations in the context of ABAP-managed database procedures.

-   ARS \(XCO\_CP\_ARS\)

    Provides standard abstractions in the context of the API Release \(ARS\) framework \(e.g. for compatibility contracts\) to be used when programmatically setting or getting API states via the XCO ABAP Repository APIs.

-   Business Application Log \(XCO\_CP\_BAL\)

    Provides APIs for creating, deleting and searching logs as well as standard abstractions for integrating logging functionality into custom application logic.

-   Behavior definition \(XCO\_CP\_BEHAVIOR\_DEFINITION\)

    Provides access to enumerations specific to behavior definitions.

-   Behavior implementation \(XCO\_CP\_BEHAVIOR\_IMPLEMENTATION\)

    Provides access to enumerations specific to behavior implementations.

-   Binary \(XCO\_CP\_BINARY\)

    Provides access to binary text encodings, e.g. Base64.

-   Business configuration object \(XCO\_CP\_BUSINESS\_CNFGRTN\_OBJECT\)

    Provides access to text attributes specific to business configuration objects.

-   Call stack \(XCO\_CP\_CALL\_STACK\)

    Provides access to abstractions for programmatically working with all stacks \(e.g. supported formats\)

-   Core Data Services \(XCO\_CP\_CDS\)

    Provides access to enumerations specific to the field of Core Data Services \(CDS\) as well as conceptual abstractions for behavior definitions, data definitions, metadata extensions and CDS entities.

-   CDS Annotation \(XCO\_CP\_CDS\_ANNOTATION\)

    Provides ways to build CDS annotation values to be used when generating DDLS, DDLX or SRVD objects via the XCO Generation APIs.

-   Character \(XCO\_CP\_CHARACTER\)

    Provides access to abstractions useful when working with character-like data, e.g. code pages which can be used to translate between STRINGs and XSTRINGs

-   Correction and Transport System \(XCO\_CP\_CTS\)

    Provides abstractions for working with the Correction and Transport System \(CTS\), e.g. for creating and releasing Workbench transport requests.

-   Database table \(XCO\_CP\_DATABASE\_TABLE\)

    Provides access to database table specific enumerations, e.g. the size category of a database table, as well as to supported origins for the XCO Read APIs for database tables.

-   Data definition \(XCO\_CP\_DATA\_DEFINITION\)

    Provides access to enumerations and text attributes specific to CDS data definitions.

-   Data element \(XCO\_CP\_DATA\_ELEMENT\)

    Provides access to text attributes specific to data elements as well as to supported origins for the XCO Read APIs for data elements.

-   Data control language \(XCO\_CP\_DCL\)

    Provides ways to build DCL \(Data control language\) expressions to be used when generating DCLS objects via the XCO Generation APIs

-   Data definition language \(XCO\_CP\_DDL\)

    Provides ways to build DDL \(Data definition language\) expressions to be used when generating DDLS objects via the XCO Generation APIs.

-   Domain \(XCO\_CP\_DOMAIN\)

    Provides access to text attributes specific to domains as well as to supported origins for the XCO Read APIs for domains.

-   Function group \(XCO\_CP\_FUNCTION\_GROUP\)

    Provides access to supported origins for the XCO Read APIs for function groups.

-   Function module \(XCO\_CP\_FUNCTION\_MODULE\)

    Provides access to function module-specific enumerations as well as to supported origins for the XCO Read APIs for function modules.

-   Generation \(XCO\_CP\_GENERATION\)

    Provides access to the XCO Generation APIs, i.e. allows to obtain a generation environment which can be used to create POST, PUT, PATCH and DELETE operations \(as supported by the respective object type\).

-   Hash \(XCO\_CP\_HASH\)

    Provides access to supported hash algorithms which can be used to calculate the hash value of strings with the XCO Standard Library.

-   Internationalization \(XCO\_CP\_I18N\)

    Provides access to the XCO I18N APIs, i.e. allows to obtain domain, data element, data definition and message class targets which can be used to programmatically maintain language-dependent texts.

-   Identify and Access Management \(XCO\_CP\_IAM\)

    Provides access to standard abstractions \(e.g. for IAM business catalogs\) within the area of Identify and Access Management.

-   IAM Business Catalog

    Provides access to text attributes specific to IAM business catalogs.

-   JSON \(XCO\_CP\_JSON\)

    Provides access to facilities used when working with JSON data in the context of the XCO standard library, such as the JSON builder or standard JSON transformations.

-   Language \(XCO\_CP\_LANGUAGE\)

    Provides access to abstractions when working with languages, e.g. different formats.

-   Message \(XCO\_CP\_MESSAGE\)

    Provides access to enumerations specific to messages, such as the message type.

-   Message class \(XCO\_CP\_MESSAGE\_CLASS\)

    Provides access to text attributes specific to message classes.

-   Metadata extension \(XCO\_CP\_METADATA\_EXTENSION\)

    Provides access to enumerations specific to metadata extensions.

-   Name \(XCO\_CP\_NAME\)

    Provides access to IF\_XCO\_NAME\_CHOICEs to be used in conjunction with POST operations in the context of the XCO Generation APIs.

-   Package \(XCO\_CP\_PACKAGE\)

    Provides access to enumerations specific to packages.

-   RESTful Application Programming \(XCO\_CP\_RAP\)

    Provides access to abstractions to integrate RAP specific types \(e.g. RAP behavior messages\) with standard abstractions \(e.g. for business application logs\) of the XCO Library.

-   Regular expression \(XCO\_CP\_REGULAR\_EXPRESSION\)

    Provides access to abstractions used when working with regular expressions in the context of the XCO standard library, such as different regular expression engines.

-   Service binding \(XCO\_CP\_SERVICE\_BINDING\)

    Provides access to enumerations specific to service bindings.

-   Service definition \(XCO\_CP\_SERVICE\_DEFINITION\)

    Provides access to supported versions and origins as they can be used in the context of the XCO Read APIs for service definitions.

-   Software component \(XCO\_CP\_SOFTWARE\_COMPONENT\)

    Provides access to enumerations specific to software components.

-   String \(XCO\_CP\_STRING\)

    Provides access to abstractions used when working with strings in the context of the XCO standard library, such as the string builder or standard string compositions and decompositions.

-   System \(XCO\_CP\_SYSTEM\)

    Provides access to abstractions for system-wide entities such as software components or application components..

-   Table \(XCO\_CP\_TABLE\)

    Provides access to enumerations specific to tables \(i.e. structures and database tables\).

-   Table type \(XCO\_CP\_TABLE\_TYPE\)

    Provides access to enumerations specific to table types.

-   Tenant \(XCO\_CP\_TENANT\)

    Provides access to enumerations specific to tenants.

-   Time \(XCO\_CP\_TIME\)

    Provides access to the XCO time library.

-   Transport \(XCO\_CP\_TRANSPORT\)

    Provides access to enumerations and abstractions specific to transports.

-   UUID \(XCO\_CP\_UUID\)

    Provides access to abstractions used when working with UUIDs in the context of the XCO standard library, such as different UUID formats.

-   XSLX \(XCO\_CP\_XSLX, XCO\_CP\_XLSX\_SELECTION, XCO\_CP\_XLSX\_READ\_ACCESS, XCO\_CP\_XLSX\_WRITE\_ACCESS

    \)

    The XCO XLSX module supports the programmatic processing of XLSX documents. The various external APIs provide access to central abstractions required when reading data from XLSX documents.


