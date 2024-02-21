<!-- loio791e17e5501849b28061718c8bec7384 -->

# Plug-ins

The SAP Cloud Deployment service supports a method that allows a multitarget applicaton to consume multiple configuration entries for each `requires` dependency.

The following is an example for multiple `requires` dependencies in the MTA Deployment Descriptor \(`mtad.yaml`\):

> ### Sample Code:  
> ```
> _schema-version: "2.1" 
> ID: com.acme.framework 
> version: "1.0" modules:
>   - name: framework 
>     type: javascript.nodejs 
>     requires: 
>       - name: plugins
>         list: plugin_configs 
>         properties: 
>           plugin_name: ~{name} 
>           plugin_url: ~{url}/sources 
>         parameters: 
>           managed: true # true | false. Default is false 
> 
> resources: 
>   - name: plugins 
>     type: configuration 
>     parameters: 
>       target: 
>         org: ${org} 
>         space: ${space} 
>       filter: 
>         type: com.acme.plugin 
> ```

The MTA deployment descriptor shown in the example above contains a module that specifies a `requires` dependency to a configuration resource. Since the `requires` dependency has a `list` property, the deploy service attempts to find multiple configuration entries that match the criteria specified in the configuration resource.

> ### Tip:  
> It is possible to create a subscription for a **single** configuration entry, for example, where no “`list:`” element is defined in the required dependency.

> ### Note:  
> The filter parameter can be used in combination with other configuration resource specific parameters, for example: `provider-nid`, `provider-id`, `target`, and `version`.

The resource itself contains a `filter` parameter that is used to filter entries from the configuration registry based on their content. In the example shown above, the filter only matches entries that are provided by an MTA deployed in the current space, which have a `type` property in their content with a value of `com.acme.plugin`.

If the `list` element is missing, the values matched by the resources filter are **single** configuration entries – not the usual list of multiple configuration entries. In addition, if either no value or multiple values are found during the deployment of the consuming \(subscribing\) MTA, the deployment operation fails. If a provider \(plug-in\) adds more configuration details after the deployment of subscriber applications, these applications won't get the new information right away. They will only receive these details when they get updated. However, this update will not be successful because there will be several configuration entries available at that point.

The XML document in the following example shows some sample configuration entries, which would be matched by the filter if they were present in the registry.

> ### Sample Code:  
> MTA Configuration Entries Matched in the Registry
> 
> ```
> <configuration-entry>
>   <id>8</id> 
>   <provider-nid>mta</provider-nid> 
>   <provider-id>com.sap.sample.mta.plugin-1:plugin-1</provider-id> 
>   <provider-version>0.1.0</provider-version> 
>   <target-space>2172121c-1d32-441b-b7e2-53ae30947ad5</target-space> 
>   <content>{"name":"plugin-1","type":"com.acme.plugin","url":"https://xxx.mo.sap.corp:51008"}</content> 
> </configuration-entry> 
> <configuration-entry> 
>   <id>10</id> 
>   <provider-nid>mta</provider-nid> 
>   <provider-id>com.sap.sample.mta.plugin-2:plugin-2</provider-id> 
>   <provider-version>0.1.0</provider-version> 
>   <target-space>2172121c-1d32-441b-b7e2-53ae30947ad5</target-space> 
>   <content>{"name":"plugin-2","type":"com.acme.plugin"}</content> 
> </configuration-entry> 
> ```

The JSON document in the following example shows the environment variable that is created from the `requires` dependency defined in the example deployment descriptor above, assuming that the two configuration entries shown in the XML document were matched by the filter specified in the configuration resource.

> ### Note:  
> References to non-existing configuration entry content properties are resolved to “`null`”. In the example above, the configuration entry published for `plugin-2` does not contain a `url` property in its content. As a result, the environment variable created from that entry is set to “`null`” for `plugin_url`.

> ### Sample Code:  
> Application Environment Variable
> 
> ```
> plugin_configs: [ 
>   { 
>     "plugin_name": "plugin-1",  
>     "plugin_url": "https://xxx.mo.sap.corp:51008/sources"  
>   },  
>   {  
>     "plugin_name": "plugin-2",  
>     "plugin_url": null  
>   } 
> ] 
> ```

`Requires` dependencies support a special parameter named “`managed`”, which registers as a “subscriber” the application created from the module containing the `requires` dependency. This registration causes the application's environment to be updated if any new configuration entries are published in the configuration registry during the deployment of another MTA. Those new entries must also match the subscription filter of the application. This will cause the application to restart so it can recognize the updated environment state.

> ### Tip:  
> When starting the deployment of an MTA \(with the `cf deploy` command\), you can use the special option `--no-restart-subscribed-apps` to specify that, if the publishing of configuration entries created for that MTA result in the update of a subscribing application's environment, then that application should **not** be restarted.

