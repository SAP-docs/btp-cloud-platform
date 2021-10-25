<!-- loioe300d63441ad45a1a7b883e58b14649c -->

# Consuming Content

Use the `app-runtime` service plan to consume HTML5 applications from the HTML5 Application Repository.



## Context

Application router can consume content from the HTML5 Application Repository by binding an HTML5 Application Repository service instance with `app-runtime` plan to the application router. In addition, the routing to the HTML5 Application Repository service is configured in the `xs-app.json` file.



## Procedure

1.  Create a service instance of `app-runtime` service plan.

    Example: `cf create-service html5-apps-repo app-runtime MyHtml5AppsRepoRuntimeInstance`

2.  Bind the HTML5 Application Repository runtime instance to the application router in the `manifest.yaml` file.

    > ### Sample Code:  
    > ```
    > applications:
    > - name: myCRMApp
    >   memory: 256M
    > 
    >   services:
    >     - MyHtml5AppsRepoRuntimeInstance  
    > 
    > ```

3.  Push the application with the following command: `cf push`

4.  To redirect requests to the HTML5 Application Repository runtime, configure the routing to the HTML5 Application Repository service in your `xs-app.json` file.

    > ### Sample Code:  
    > ```
    > {
    >  
    >      "source": "^(/.*)",
    >  
    >      "target": "$1",
    >  
    >      "service": "html5-apps-repo-rt",
    >  
    >      "authenticationType": "xsuaa"
    >  
    >  }
    > 
    > ```

5.  HTML5 application content can be consumed from the application router using an URL in the following format: `https://<host>.<domain>/<appName>-<appVersion>/<resourcePath>`

    > ### Note:  
    > `appName` - the `manifest.json app.id` **without the dots**
    > 
    > `appVersion` - the `manifest.json applicationVersion.version`. The appVersion is optional. If not provided, the latest version will be used.


