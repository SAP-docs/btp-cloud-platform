<!-- loiob8e1953a618e47e1bd3c3a60c213226e -->

# Cross-MTA Dependencies

In addition to having dependencies to one or multiple modules or resources in the same MTA, modules can have dependencies with modules from other MTAs as well. For these so-called cross-MTA dependencies to work, the MTA that **provides** the dependencies must be set to declare them as “public”. Use the `configuration` resource to declare when one module consumes configurations from other MTAs.

> ### Caution:  
> Do not use this feature for storing sensitive content, for example credentials, as this data is stored unencrypted.

> ### Note:  
> The declaration method requires adding a resource in the deployment descriptor; the additional resource defines the provided dependency from the other MTA.



<a name="loiob8e1953a618e47e1bd3c3a60c213226e__section_m5p_ywx_nv"/>

## Cross-MTA Dependency Method: Resource Type “configuration”

This method can be used to access any entry that is present in the configuration registry. The parameters used in this cross-MTA declaration method are `provider-nid`, `provider-id`, `version`, and `target`. The parameters are all optional and are used to filter the entries in the configuration registry based on their respective fields. If any of these parameters is not present, the entries will not be filtered based on their value for that field. The `version` parameter can accept any valid Semver ranges.

When used for cross-MTA dependency resolution the `provider-nid` is always “`mta`”, the`provider-id` follows the format `*<mta-id\>*:*<mta-provides-dependency-name\>*` and the `version` parameter is the version of the provider MTA. In addition, as illustrated in the following example, the `target` parameter is structured and contains the name of the organization and space in which the provider MTA is deployed. In the following example, the placeholders `${org}` and `${space}` are used, which are resolved to the name of the organization and space of the consumer MTA. In this way, the provider MTA is deployed in the same space as the consumer MTA.

> ### Note:  
> As of version 3.0 of the MTA specification, the provided dependencies are no longer public by default. They have to be explicitly declared public for cross-MTA dependencies to work.

The following example shows the dependency declaration in the deployment descriptor of the “consumer” MTA :

> ### Sample Code:  
> Consumer MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "3.1" 
> ID: com.sap.sample.mta.consumer 
> version: 0.1.0 
> modules:
>   - name: consumer
>     type: java.tomee 
>     requires: 
>       - name: message-provider 
>         properties: 
>           message: ~{message} 
> 
> resources: 
>   - name: message-provider 
>     type: configuration 
>     parameters:
>       provider-nid: mta 
>       provider-id: com.sap.sample.mta.provider:message-provider 
>       version: ">=1.0.0" 
>       target: 
>         org: ${org}     # Specifies the org of the provider MTA
>         space: ${space} 
> ```

> ### Tip:  
> If no target organization or space is specified by the consumer, then the current organization and space are used to deploy the provider MTA.

The following example shows the dependency declaration in the deployment descriptor of the “provider” MTA :

> ### Sample Code:  
> Provider MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "3.1" 
> ID: com.sap.sample.mta.provider 
> version: 2.3.0
> 
> modules: 
>   - name: provider 
>     type: javascript.nodejs 
>     provides: 
>       - name: message-provider 
>         public: true 
>         properties: 
>           message: "Hello! This is a message provided by application \"${app-name}\", deployed in org \"${org}\" and space \"${space}\"!" 
> ```



<a name="loiob8e1953a618e47e1bd3c3a60c213226e__section_pks_lh3_1db"/>

## Cross-MTA Configuration Visibility

A “consumer” module must explicitly declare the organizations and spaces in which a “provider” is expected to be deployed, except if it is the same space as the consumer. The “provider” can define a white list that specifies the organizations and spaces from which the consumption of configuration data is permitted. It is not required to white list all the provider's spaces in its own organization.

> ### Note:  
> Previously, registry entries were visible from all organizations by default. Now, the default visibility setting is “visible within the current organization and all the organization's spaces”.

White lists can be defined on various levels. For example, a visibility white list could be used to ensure that a provider's configuration data is visible in the local space only, in all organizations and spaces, in a defined list of organizations, or in a specific list of organization and space combinations.

The options for white lists and the visibility of configuration data are similar to the options available for managed services. However, for visibility white lists, space developers are authorized to extend the visibility of configuration data beyond the space in which they work, without the involvement of an administrator. An administrator is required to release service plans to certain organizations.

Visibility is declared on the provider side by setting the parameter `visibility:` \(of type 'sequence'\), containing entries for the specified organization \(`org:`\) and space \(`space:`\). If no `visibility:` parameter is set, the default visibility value `org: ${org}, space: '*'` is used, which restricts visibility to consumers deployed into all spaces of the provider's organization. Alternatively, the value`org: '*'` can be set, which allows to bindings from all organizations and spaces. The white list can contain entries at the organization level only. This, however, releases configuration data for consumption from all spaces within the specified organizations, as illustrated in the following \(annotated\) example.

> ### Tip:  
> Since applications deployed in the same space are always considered “friends”, visibility of configuration data in the local space is always preserved, no matter which visibility conditions are set.

> ### Sample Code:  
> ```
> provides:
>   - name: backend
>     public: true
>     parameters:
>       visibility:          # a list of possible settings:
>        - org: ${org}       # for local org 
>          space: ${space}   # and local space
>        - org: org1         # for all spaces in org1
>        - org: org2         # for the specified combination (org2,space2)
>          space: space2
>        - org: ${org}       # default: all spaces in local org
>        - org: '*'          # all orgs and spaces
>        - org: '*'          
>          space: space3     # every space3 in every org
> ```

The authorization model ensures the following rules apply:

-   Only those users in the white-listed spaces can read or consume the provided configuration data.

-   Only users with the role “SpaceDeveloper” in the configuration-data provider's space can modify \(edit or delete\) configuration data.


-   **[Plug-ins](Plug-ins_791e17e.md "The SAP Cloud Deployment
                                    service
		supports a method that allows a multitarget applicaton to consume multiple configuration
		entries for each requires dependency. ")**  
The SAP Cloud Deployment service supports a method that allows a multitarget applicaton to consume multiple configuration entries for each `requires` dependency.

