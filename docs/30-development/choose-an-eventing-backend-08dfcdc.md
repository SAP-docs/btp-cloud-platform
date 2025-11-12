<!-- loio08dfcdcaf4ff4914b70c8173731a9188 -->

# Choose an Eventing Backend

The Eventing module supports two backends: NATS and SAP Event Mesh. Learn how to set up your preferred eventing backend.



<a name="loio08dfcdcaf4ff4914b70c8173731a9188__prereq_uvp_3w3_dzb"/>

## Prerequisites

-   You have the Eventing module in your Kyma cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   If you want to use NATS, you have added the NATS module.

-   If you want to use SAP Event Mesh, you have configured it for Kyma Eventing. See [Configure SAP Event Mesh for Kyma Eventing](configure-sap-event-mesh-for-kyma-eventing-407d126.md).




<a name="loio08dfcdcaf4ff4914b70c8173731a9188__context_fhs_qf3_3rb"/>

## Context

You can send and receive events in Kyma with the Eventing module. By default, Kyma clusters have no eventing backend defined. You must set up an eventing backend, either based on the NATS technology or SAP Event Mesh.



<a name="loio08dfcdcaf4ff4914b70c8173731a9188__steps_afw_5f3_3rb"/>

## Procedure

1.  Log in to Kyma dashboard. The URL is in the *Overview* section of your subaccount.

2.  Go to the `kyma-system` namespace.

3.  Go to *Kyma* \> *Eventing*, open the `Eventing` resource, and choose *Edit*.

4.  Under *Backend Type*, select your preferred backend.

5.  If you selected *EventMesh*, go to *Event Mesh Secret*, and select the namespace and name of your SAP Event Mesh service binding.

    > ### Remember:  
    > If you selected *NATS*, make sure the NATS module is added.

6.  Choose *Save*.




<a name="loio08dfcdcaf4ff4914b70c8173731a9188__result_usl_5ls_5zb"/>

## Results

You have set up your eventing backend for Kyma.

If you want to choose another backend, edit the `Eventing` resource again, select the preferred backend, and save your changes.

You can no longer return to an empty eventing backend.



<a name="loio08dfcdcaf4ff4914b70c8173731a9188__postreq_i2m_jms_5zb"/>

## Next Steps

Learn more about the [Eventing Module](https://kyma-project.io/#/eventing-manager/user/README).

**Related Information**  


[Configure SAP Event Mesh for Kyma Eventing](configure-sap-event-mesh-for-kyma-eventing-407d126.md "If you want to use SAP Event Mesh as backend for the Eventing module, you must first set up the credentials.")

[SAP Event Mesh](https://help.sap.com/viewer/product/SAP_EM/Cloud/en-US)

