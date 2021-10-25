<!-- loioc2d4d873ab0c41ecb5b4e7ed2b909700 -->

# Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment

Use this procedure to enable the SAP Event Mesh service for the subaccount where your extension application will reside.



## Context

To enable the SAP Event Mesh service for your subaccount in SAP BTP, you have to go through the following steps.



## Procedure

1.  Prepare a JSON file that contains details of a message client. See [Define SAP Event Mesh Service Descriptor JSON File](Define_SAP_Event_Mesh_Service_Descriptor_JSON_File_5722fc4.md).

2.  Create an SAP Event Mesh service instance for the application to consume SAP S/4HANA Cloud events.

    1.  In the SAP BTP cockpit, navigate to the space in which you want to create a service instance.

    2.  In the navigation area, choose *Services* \> *Service Marketplace*, and then choose *Event Mesh* in the *Service Marketplace* panel.

    3.  From the *Event Mesh* service tile, choose *Create* and follow the steps in the wizard to subscribe to the service.

    4.  In the *New Instance or Subscription* wizard:

        1.  In the *Service* dropdown list, select *Event Mesh*.

        2.  In the *Plan* dropdown list select the *default* service plan.

        3.  In the *Runtime Environment* dropdown list, select *Cloud Foundry*.

        4.  In the *Space* dropdown list, select your Cloud Foundry space.

        5.  In the *Instance Name* field, enter a name for your instance. Choose *Next*.

        6.  Specify the JSON file you prepared in **Step 1**. Choose *Next*.
        7.  Review and verify the instance details, and choose *Create*.





<a name="loioc2d4d873ab0c41ecb5b4e7ed2b909700__postreq_zd4_l15_b4b"/>

## Next Steps

[Create Queues and Subscribe to Them](Create_Queues_and_Subscribe_to_Them_e54e609.md)

