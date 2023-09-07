<!-- loioae1d53e5fbe14383bfafe690f52711d7 -->

# Troubleshooting

A troubleshooting guide for HTML5 application repository.



<a name="loioae1d53e5fbe14383bfafe690f52711d7__section_v11_2sm_b3b"/>

## Uploading Applications



### 400: Application metadata already exists when uploading HTML5 applications


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

HTML5 Application Deployment fails with error "Application metadata for application xyz already exists."



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

There is already an app-host service instance that contains a manifest.json with app.id = xyz in this space it is not possible to have multiple app-hosts containing the same app.id.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Delete or do not deploy the old app-host instance or use another app.id in the resources folder for a new app-host.



</td>
</tr>
</table>



### 400: Failed to run the application router after subscription; route not found


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

After subscribing to the application router using the <subdomain\>-<myapprouter\>.<scp domain\> format, the calling the application router fails with error "route not found".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

In order to support subscriptions out of the box, a route with format \*.<custom-domain\> should be created and mapped to the application router. The \* host represents a wildcard that is replaced by the actual subscriber subdomain during runtime.

Without a custom domain, this type of route \(wildcard host\) cannot be created; only a fixed host can be used. Without a custom domain, the route format is <subdomain\>-<myapprouter\>.<scp domain\>. It means that you have to create a route with the expected subdomain for each new subscriber.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

In development setups, if you don't have a custom domain before subscription, then create a route with the expected subscriber subdomain.



</td>
</tr>
</table>



### 400: Uploading application content failed


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

When trying to upload content, it fails with error: "Upload failed".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

One or more of the input validations performed by HTML5 application repository failed. The possible validation failures are:

1.  Missing manifest.json file on the root level.

2.  manifest.json app.id has invalid characters \(hyphens, @, %, &, etc.\).

3.  manifest.json app.version is not using the following format: *xx.xx.xx*, where x must be an integer \(e.g.: -snapshot is not supported\).

4.  app.id of one or more of the applications already exists in another html5-apps-repo/app-host service instance in the same space.




</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Check if one of the causes is your issue. For example, check the size of your html5-app-deployer resources folder, check manifest.json. If you are not sure if another service instance already uses your app.id, try making a small change to your app.id and deploy it again.



</td>
</tr>
</table>



### 403: App-host is being modified by another process


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

HTML5 application repository deployment fails with error "app-host is being modified by another process."



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The HTML5 application repository deployer attempts to upload content while another deployer is also uploading content using the same app-host.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Try again after the first HTML5 application repository deployer has completed its upload.



</td>
</tr>
</table>



### 409: App-host deploy or redeploy remains in progress


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

HTML5 application repository deployment fails with error "Deploy in progress" or "Redeploy in progress" and response type 409 for a long time or any other issue.



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

If something happens during the upload, it might cause some inconsistencies.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Delete the content of one or more multiple app-hosts, and reset the state to initial without deleting the service instances. Use the following command line in the CF CLI HTML5 application repository plug-in:

```
cf html5-delete --content <app-host-id> [...]
```



</td>
</tr>
</table>



### Failed to upload content; exceeded maximum file length


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

When trying to upload content, it fails with error: "Error while parsing request; Error: maximum file length exceeded".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The zipped application file length exceeds the size limit of the app-host service instance.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Increase the app-host size limit using the update service. For example: `cf update-service my-app-host -c '{"sizeLimit":100}'`.



</td>
</tr>
</table>



### Timeout while uploading content


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

When trying to upload content using the `cf push` command, it fails with error: "Failed to make TCP connection to port 8080: connection refused. Timed out after 1m0s: health check never passed."



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The `cf push` plugin checks if the start process is finished. If the process times out, then it tries to start it again.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Set `health-check-type` to `none` in the manifest.yaml of the HTML5 Application Deployer.



</td>
</tr>
</table>



### Uploading application content failed; application size exceeds the maximum size limit of 100 MB


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

When trying to upload content, you receive the following error: "Uploading application content failed: application's size exceeds the maximum size limit of 100 MB".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The unzipped applications content exceeds the size limit \(deprecated\) of the app-host service instance.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Deploy an application that is less than 100 MB or remove some of your applications and move them to another app-host. .



</td>
</tr>
</table>



<a name="loioae1d53e5fbe14383bfafe690f52711d7__section_rh5_bym_b3b"/>

## Running Applications



### 400: Failed to retrieve xs-app.json; invalid app-host ID


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

Serving content from the HTML5 application repository fails with error "Invalid App Host ID. Please check with business service provider if the requested App Host ID is valid".



</td>
</tr>
<tr>
<td valign="top">

Caution



</td>
<td valign="top">

HTML5 application repository belongs to a business service and the app host ID is invalid or incompatible.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Ask the business service owner to define`"public" : true` in the app manifest.json or wait until the HTML5 application repository is restarted.



</td>
</tr>
</table>



### 403: Failed to retrieve xs-app.json; unauthorized


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

Serving content from the application router fails with error "Unauthorized. Please check with the business service UI provider if the requested UI is defined as public".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

HTML5 application repository belongs to a business service and it is not public.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Ask the business service owner to define `"public": true` in the app manifest.json.



</td>
</tr>
</table>



### 404: Application does not exist


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

The HTML5 application repository fails to serve content. The application log states: "Application xyz does not exist" is printed to the console.



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The application name provided in URL is not correct or the request URL doesn’t provide the application key:

Application names are stored in HTML5 application repository without using full stops as separators in the URL. If *manifest.json app.id* equals *country.list*, then the application name is *countrylist* and the same application name should be used in URL.

