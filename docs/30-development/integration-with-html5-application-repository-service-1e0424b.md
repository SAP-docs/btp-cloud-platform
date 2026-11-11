<!-- loio1e0424b4e1d8441ebb245c4d1e6bb0e5 -->

# Integration with HTML5 Application Repository Service

The application router is integrated with the SAP HTML5 Application Repository service on SAP platform, to retrieve all the static content and routes \(`xs-app.json`\) of the HTML5 applications stored in the repository.

To integrate SAP HTML5 Application Repository service with an application router, create an instance of the `html5-apps-repo` service of the `app-runtime` plan, and bind it to the application router.

Model the `xs-app.json` routes that are used to retrieve static content from SAP HTML5 Application Repository service in the following way:

> ### Sample Code:  
> ```
> { 
>      "source": "^(/.*)",                                    
>      "target": "$1",                                        
>      "service": "html5-apps-repo-rt", 
>      "authenticationType": "xsuaa"                      
>  }
> ```

In case the application router needs to serve HTML5 applications not stored in SAP HTML5 Application Repository service, it is possible to model that in the `xs-app.json` file of the application router.

When the application router is bound to the SAP HTML5 Application Repository service, the following restrictions apply:

-   It is not possible to implement the "first" middleware slot to provide routes dynamically.

-   Only the `workingDir` option can be provided in the start of the application router.

-   A mixed scenario of modeling part of the static content in a local resources folder and also retrieving static content from theSAP HTML5 Application Repository service is not supported.


**Related Information**  


[](https://help.sap.com/viewer/43aae20270c44f3190e01df87a3807e6/Cloud/en-US/f8520f572a6445a7bfaff4a1bbcbe60a.html)

