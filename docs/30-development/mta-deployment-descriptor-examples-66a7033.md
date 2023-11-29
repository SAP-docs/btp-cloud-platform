<!-- loio66a7033658ac4b5db33998c12dc9f37f -->

# MTA Deployment Descriptor Examples

Examples of MTA deployment descriptors.



> ### Note:  
> The format and available options in the MTA deployment descriptor could change with the newer versions of the MTA specification. Always specify the schema version when defining an MTA deployment descriptor, so that the SAP BTP is aware against which specific MTA specification version you are deploying.



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_glw_v5n_5jb"/>

## Example 1

Deployment descriptor with a resource \(managed service\)

> ### Example:  
> ```
> _schema-version: "3.1.0"
> ID: simple-mta
> version: 1.0.0
> 
> modules:
> - name: anatz
>   type: javascript.nodejs
>   requires:
>     - name: hdi-service
> 
> resources:
> - name: hdi-service
>   type: org.cloudfoundry.managed-service
>   parameters:
>     service: hana
>     service-plan: hdi-shared
>     
> 
> ```



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_jhd_v5n_5jb"/>

## Example 2

Deployment descriptor with the `keep-existing` parameter \(will keep the existing: environment, service-bindings and routes\)

> ### Example:  
> ```
> _schema-version: 3.1.0
> ID: anatz-keep-existing
> version: 4.0.0
> 
> modules:
> - name: anatz
>   type: staticfile
>   path: hello-world.zip
>   parameters:
>     memory: 64M
>     route: new-custom-route-${space}
>     keep-existing:
>       env: true
>       service-bindings: true
>       routes: true
> 
>     
> 
> ```



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_sw2_bvn_5jb"/>

## Example 3

Deployment descriptor with enabled parallel deployment of modules \(will deploy modules in parallel\)

> ### Example:  
> ```
> _schema-version: 3.1.0
> ID: hello-world
> version: 1.0.0
> parameters:
>   enable-parallel-deployments: true
> 
> modules:
> - name: hello-world
>   type: staticfile
>   path: content/hello_world.zip
> 
> - name: hello-world-first
>   type: staticfile
>   path: content/hello_world.zip
>     
> - name: hello-world-second
>   type: staticfile
>   path: content/hello_world.zip
> 
> - name: hello-world-third
>   type: staticfile
>   path: content/hello_world.zip
> 
> 
>     
> 
> ```



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_bsl_kvn_5jb"/>

## Example 4

Deployment descriptor with docker image module

> ### Example:  
> ```
> _schema-version: "3.1.0"
> ID: docker-mtar
> version: 2.0.1
> 
> modules:
> - name: docker-image
>   type: application
>   parameters:
>     docker:
>       image: cloudfoundry/test-app
> 
> 
>     
> 
> ```



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_y2s_nvn_5jb"/>

## Example 5

Deployment descriptor with optional resource

> ### Example:  
> ```
> _schema-version: "3.1.0"
> ID: ztana1
> version: 1.1.0
> 
> modules:
>   - name: ztana
>     type: javascript.nodejs
>     requires:
>       - name: test-resource
>       
> resources:
>   - name: test-resource
>     type: org.cloudfoundry.existing-service
>     optional: true
>     parameters:
>       service: non-required-service
> 
> 
> 
>     
> 
> ```



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_z5s_ftn_5jb"/>

## Example 6

A basic MTA deployment descriptor that is defined in an `mtad.yaml` file:

> ### Example:  
> ```
> _schema-version: "3.1" 
> ID: com.sap.xs2.samples.javahelloworld 
> version: 0.1.0 
>  
>  
> modules: 
>   - name: java-hello-world 
>     type: javascript.nodejs 
>     path: web/ 
>     requires: 
>       - name: java-uaa 
>       - name: java 
>         group: destinations 
>         properties: 
>           name: java 
>           url: ~{url} 
>           forwardAuthToken: true 
>   - name: java-hello-world-backend 
>     type: java.tomee 
>     path: java/target/java-hello-world.war 
>     provides:  
>       - name: java 
>         properties: 
>           url: ${default-url} 
>     properties: 
>       JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/webapps/ROOT/WEB-INF/resources.xml': {'service_name_for_DefaultDB' : 'java-hdi-container'}]" 
>     requires: 
>       - name: java-uaa 
>       - name: java-hdi-container 
>       - name: java-hello-world-db 
>   - name: java-hello-world-db 
>     type: com.sap.xs.hdi 
>     path: db/ 
>     requires: 
>       - name: java-hdi-container 
>  
> resources: 
>   - name: java-hdi-container 
>     type: com.sap.xs.hdi-container 
>      
>   - name: java-uaa 
>     type: com.sap.xs.uaa-space 
>     parameters: 
>       config-path: xs-security.json    
> 
> ```

