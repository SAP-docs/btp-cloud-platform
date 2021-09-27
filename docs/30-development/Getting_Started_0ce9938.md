<!-- loio0ce993811c1c4dc4a063e7e5f4332775 -->

# Getting Started

This section lists the example steps to deploy your first multitarget application. An mtar archive and an extension descriptor \(optional\) are used to execute the deployment.

For more information about the extension descriptor, see [Defining MTA Extension Descriptors](Defining_MTA_Extension_Descriptors_50df803.md) 

1.  Copy the example below to an `mtad.yaml` file.

    > ### Example:  
    > ```
    > _schema-version: "3.1" 
    > ID: app
    > version: 1.0.0
    > 
    > modules: 
    >   - name: my-first-app
    >     type: staticfile
    >     path: content.zip
    >     requires:
    >       - name: my-first-app-service
    > 
    > resources:
    >   - name: my-first-app-service
    >     type: org.cloudfoundry.managed-service
    >     parameters:
    >       service: application-logs
    >       service-plan: lite
    > 
    > ```

2.  Create a `content.zip` archive which contains an `index.html` file.

3.  Execute the following:

    1.  `cf add-plugin-repo CF-Community https://plugins.cloudfoundry.org` 

    2.  `cf install-plugin multiapps`

    3.  `cf deploy ./`

4.  Check your application


> ### Example:  
> Output
> 
> > ### Output Code:  
> > ```
> > Deploying multi-target app archive app.mtar in org deploy-service / space <SPACE> as <USER>...
> > 
> > Uploading 1 files...
> >   <PATH_TO_MTAR>
> > OK
> > Deploying in org "<ORG>" and space "<SPACE>"
> > Detected MTA schema version: "3"
> > No deployed MTA detected - this is initial deployment
> > Detected new MTA version: "2.4.0"
> > Processing service "my-first-app-service"...
> > Creating service "my-first-app-service" from MTA resource "my-first-app-service"...
> > Creating application "my-first-app" from MTA module "my-first-app"...
> > Uploading application "my-first-app"...
> > Scaling application "my-first-app" to "1" instances...
> > Staging application "my-first-app"...
> > Application "my-first-app" staged
> > Starting application "my-first-app"...
> > Application "my-first-app" started and available at "deploy-service-<SPACE>-my-first-app.cfapps.sap.hana.ondemand.com"
> > Skipping deletion of services, because the command line option "--delete-services" is not specified.
> > Process finished.
> > Use "cf dmol -i 830247915" to download the logs of the process.
> > 
> > ```

In the output example above, the application `my-first-app` is deployed and started. A service called `my-first-app-service` is also created and is bound to the application. Credentials are provisioned for the service instance and delivered to the application runtime in the `VCAP_SERVICES` environment variable.

To check the application, execute `cf apps`. The result should be as follows :

> ### Output Code:  
> ```
> cf apps
> Getting apps in org <ORG> / space <SPACE> as <USER>...
> OK
> 
> name               requested state      instances   memory   disk   urls
> my-first-app       started              1/1         1G       1G     deploy-service-<SPACE>-my-first-app.cfapps.sap.hana.ondemand.com
> 
> ```

To check the service, execute `cf services`. The result should be as follows :

> ### Output Code:  
> ```
> 
> cf services
> Getting services in org <ORG> / space <SPACE> as <USER>...
> 
> name                   service            plan     bound apps     last operation
> my-first-app-service   application-logs   lite     my-first-app   create succeeded
> 
> ```

