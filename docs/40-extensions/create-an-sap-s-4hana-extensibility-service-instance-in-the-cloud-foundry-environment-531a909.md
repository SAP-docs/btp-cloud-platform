<!-- loio531a90945a854f60838429dbe1d8bdf5 -->

# Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment

Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event Mesh.



<a name="loio531a90945a854f60838429dbe1d8bdf5__prereq_fms_2dv_5lb"/>

## Prerequisites

-   Before creating an SAP S/4HANA Cloud Extensibility service instance in the Cloud Foundry environment, see [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md).

-   Have enabled Cloud Foundry environment for your subaccount. See [Enable Environment or Create Environment Instance](../50-administration-and-ops/enable-environment-or-create-environment-instance-78c14b6.md).

-   Have registered an SAP S/4HANA Cloud system. See[Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

-   Have configured the entitlements to the SAP S/4HANA Cloud Extensibility service. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md).




## Context

To configure the connectivity between the SAP S/4HANA Cloud tenant and Event Mesh and to enable the exchange of credentials between the two systems, you first need to create an *SAP S/4HANA Cloud Extensibility* service instance with service plan `messaging`. For more information about the `messaging` service plan, see [Supported Service Plans for SAP S/4HANA Cloud](supported-service-plans-for-sap-s-4hana-cloud-925c00a.md).

When creating this service instance, you create the required configurations in both the SAP S/4HANA Cloud tenant and the Event Mesh system associated with the subaccount in SAP BTP, so that events can flow.



<a name="loio531a90945a854f60838429dbe1d8bdf5__steps_nqw_ngm_lhb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in which you want to create a service instance.

2.  In the navigation area, choose *Services* \> *Service Marketplace*.

    All services available to you appear.

3.  To enable the integration with an SAP S/4HANA Cloud system that you have registered in the global account in SAP BTP, choose *SAP S/4HANA Cloud Extensibility*.

4.  In the *SAP S/4HANA Cloud Extensibility* page, choose *Create*.

5.  In the *New Instance or Subscription* wizard:

    1.  In the *Service* dropdown list, ensure you have selected the *SAP S/4HANA Cloud Extensibility* service.

    2.  In the *Plan* dropdown list, select the *messaging* service plan.

    3.  In the *Runtime Environment* dropdown list, select *Cloud Foundry*.

    4.  In the *Space* dropdown list, select your space. If you haven't create a space yet, you can do it at this point.

    5.  In the *System Name* dropdown list, select the SAP S/4HANA Cloud system you have registered.

    6.  In the *Instance Name* field, enter a name for your instance. Choose *Next*.

    7.  Specify a JSON file or specify parameters in the JSON format to define the communication arrangement for the communication scenario *Enterprise Eventing Integration \(SAP\_COM\_0092\)* in the SAP S/4HANA Cloud tenant and to configure the parameters for the Enterprise Messaging service. If you decide to define the communication arrangement later on, you have to delete this service instance and create it again. Choose *Next*.

        For more information about the structure of the JSON file, see [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON/YAML File](define-sap-s-4hana-cloud-extensibility-service-descriptor-json-yaml-file-2d50d91.md).

    8.  Choose *Create*.


    The newly created instance appears in the list of instances in the *Instance and Subscriptions* page.

    Alternatively, you can create the instance using cf CLI. To do so, execute the following command

    ```
    cf create-service s4-hana-cloud messaging emsconnect -c '{"systemName": "<system_name>","communicationArrangement": {"communicationArrangementName": "<communication_arrangement_name>","attributes": [{"name": "Channel","value": "<channel_name>"},{"name": "Description","value": "<short_description>"},{"name": "Topic Space","value": "<topic_to_be_used_by_events>"},{"name": "QoS","value": "<quality_of_service>"},{"name": "Reconnect Attempts","value": "<number_of_reconnect_attempts>"},{"name": "Reconnect wait time(sec)","value": "<time_before_trying_to_reconnect>"}]},"ems": {"parameters": {"emname": "enterprise_messaging_client_name","namespace": "enterprise-messaging_client_namespace":{"options": {<required_options>},"rules": {<required_rules>}}'
    ```

    For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a872531845d6416b8fa07a8b84875d7e.html).

    > ### Note:  
    > You can use the cf CLI to troubleshoot if the creation of the service instance fails. To do that, use this command in the cf CLI:
    > 
    > ```
    > cf service <service_instance_name>
    > ```




<a name="loio531a90945a854f60838429dbe1d8bdf5__postreq_jjk_j3h_vhb"/>

## Next Steps

[Configure Event Topics in SAP S/4HANA Cloud](configure-event-topics-in-sap-s-4hana-cloud-f5bbc57.md)

