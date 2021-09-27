<!-- loio1e0424b4e1d8441ebb245c4d1e6bb0e5 -->

# Integration with HTML5 Application Repository

The application router is integrated with the HTML5 Application Repository service, to retrieve all the static content and routes \(`xs-app.json`\) of the HTML5 applications stored in the repository.

To integrate HTML5 Application Repository with an application router, create an instance of the `html5-apps-repo` service of the `app-runtime` plan, and bind it to the application router.

Model the `xs-app.json` routes that are used to retrieve static content from HTML5 Application Repository in the following way:

> ### Sample Code:  
> ```
> { 
>      "source": "^(/.*)",                                    
>      "target": "$1",                                        
>      "service": "html5-apps-repo-rt", 
>      "authenticationType": "xsuaa"                      
>  }
> ```

In case the application router needs to serve HTML5 applications not stored in HTML5 Application Repository, it is possible to model that in the `xs-app.json` file of the application router.

When the application router is bound to HTML5 Application Repository, the following restrictions apply:

-   This feature is only supported in Cloud Foundry.

-   It is not possible to implement the "first" middleware slot to provide routes dynamically.

-   Only the `workingDir` option can be provided in the start of the application router.

-   The destination property is not supported.

-   External session management via extensibility is not supported.

-   A mixed scenario of modeling part of the static content in a local resources folder and also retrieving static content from HTML5 Application Repository is not supported.


-   **[Processing a Request at Runtime](Processing_a_Request_at_Runtime_5038f1e.md "At runtime, the application router tries to fetch the xs-app.json file
		from the HTML5 application in the HTML5 Application Repository, and to use it for routing
		the request.")**  
At runtime, the application router tries to fetch the `xs-app.json` file from the HTML5 application in the HTML5 Application Repository, and to use it for routing the request.
-   **[Multitenancy of HTML5 Application Repository](Multitenancy_of_HTML5_Application_Repository_36f266b.md "The HTML5 Application Repository is a multitenant service. Non-public HTML5 Applications are visible only to the application providers
		(with provider subaccounts) and the consumers subscribed to the applications (with consumer subaccounts).")**  
The HTML5 Application Repository is a multitenant service. Non-public HTML5 Applications are visible only to the application providers \(with provider subaccounts\) and the consumers subscribed to the applications \(with consumer subaccounts\).

**Related Information**  


[](https://help.sap.com/viewer/43aae20270c44f3190e01df87a3807e6/Cloud/en-US/f8520f572a6445a7bfaff4a1bbcbe60a.html)

