<!-- loio0a69484539d64567ba17269f6e5ba88d -->

# Add Authentication and Functional Authorization Checks to Your Application

Learn how to create a security application descriptor file and use it to create a service instance of the Authorization and Trust Management service.



## Context

You want to protect your application resources \(functionality and data\) so that only authenticated and authorized business users are able to access these resources.

 ![](images/Authorization_and_Trust_Management_Concepts_CF_71e83d3.png) 

You declare your application security descriptor with JSON syntax and store it in a flat file on the filesystem. The standard name for this file is `xs-security.json`.



## Procedure

1.  Create your application security descriptor \(`xs-security.json`\) and set the `xsappname` element.

    The element xsappname defines a prefix for the runtime name of the application. For each tenant \(subaccount\), which has subscribed to the application, the XSUAA service supplies a unique tenant index for the application subscription and internally concatenates the tenant index with `xsappname` at runtime \(see also next step\).

    > ### Sample Code:  
    > ```
    > {
    >   "xsappname" : "hello-world",
    >   ...
    > }
    > ```

2.  Set the `scopes` element.

    Scopes represent the API endpoints - or functions - for which access should be restricted. They’re required if you want to define the functions a user is authorized to process. A scope has an arbitrary name and must be prefixed with the runtime application name to distinguish the user scopes between tenants \(subaccounts\) which have subscribed to the application and equally named scopes between different applications. The `$XSAPPNAME` dummy value is a wildcard for the application runtime name and is used to prefix the arbitrary scope names. The XSUAA service substitutes the `$XSAPPNAME` dummy value with the application runtime name for each of the subscribed tenants \(see also step 1\).

    > ### Sample Code:  
    > ```
    > {
    >   ... 
    >   "scopes"    : [
    >     { 
    >       "name"        : "$XSAPPNAME.Display", 
    >       "description" : "display" }, 
    >     { 
    >       "name"        : "$XSAPPNAME.Edit", 
    >       "description" : "edit" }, 
    >     { 
    >       "name"        : "$XSAPPNAME.Delete", 
    >       "description" : "delete" } 
    >   ],
    >   ... 
    > }
    > ```

3.  Set the `attributes` element.

    Attributes represent the data entities for which access should be restricted. They’re required if you want to define which data a user is authorized to process.

    Attributes provide instance-based, fine-granular authorization checks. See [Setting Up Instance-Based Authorizations](Setting_Up_Instance-Based_Authorizations_519965c.md).

    > ### Sample Code:  
    > ```
    > {
    >   ...
    >   "attributes" : [
    >     { 
    >       "name"        : "Country", 
    >       "description" : "Country", 
    >       "valueType"   : "string" }, 
    >     {
    >       "name"        : "CostCenter", 
    >       "description" : "CostCenter", 
    >       "valueType"   : "int" } 
    >   ], 
    >   ...
    > }
    > ```

4.  Set the `role-templates` element.

    Role templates combine scopes with attributes and serve as templates from which roles are created later by the administrator.

    > ### Sample Code:  
    > ```
    > {
    >   ...
    >   "role-templates" : [
    >     { 
    >       "name"                 : "Viewer", 
    >       "description"          : "View all books", 
    >       "scope-references"     : [ "$XSAPPNAME.Display" ], 
    >       "attribute-references" : [ "Country" ] }, 
    >     {
    >       "name"                 : "Editor", 
    >       "description"          : "Edit, delete books", 
    >       "scope-references"     : [ "$XSAPPNAME.Edit", "$XSAPPNAME.Delete" ], 
    >       "attribute-references" : [ "Country", "CostCenter"] } 
    >   ]
    > }
    > ```

5.  Deploy the application security descriptor \(`xs-security.json`\).

    Example:

    > ### Sample Code:  
    > ```
    > cf create-service xsuaa application my_xsuaa_service_instance -c xs-security.json
    > ```

6.  Check the scopes in the application.

    > ### Sample Code:  
    > ```
    > app.get('/books', checkReadScope, getBooks);
    > 
    > // Scope check
    > function checkReadScope(req, res, next) {
    >     if (req.authInfo.checkLocalScope('read')) {
    >         return next();
    >     } else {
    >         console.log('Missing the expected scope');
    >         res.status(403).end('Forbidden');
    >     }
    > }
    > ```

    The `checkReadScope` function ensures that only a user with the correct authorizations can look at the books.

    See [Tutorials for the SAP Authorization and Trust Management Service](Tutorials_for_the_SAP_Authorization_and_Trust_Management_Service_902ae80.md) for ways to check scopes in Java and other frameworks, like Spring.

7.  In the manifest file, add the binding for the service instance to your application.

    > ### Sample Code:  
    > ```
    >   ...
    >   services:
    >     - my_xsuaa_service_instance
    > ```

8.  Deploy the application.

    > ### Sample Code:  
    > ```
    > cf push
    > ```




<a name="loio0a69484539d64567ba17269f6e5ba88d__result_ukr_s3h_g4b"/>

## Results

You’ve declared and deployed your application security descriptor \(`xs-security.json`\) with scopes \(functional authorizations\), attributes \(data authorizations\), and role templates \(to combine scopes with attributes\). The `xsappname` element is mandatory. The `scopes`, `attributes`, and `role-templates` elements are optional. You've also bound your service instance to your application, and then deployed it.

> ### Sample Code:  
> ```
> {
>   "xsappname" : "hello-world", 
>   "scopes"    : [
>     { 
>       "name"        : "$XSAPPNAME.Display", 
>       "description" : "display" }, 
>     { 
>       "name"        : "$XSAPPNAME.Edit", 
>       "description" : "edit" }, 
>     { 
>       "name"        : "$XSAPPNAME.Delete", 
>       "description" : "delete" } 
>   ], 
>   "attributes" : [
>     { 
>       "name"        : "Country", 
>       "description" : "Country", 
>       "valueType"   : "string" }, 
>     {
>       "name"        : "CostCenter", 
>       "description" : "CostCenter", 
>       "valueType"   : "int" } 
>   ], 
>   "role-templates" : [
>     { 
>       "name"                 : "Viewer", 
>       "description"          : "View all books", 
>       "scope-references"     : [ "$XSAPPNAME.Display" ], 
>       "attribute-references" : [ "Country" ] }, 
>     {
>       "name"                 : "Editor", 
>       "description"          : "Edit, delete books", 
>       "scope-references"     : [ "$XSAPPNAME.Edit", "$XSAPPNAME.Delete" ], 
>       "attribute-references" : [ "Country", "CostCenter"] } 
>   ] 
> }
> ```



<a name="loio0a69484539d64567ba17269f6e5ba88d__postreq_dqj_mmq_l4b"/>

## Next Steps

To implement web access using a browser or a browser-based user interface, you can use an application router to enable you to create a secure route to your application, or an open source UI framework, such as Spring \(Boot\). For more information, see the related links.

**Related Information**  


[Application Router](Application_Router_01c5f9b.md "The application router is the single point-of-entry for an application running in the Cloud Foundry environment on SAP BTP. The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information.")

[Open Source UI Framework](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/samples/spring-security-xsuaa-usage)



