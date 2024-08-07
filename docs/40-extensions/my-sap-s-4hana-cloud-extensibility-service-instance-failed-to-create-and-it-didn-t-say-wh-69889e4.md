<!-- loio69889e40aae04c06b05df57645323bf5 -->

# My SAP S/4HANA Cloud Extensibility Service Instance Failed to Create and It Didn't Say Why

My SAP S/4HANA Cloud Extensibility service instance failed to create and it didn't say why.



<a name="loio69889e40aae04c06b05df57645323bf5__section_c1h_xrx_dcc"/>

## Issue/Symptom

You are trying to create an SAP S/4HANA Cloud Extensibility service instance but the creation fails with no error message.



<a name="loio69889e40aae04c06b05df57645323bf5__section_f2p_ksx_dcc"/>

## Solution

This is what you can do:

-   You can use the Cloud Foundry command line interface to get the error message by executing the command:

    `cf service <service_instance_name>`

    Check for any error messages there.

-   Can you reach the SAP S/4HANA Cloud tenant? Check that the tenant is not in maintenance or being updated.


If this didn't help, you can try some more specific actions. What service plan are you using?



### I am using the messaging service plan

**Issue/Symptom**

Your SAP S/4HANA Cloud Extensibility service instance of the messaging plan failed to create and it didn't say why.

**Solution**

Try to do the following:

-   Is the Enterprise Messaging Integration scenario \(SAP\_COM\_0092\) enabled on your SAP S/4HANA Cloud tenant? Check whether you see it in the **Display Communication Scenarios** application in your SAP S/4HANA Cloud tenant.
-   The clients for SAP Event Mesh require unique values \(within your subaccount in SAP BTP\) for the **emname** and **namespace** properties. In the *messaging* plan, you have either provided these manually, or you have only set the **emClientId** property and let it generate them. If the latter, then these values would be **emClientId\>** for **emname** and **sap/S4HANAOD/emClientId\>** for **namespace**. Check whether your subaccount already has existing clients with such **emname** or **namespace**values. You can do this by using the **Enterprise Messaging Business Application** from the SAP Event Mesh subscription of your subaccount. See [View Event Catalog for a Subaccount](https://help.sap.com/docs/SAP_EM/bf82e6b26456494cbdd197057c09979f/01884b95c5ef4f0f8b6e806c9c901b1f.html).



### I am using the api-access service plan

**Issue/Symptom**

Your SAP S/4HANA Cloud Extensibility service instance of the api-access plan failed to create and it didn't say why.

**Solution**

Try to do the following:

-   Is the communication scenario with the **scenarioId** that you provided enabled on that tenant? Check whether you see it in the **Display Communication Scenarios** application in your SAP S/4HANA Cloud tenant.
-   Are you using supported authentication types? In the scenario definition, you can see which authentication types are supported for both outbound and inbound connectivity. Verify that the types you are providing in the descriptor are supported by the scenario.

