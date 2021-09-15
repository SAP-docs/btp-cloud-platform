<!-- loio1764436d8faa473d9f7039fe65d308aa -->

# Definition of the MTA Resources

The service instance for xsuaa, SaaS provisioning and ABAP solution are modeled as MTA resources. In general, all values defined in the property “config” of the “parameters” section of a module will be used for the service instance creation. Thus, we need to define the same values as described in the approach without the MTA.

The “type” defines the service. We only use MTA resources that define a CF service which is fully managed by the MTA. Some of the available CF services have a dedicated type and others are handled by the generic one, “org.cloudfoundry.managed-service”. If the generic one is used, the name of the service must be specified using the parameter “service”.

The parameter “service-plan” defines the plan of the service. The parameter “service-name” defines the name of the service instance that will be created.

-   **[XSUAA](XSUAA_6069e4e.md)**  

-   **[SaaS Provisioning Service](SaaS_Provisioning_Service_8be9a3a.md)**  

-   **[ABAP Solution Service](ABAP_Solution_Service_4370115.md)**  


