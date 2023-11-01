<!-- loio407d1266017f4b529b61665fa7408c41 -->

# Configure a Backend for Kyma Eventing

The event service in Kyma runtime supports two backends: NATS and SAP Event Mesh. Learn how to set up your preferred eventing backend.



<a name="loio407d1266017f4b529b61665fa7408c41__prereq_uvp_3w3_dzb"/>

## Prerequisites

-   If you want to use NATS, enable the NATS module. See [Enable and Disable a Kyma Module](../50-administration-and-ops/enable-and-disable-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   If you want to use [SAP Event Mesh](https://help.sap.com/viewer/product/SAP_EM/Cloud/en-US), follow the steps below.




<a name="loio407d1266017f4b529b61665fa7408c41__context_fhs_qf3_3rb"/>

## Context

You can send and receive events in Kyma with the built-in Eventing infrastructure. To learn more about Kyma Eventing, read [What is Eventing in Kyma?](https://kyma-project.io/#/01-overview/eventing/) and follow the [Eventing tutorials](https://kyma-project.io/#/03-tutorials/00-eventing/).

By default, Kyma clusters have an Eventing backend based on the [NATS](https://nats.io/) technology. You can switch the Kyma Eventing backend from NATS to SAP Event Mesh by following these steps:



<a name="loio407d1266017f4b529b61665fa7408c41__steps_afw_5f3_3rb"/>

## Procedure

1.  Log in to Kyma Dashboard. The URL is in the *Overview* section of your subaccount.

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

7.  Provide the name of your binding, and select the name of your instance from the list, then click *Create*.

8.  In your Namespace, go to *Configuration* \> *Secrets*.

9.  To switch the backend to SAP Event Mesh, you must label your Secret. Choose the name of your binding, click *Edit*, and label the Secret with `kyma-project.io/eventing-backend: beb`.

    > ### Note:  
    > To see the SAP Event Mesh Secret information, click *Decode*.

    In the editor, you see the following:

    ```
      labels:
          kyma-project.io/eventing-backend: beb
    ```




<a name="loio407d1266017f4b529b61665fa7408c41__result_fr1_4g3_3rb"/>

## Results

You can use SAP Event Mesh.

There can be only one labeled SAP Event Mesh Secret in the whole Kyma cluster. If there are multiple Secrets, the Eventing infrastructure is marked as not ready.



<a name="loio407d1266017f4b529b61665fa7408c41__postreq_vqh_yw3_dzb"/>

## Next Steps

You can switch the Eventing backend from SAP Event Mesh back to NATS:

1.  Log in to Kyma Dashboard and select your namespace.

2.  Go to *Configuration* \> *Secrets*, and delete the Secret.

3.  Enable the NATS module.


**Related Information**  


[Enable and Disable a Kyma Module](../50-administration-and-ops/enable-and-disable-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c "If you want to use a Kyma module, you must enable it. If you don't need it anymore, disable the module to save resources.")