> ### Note:  
> The example above is incomplete. To deploy a solution, you have to create an MTA extension descriptor with the user and password added there. You also have to create the MTA archive.



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_lys_dzn_sbb"/>

## Example 7

Another basic example of an MTA deployment descriptor.

> ### Sample Code:  
> ```
> _schema-version: "3.1" 
> ID: com.sap.xs2.samples.nodehelloworld
> version: 0.1.0
> 
> modules:
>   - name: node-hello-world
>     type: javascript.nodejs
>     path: web/
>     requires:
>       name: nodejs-uaa
>       - name: nodejs
>         group: destinations
>         properties:
>           name: backend
>           url: ~{url}
>           forwardAuthToken: true
>         properties-metadata:  
>           name:  
>            optional: false  
>            overwritable: false
>           url:  
>            overwritable: false  
>     parameters:
>       host: !sensitive ${user}-node-hello-world
>       memory: 128MB
>     parameters-metadata:  
>       memory:  
>         optional: true  
>         overwritable: true 
>   - name: node-hello-world-backend
>     type: javascript.nodejs
>     path: js/
>     provides:
>       - name: nodejs
>         properties:
>           url: "${default-url}"
>     requires:
>       - name: nodejs-uaa
>       - name: nodejs-hdi-container
>       - name: node-hello-world-db
>     parameters:
>       host: ${user}-node-hello-world-backend
> 
>   - name: node-hello-world-db
>     type: com.sap.xs.hdi
>     path: db/
>     requires:
>       - name: nodejs-hdi-container
>     parameters:
>       tasks:
>         - name: task-1                   #You can model Cloud Foundry tasks as described here. For additional information, check the Cloud Foundry "Information for Developers" document.
>           command: node deploy.js 
>           disk-quota: 1GB
>           memory: 1GB
> 
> resources:
>   - name: nodejs-hdi-container
>     type: com.sap.xs.hdi-container
>     parameters:
>       config:
>         schema: ${default-container-name}
>     
>   - name: nodejs-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       config-path: xs-security.json
>   - name: log
>     type: application-logs
>     optional: true
> 
> ```



<a name="loio66a7033658ac4b5db33998c12dc9f37f__section_xbt_nks_sbb"/>

## Example 8

A more complex example, which shows an MTA deployment description with the following modules:

-   A database model
-   An SAP UI5 application \(hello world\)
-   An application written in node.js

The UI5 application “hello-world” uses the environment variable *<ui5\_library\>* as a logical reference to some version of UI5 on a public Website.

> ### Sample Code:  
> ```
> ID: com.acme.xs2.samples.javahelloworld 
> version: 0.1.0 
> 
> modules:
>   - name: hello-world
>     type: javascript.nodejs
>     requires:
>       - name: uaa
>       - name: java_details
>         properties:
>           backend_url: ~{url3}/
> 
>     properties:
>       ui5_library: "https://sapui5.hana.acme.com/"
>     
>   - name: java-hello-world-backend
>     type: java.tomee
>     requires: 
>       - name: uaa
>       - name: java-hello-world-db        # deploy ordering
>       - name: java-hdi-container
>     provides: 
>       - name: java_details
>         properties:
>           url3: ${url}                   # the value of the place-holder ${url} 
>                                          # will be made known to the deployer
>   - name: java-hello-world-db
>     type: com.sap.xs.hdi
>     requires: 
>       - name: java-hdi-container
> 
> resources:
>   - name: java-hdi-container
>     type: com.sap.xs.hdi-container
>     
>   - name: java-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       name: java-uaa                          # the name of the actual service
> 
> ```