A request to the application router must provide the application key in the URL because the application router uses the application key to fetch the xs-app.json file of the HTML5 application from the HTML5 Application Repository. The application key can consist of the business service prefix, application name, and application version. \(Only the application name is mandatory.\).



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

First check the application name. For the request URL, use the application name without full stops as separators.

If the application name is correct, check if the request URL to the application router contains the application key. If it doesn’t contain the application key, check how you configured the backend application data retrieval in your HTML5 application:

-   If you use SAP Fiori tools such as BAS, in the `manifest.json` file of the application, check the `dataSources.uri` property. The value for `dataSources.uri` must not start with a slash\("`/`"\). For example, the value `northwind/V2/ Northwind.svc` this is correct, but <code><b>/</b>northwind/V2/ Northwind.svc/</code> is wrong because it would create an absolute path from which the browser cannot concatenate the application key for the request. If there is a slash, remove it.

-   • If you use a JQueryAjax call for the request, make sure that the URL that is provided to the JQueryAjax call is a relative path and does not start with a slash \("`/`"\).




</td>
</tr>
</table>



### 404: Calls to service endpoints specified in an application's xs-app.json fails


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

You have defined routes in a UI app's local xs-app.json but calls do not get routed and instead return a 404 error.



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The routes in the xs-app.json file are processed top to bottom. If a route maps the pattern, it is picked even if a route below it is a better match. The route for the HTML5 application repository typically is a "catch all" route, and if any routes are defined below it, then they are never reached.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Move the route leading to the html5-apps-repo-rt to be the last entry in the xs-app.json file.



</td>
</tr>
</table>



### 500: Failed to retrieve xs-app.json


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

Serving content fails with error "Error while retrieving xsApp configuration".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The HTML5 application repository is not available.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Wait until HTML5 application repository is restarted.



</td>
</tr>
</table>



### 500: Failed to use dynamic destination


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

Serving content from the application router failed with an internal server error. In the application router application log, an error: "Destination <destinationName\> is not defined as a dynamic destination in destination service, configure additional property HTML5.DynamicDestination true" appears.



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The destination name provided on the host or path level is not defined as a dynamic destination in destination service.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

In the additional properties section of the destination section of the SAP BTP cockpit, add the `HTML5.DynamicDestination` property and set the value to *true*.



</td>
</tr>
</table>



### 500: Missing xs-app.json in HTML5 application repository when reading an HTML5 application file from the application router


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

 



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

Serving content from the application router fails with error "Application does not have xs-app.json".



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

xs-app.json file is missing in HTML5 Application.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Redeploy the HTML5 Application with xs-app.json file or ask the business service owner to add the xs-app.json.



</td>
</tr>
</table>



### Bearer token invalid


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

The `app-router` token exchange with a business service token fails. XSUAA returns the following error: "Bearer token invalid, requesting client does not have grant\_type=user\_token or no scopes were granted."



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The uaa.user scope in XSUAA instance configuration is missing or the target business service is not subscribed.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

1.  If missing, add the following to the `n xs-security.json` file:

    "scopes": \[ \{ "name": "uaa.user", "description": "UAA" \}\],

    "role-templates": \[ \{"name": "Token\_Exchange","description": "UAA","scope-references": \["uaa.user"\] \} \]

2.  Redeploy or update the XSUAA service instance.

3.  Make sure that the users have the new role\_template, *Token\_Exchange* added to their role\_collections in the SAP BTP cockpit *Global Account* \> *Subaccount* \> *Security* \> *Role Collections* and verify that the created role's *Application Identifier* is the same as the `xsappname` from the xs-security.json.

4.  If the roles of the target business service does not appear on the subscriber tenant UI, it means that the target business service subscription failed or it was bound to the application router after the subscription took place. In this case, try to unsubscribe and subscribe again. Make sure that the target business service roles appear on subscriber tenant UI.




</td>
</tr>
</table>



### Caching issue in browser


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

Your application does not work properly after logging out and when you try to log back in, for example, click anywhere on the application screen, nothing happens.



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

The main page of your application, that appears after you log in, is cached by the browser. Clicking links does not reach the backend \(application router\) and the log in process does not work.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

Check that the main page is not configured to be cached by the browser in your xs-app.json file. The best practice is to model the cacheControl as follows:

```
{
  "routes": [
    {
      "source": "^/ui/index.html",
      "target": "index.html",
      "service": "html5-apps-repo-rt",
      "authenticationType": "xsuaa"
      "cacheControl": "no-cache, no-store, must-revalidate"
    }
  ]
}
```



</td>
</tr>
</table>



### Running application router after subscribing to it fails


<table>
<tr>
<th valign="top">

Term



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Issue



</td>
<td valign="top">

After subscribing to the application router using `<subdomain>-<myapprouter>.<scp domain>` format, it fails and returns the following error, "route not found."



</td>
</tr>
<tr>
<td valign="top">

Cause



</td>
<td valign="top">

In order to support subscriptions out-of-the-box, create a route using `*.<custom-domain>` format and map it to the application router. The `* host` represents a wildcard that during runtime should be replaced by the actual subscriber sub-domain.

Without a custom domain, this type of route \(wildcard host\) cannot be created, only a fixed host can be used. Without a custom domain, the route format will be `<subdomain>-<myapprouter>.<scp domain>`. It means that for each new subscriber you need to create a new route with the expected sub-domain.



</td>
</tr>
<tr>
<td valign="top">

Solution



</td>
<td valign="top">

If you do not have a custom domain before subscribing to the application router, create a route with the expected subscriber sub-domain.



</td>
</tr>
</table>

