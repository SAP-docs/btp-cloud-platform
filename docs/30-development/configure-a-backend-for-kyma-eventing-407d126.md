<!-- loio407d1266017f4b529b61665fa7408c41 -->

# Configure a Backend for Kyma Eventing

The event service in Kyma runtime supports two backends: NATS and SAP Event Mesh. Learn how to set up your preferred eventing backend.



<a name="loio407d1266017f4b529b61665fa7408c41__prereq_uvp_3w3_dzb"/>

## Prerequisites

-   If you want to use NATS, enable the NATS module. See [Enable and Disable a Kyma Module](../50-administration-and-ops/enable-and-disable-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   If you want to use [SAP Event Mesh](https://help.sap.com/viewer/product/SAP_EM/Cloud/en-US), follow the steps below.




<a name="loio407d1266017f4b529b61665fa7408c41__context_fhs_qf3_3rb"/>

## Context

You can send and receive events in Kyma with the built-in Eventing infrastructure. To learn more about Kyma Eventing, read [What is Eventing in Kyma?](https://kyma-project.io/#/eventing-manager/user/README) and follow the [Eventing tutorials](https://kyma-project.io/#/eventing-manager/user/tutorials/evnt-01-prerequisites).

By default, Kyma clusters have an Eventing backend based on the [NATS](https://nats.io/) technology. You can switch the Kyma Eventing backend from NATS to SAP Event Mesh by following these steps:



<a name="loio407d1266017f4b529b61665fa7408c41__steps_afw_5f3_3rb"/>

## Procedure

1.  Log in to Kyma dashboard. The URL is in the *Overview* section of your subaccount.

2.  To generate an SAP Event Mesh Secret, select a Namespace and go to *Service Management* \> *BTP Service Instance*.

3.  Click *Create Service Instance +*, and enter the following information:

    -   *Name* - enter or generate the name of your instance.

    -   *Offering Name* - type: `enterprise-messaging`.

    -   *Plan Name* - type: `default`.


4.  Go to the *YAML* tab, and paste the following sample `config.json` file under the `parameters` key.

    ```
    {
      "options": {
          "management": true,
          "messagingrest": true
      },
      "rules": {
          "topicRules": {
              "publishFilter": [
                  "${namespace}/*"
              ],
              "subscribeFilter": [
                  "${namespace}/*"
              ]
          },
          "queueRules": {
              "publishFilter": [
                  "${namespace}/*"
              ],
              "subscribeFilter": [
                  "${namespace}/*"
              ]
          }
      },
      "resources": {
        "units": "10"
      },
      "version": "1.1.0",
      "emname": "{EVENT_MESH_NAME}",
      "namespace": "{EVENT_MESH_NAMESPACE}"
    }
    ```

5.  Replace `{EVENT_MESH_NAME}` and `{EVENT_MESH_NAMESPACE}` with your own values.

    > ### Note:  
    > The `{EVENT_MESH_NAMESPACE}` field cannot exceed 64 characters, or begin or end with a dot or hyphen: It must follow the SAP Event Specification, which is based on the [CloudEvents Specification](https://github.com/cloudevents/spec/blob/v1.0/spec.md). For more information, read the [SAP Event Mesh documentation](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/00d56d697c7549408cfacc8cb6a46b11.html).

6.  Go to *Service Management* \> *BTP Service Bindings* and click *Create Service Binding +*.

7.  Provide the name of your binding, select the name of your instance from the list, and click *Create*.

8.  Go to the `kyma-system` namespace.

9.  Go to *Kyma* \> *Eventing*, open the `eventing` resource, and click *Edit*.

10. In the *Backend Type* section, select `EventMesh` from the dropdown.

11. In the *Event Mesh Secret* section, select the `namespace` and `name` of your binding, and click *Update*.




<a name="loio407d1266017f4b529b61665fa7408c41__result_fr1_4g3_3rb"/>

## Results

You can use SAP Event Mesh.



<a name="loio407d1266017f4b529b61665fa7408c41__postreq_vqh_yw3_dzb"/>

## Next Steps

You can switch the Eventing backend from SAP Event Mesh back to NATS:

1.  Log in to Kyma dashboard and select the `kyma-system` namespace.

2.  Go to *Kyma* \> *Eventing*, open the `eventing` resource and click *Edit*.

3.  In the *Backend Type* section, select `NATS` from the dropdown, and click *Update*.


**Related Information**  


[Enable and Disable a Kyma Module](../50-administration-and-ops/enable-and-disable-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c "To use a Kyma module, you must enable it first. Use Kyma dashboard or Kyma CLI to do that. If you don't need the module anymore, disable it to save resources.")

