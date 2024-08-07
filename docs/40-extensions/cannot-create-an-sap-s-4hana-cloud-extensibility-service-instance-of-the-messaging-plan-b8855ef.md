<!-- loiob8855efa448a4e40a4abd358ac9cb3e2 -->

# Cannot create an SAP S/4HANA Cloud Extensibility Service Instance of the Messaging Plan

Cannot create an SAP S/4HANA Cloud Extensibility service instance of the messaging plan.



<a name="loiob8855efa448a4e40a4abd358ac9cb3e2__section_bxp_crx_dcc"/>

## Issue/Symptom

You are trying to create an SAP S/4HANA Cloud Extensibility service instance of the messaging plan and you get the following error message:"Creation Failed."



<a name="loiob8855efa448a4e40a4abd358ac9cb3e2__section_wwm_hrx_dcc"/>

## Reason

You are probably providing in the JSON file the same *emClientId* that was already used in the subaccount.



<a name="loiob8855efa448a4e40a4abd358ac9cb3e2__section_dnk_jrx_dcc"/>

## Solution

Make the value of the *emClientId* parameter unique within the subaccount.

**Related Information**  


[Set Up the Connectivity Between Event Mesh and the SAP S/4HANA Cloud Tenant](set-up-the-connectivity-between-event-mesh-and-the-sap-s-4hana-cloud-tenant-13c0366.md "")

