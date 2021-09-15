<!-- loio6ef40dfc2ef14bb08c28cd53b4de4c0b -->

# Services

If you want to create a service in the Cloud Foundry environment using the SAP Cloud Deployment service, you must define an MTA resource first. These resources can have different types and parameters which modify their behavior. There is a predefined set of supported resource types, that in most cases represents certain combination of service offering and plan. See [Generic MTA Resource Types](Resources_9e34487.md#loio9e34487b1a8643fb9a93ae6c4894f015__section_mtaResourceTypes).

For a more flexible approach, use the resource types listed below.

> ### Note:  
> In most of cases, MTA resources represent a Cloud Foundry service, but there are cases where they represent a different platform entity, for example a service key. They can even serve only to a group of configurations. See [Resources](Resources_9e34487.md) for more information.

-   **[Service Creation Parameters](Service_Creation_Parameters_a36df26.md "Some services support additional configuration parameters in the
			create-service request. These parameters are parsed in a valid JSON
		object containing the service-specific configuration parameters. ")**  
Some services support additional configuration parameters in the `create-service` request. These parameters are parsed in a valid JSON object containing the service-specific configuration parameters.
-   **[Service Binding Parameters](Service_Binding_Parameters_c7b09b7.md "Some services support additional configuration parameters in the
			create-bind request; these parameters are passed in a valid JSON
		object containing the service-specific configuration parameters.")**  
Some services support additional configuration parameters in the `create-bind` request; these parameters are passed in a valid JSON object containing the service-specific configuration parameters.
-   **[Service Tags](Service_Tags_3e36d13.md "Some services provide a list of tags that are later added to the
			VCAP_SERVICES environment variable. These tags provide a more generic
		way for applications to parse VCAP_SERVICES for credentials. ")**  
Some services provide a list of tags that are later added to the *<VCAP\_SERVICES\>* environment variable. These tags provide a more generic way for applications to parse *<VCAP\_SERVICES\>* for credentials.
-   **[Service Broker Creation](Service_Broker_Creation_ee1189a.md "Service brokers are applications that advertise a catalog of service offerings and
		service plans, as well as interpreting calls for creation, binding, unbinding, and deletion.
		The deploy service supports automatic creation (and update) of service brokers as part of an
		application deployment process.")**  
Service brokers are applications that advertise a catalog of service offerings and service plans, as well as interpreting calls for creation, binding, unbinding, and deletion. The deploy service supports automatic creation \(and update\) of service brokers as part of an application deployment process.
-   **[Service Keys](Service_Keys_32297f1.md)**  


