<!-- loio9ed190c223b54f8cb7d72fae41b22c56 -->

# Redeploy Content

You can redeploy changed content to the existing app-host service instance.

After making changes to the static content files of HTML5 applications, you can redeploy the new content to the already existing app-host service instance of the HTML5 application repository. All content referenced by the app-host service instance ID is replaced by the new content. If you want to keep more than one version of your HTML5 application on the repository, you deploy all versions, the new versions and the old versions that you want to keep, to the same app-host service instance ID.



## Deploying More Than One Version to the Repository

-   Application **app1** with version 1.0.0 has been deployed to the repository. This app matches a back-end application with version 3.0.0

-   For the app, a new back-end version 4.0.0 is available. Therefore, the application with version 2.0.0 is developed that matches the new back-end version.

-   As customers may still have a backend with version 3.0.0, **app1** with version 1.0.0 cannot be dropped. On the repository, both versions shall be available so the customer can decide which one to use depending on their back-end version.


This example shows how to deploy two versions of an application with the HTML5 Application Deployer. You can use a similar structure when you deploy MTA applications with the Generic Application Content Deployer \(GACD\): /

> ### Sample Code:  
> ```
> 
> myAppsDeployer
>   + node_modules
>   - resources
>     - app1-old-backend
>       index.html
>       manifest.json (app.id: 1.0.0)
>       xs-app.json
>     - app1-new-backend
>       index.html      
>       manifest.json (app.id: 2.0.0)      
>       xs-app.json
>   package.json
>   manifest.yaml
> 
> ```

