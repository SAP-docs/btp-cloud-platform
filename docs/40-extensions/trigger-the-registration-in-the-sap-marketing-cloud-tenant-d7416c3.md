<!-- loiod7416c31f2164c8aa5bc744f85038631 -->

# Trigger the Registration in the SAP Marketing Cloud Tenant

Use this procedure to trigger the registration process for an SAP Marketing Cloud system that you want to pair with your global account in SAP BTP.



<a name="loiod7416c31f2164c8aa5bc744f85038631__prereq_kdr_fzq_13b"/>

## Prerequisites

You are an SAP Marketing Cloud tenant administrator.



<a name="loiod7416c31f2164c8aa5bc744f85038631__steps_dqj_qxq_13b"/>

## Procedure

1.  Log on to the SAP Marketing Cloud tenant, go to *Home*, *Communication Management* tab and then choose the *Maintain Extensions on SAP BTP* tile.

2.  In the *Maintain Extensions on SAP BTP* screen, in the *Integrations* section, choose *New*.

3.  In the *Integration Token* field, enter the content of the registration token from the SAP BTP cockpit.

4.  Choose *Save*. A new entry in the table appears with status *Enabling*.

5.  After the integration has finished successfully, you can refresh the table.

    .The status of the integration should have changed to *Enabled*.

6.  \(Optional\) If required, you can perform the following actions:

    -   Disable the integration. To do so, choose the *Disable* button in the *Action* column.
    -   Delete the integration. To do so, choose the *Delete* button in the *Actions* column.

        > ### Note:  
        > Before deleting an integration, make sure you have deleted any SAP S/4HANA Cloud Extensibility service instances for this integration in the SAP BTP cockpit. See [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md).



