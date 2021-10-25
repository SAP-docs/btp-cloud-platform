<!-- loio531a90945a854f60838429dbe1d8bdf5 -->

# Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment

Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event Mesh.



## Context

To configure the connectivity between the SAP S/4HANA Cloud tenant and Event Mesh and to enable the exchange of credentials between the two systems, you first need to create an *SAP S/4HANA Cloud Extensibility* service instance with service plan `messaging`. For more information about the `messaging` service plan, see [Supported Service Plans for SAP S/4HANA Cloud](Supported_Service_Plans_for_SAP_S4HANA_Cloud_925c00a.md).

When creating this service instance, you create the required configurations in both the SAP S/4HANA Cloud tenant and the Event Mesh system associated with the subaccount in SAP BTP, so that events can flow.



<a name="loio531a90945a854f60838429dbe1d8bdf5__steps_nqw_ngm_lhb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in which you want to create a service instance.

2.  In the navigation area, choose *Services* \> *Service Marketplace*.

    All services available to you appear.

3.  To enable the integration with an SAP S/4HANA Cloud system that you have registered in the global account in SAP BTP, choose *SAP S/4HANA Cloud Extensibility*.

4.  In the *SAP S/4HANA Cloud Extensibility* page, choose *Create Instance*.

5.  In the *New Instance* wizard:

    1.  In the *Service* dropdown list, ensure you have selected the *SAP S/4HANA Cloud Extensibility* service.

    2.  In the *Service Plan* dropdown list select the *messaging* service plan

    3.  A message ending with a link appears bellow the *Service Plan* field. Click on the link to finish the procedure. You are redirected to another page.

    4.  Choose *New Instance*.


6.  In the *Create Instance* wizard:

    1.  In the *Plan* dropdown list select the *messaging* service plan, and then in the *System Name* dropdown list select the SAP S/4HANA Cloud system that you have registered. Choose *Next*.

    2.  Specify a JSON file or specify parameters in the JSON format to define the communication arrangement for the communication scenario *Enterprise Eventing Integration \(SAP\_COM\_0092\)* in the SAP S/4HANA Cloud tenant and to configure the parameters for the Enterprise Messaging service. Choose *Next*.

        For more information about the structure of the JSON file, see [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON File](Define_SAP_S4HANA_Cloud_Extensibility_Service_Descriptor_JSON_File_2d50d91.md).

    3.  \(Optional\) If you have already deployed an application that you want to bind to the new service instance, choose it from the list. Choose *Next*.

    4.  Enter a name for your instance and choose *Finish*.


    Alternatively, you can create the instance using cf CLI. To do so, execute the following command

    ```nocode
    cf create-service s4-hana-cloud messaging emsconnect -c '{"systemName": "<system_name>","communicationArrangement": {"communicationArrangementName": "<communication_arrangement_name>","attributes": [{"name": "Channel","value": "<channel_name>"},{"name": "Description","value": "<short_description>"},{"name": "Topic Space","value": "<topic_to_be_used_by_events>"},{"name": "QoS","value": "<quality_of_service>"},{"name": "Reconnect Attempts","value": "<number_of_reconnect_attempts>"},{"name": "Reconnect wait time(sec)","value": "<time_before_trying_to_reconnect>"}]},"ems": {"parameters": {"emname": "enterprise_messaging_client_name","namespace": "enterprise-messaging_client_namespace":{"options": {*<required\_options\>*},"rules": {*<required\_rules\>*}}'
    ```

    The newly created instance appears in the list of instances in the *Instance* panel.




<a name="loio531a90945a854f60838429dbe1d8bdf5__postreq_jjk_j3h_vhb"/>

## Next Steps

[Configure Event Topics in SAP S/4HANA Cloud](Configure_Event_Topics_in_SAP_S4HANA_Cloud_f5bbc57.md)

