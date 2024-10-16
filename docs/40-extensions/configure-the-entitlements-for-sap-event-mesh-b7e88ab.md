<!-- loiob7e88abcc00044ec9c81c629753e3963 -->

# Configure the Entitlements for SAP Event Mesh

To be able to consume SAP S/4HANA Cloud events, you need to configure the entitlements for SAP Event Mesh for the subaccount in SAP BTP.



## Context

The *messaging* service plan connects SAP S/4HANA Cloud tenant to SAP Event Mesh for the subaccount where the SAP Event Mesh service entitlement is configured. This SAP Event Mesh service instance allows you to consume events from SAP S/4HANA Cloud.

You need to configure the entitlements for the SAP Event Mesh service to create an SAP Event Mesh service instance. Then, you bind this service instance to an application to consume events from this application.



<a name="loiob7e88abcc00044ec9c81c629753e3963__steps_zlg_4sz_khb"/>

## Procedure

1.  In SAP BTP cockpit, navigate to the global account that contains the subaccount in which you want to make your SAP system accessible.

2.  In the navigation area, choose *Entitlements* \> *Entity Assignments*.

3.  On the *Entity Assignments* screen, select your subaccount in the *Subaccounts/Directories* field.

4.  Choose *Edit*, and then choose *Add Service Plans*.

5.  Select the *SAP Event Mesh* service.

6.  In the *Service Details* area, select the system you have registered. In the *Available Plans* area, select the *default* service plan, and then choose *Add Service Plan*.

7.  Choose *Save*.


**Related Information**  


[Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/managing-entitlements-and-quotas-using-the-cockpit-c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

