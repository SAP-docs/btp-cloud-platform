<!-- loiob7e88abcc00044ec9c81c629753e3963 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure the Entitlements for SAP Event Mesh

To be able to consume SAP S/4HANA Cloud events, you need to configure the entitlements for SAP Event Mesh for the subaccount in SAP BTP.



## Context

The *messaging* service plan connects SAP S/4HANA Cloud tenant to SAP Event Mesh for the subaccount where the SAP Event Mesh service entitlement is configured. This SAP Event Mesh service instance allows you to consume events from SAP S/4HANA Cloud.

You need to configure the entitlements for the SAP Event Mesh service to create an SAP Event Mesh service instance. Then, you bind this service instance to an application to consume events from this application.



<a name="loiob7e88abcc00044ec9c81c629753e3963__steps_zlg_4sz_khb"/>

## Procedure

1.  In SAP BTP cockpit, navigate to the global account that contains the subaccount in which you want to make your SAP system accessible.

2.  In the navigation area, choose *Entitlements*. Then, depending on the feature set you are using, you have to follow different steps. See [Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md).

    -   If you are using feature set A, you have to:
        1.  In the navigation area, choose *Entitlements* \> *Subaccount Assignments*.
        2.  Select your subaccount from the drop down menu, choose *Go*, and then choose *Configure Entitlements*.

            > ### Tip:  
            > If your global account contains more than 20 subaccounts, choose <span class="SAP-icons"></span> to open up the value help dialog. There you can filter subaccounts by role, environment and region to make your selection easier and faster. You can only select a maximum of 50 subaccounts at once.


    -   If you are using feature set B, you have to:
        1.  In the navigation area, choose *Entitlements* \> *Entity Assignments*.
        2.  On the *Entity Assignments* screen, select your subaccount in the*Select Entities* field.
        3.  Choose *Go*, and then choose *Configure Entitlements*.


3.  Choose *Add Service Plans*, and then select the *SAP Event Mesh* service.

4.  In the *Available Service Plans* area, select the system you have registered and the *default* service plan, and then choose *Add Service Plan*.

5.  Choose *Save*.


**Related Information**  


[Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

