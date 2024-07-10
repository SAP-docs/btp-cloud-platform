<!-- loiobe0acbfdd48d4678b8b4d81f708c373b -->

# Automatic Creation of Destination Configurations

If you use the HTML5 application deployer together with an application router managed by SAP for the Kyma runtime, you can enable that the required destination configurations pointing to the service instances are created automatically.

To enable the automatic creation of destination configurations, add the environment variable SAP\_CLOUD\_SERVICE in the deployment.yaml or Helm chart of the Kyma project and provide the value of the sap.cloud.service property from the manifest.json file of the HTML5 application that you want to deploy. The destination configurations can point to instances of the following services:

-   An HTML5 Application Repository service instance of the app-host service plan \(mandatory\)

-   An SAP Authorization and Trust Management \(XSUAA\) service instance \(optional\)

    To create a destination that points to an SAP Authorization and Trust Management \(XSUAA\) service instance, the SAP Authorization and Trust Management \(XSUAA\) service instance and a destination service instance must be bound to the HTML5 application deployer.

-   A business service instance \(optional\)

-   One or more backend destinations that point to cloud or on-premise backend applications.

    In addition to the SAP\_CLOUD\_SERVICE environment variable, also add the environment variable BACKEND\_DESTINATIONS to create backend destinations.


> ### Note:  
> To enable app-to-app navigation, you also have to add the environment variable IAS\_DEPENDENCY\_NAME and provide the name of the dependency that has been configured for the Identity Authentication token exchange that is required for app-to-app navigation. For more information about how to configure the dependency for app-to-app navigation, see [Consume an API from Another Application](https://help.sap.com/docs/identity-authentication/identity-authentication/consume-api-from-another-application?version=Cloud).

You would typically use the automatic creation of destination configurations in Kubernetes if the HTML5 application deployer application has been previously uploaded as a docker image to Artifactory or Docker Hub. See, for example, this Kubernetes deployment:

> ### Sample Code:  
> ```
> --
> apiVersion: apps/v1
> kind: Deployment
> metadata:
>   name: html5appdeployer
>   namespace: default
>   labels:
>     app: html5appdeployer
> spec:
>   replicas: 1
>   selector:
>     matchLabels:
>       app: html5appdeployer
>   template:
>     metadata:
>       labels:
>         app: html5appdeployer
>     spec:
>       containers:
>         - image: html5-apps-repo.docker.repositories.sap.ondemand.com/myapp-html5-app-deployer:1.0
>           name: html5appdeployer
>           volumeMounts:
>             - name: html5-repo-app-host-volume
>               mountPath: "/etc/secrets/sapcp/html5-apps-repo/myapp-app-host-instance"
>               readOnly: true
>             - name: xsuaa-volume
>               mountPath: "/etc/secrets/sapcp/xsuaa/myapp-xsuaa-instance"
>               readOnly: true
>             - name: destination-volume
>               mountPath: "/etc/secrets/sapcp/destination/myapp-destination-instance"
>               readOnly: true
>           env:
>             - name: PORT
>               value: "5000"
>             - name: SAP_CLOUD_SERVICE
>               value: "com.sap.test.service"
>             - name: BACKEND_DESTINATIONS
>               value: "[{
>               \"Name\":\"myapp-backend\",
>               \"Description\":\"My application backend\",
>               \"Type\":\"HTTP\",
>               \"ProxyType\":\"Internet\",
>               \"URL\":\"https://<backendApplicationHost>/\",
>               \"Authentication\":\"NoAuthentication\",
>               \"HTML5.ForwardAuthToken\": true}]"
>       imagePullSecrets:
>         - name: backend-dockersecret
>       volumes:
>         - name: html5-repo-app-host-volume
>           secret:
>             secretName: myapp-app-host-binding
>         - name: xsuaa-volume
>           secret:
>             secretName: myapp-xsuaa-binding
>         - name: destination-volume
>           secret:
>             secretName: myapp-destination-binding
> ```

