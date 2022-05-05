<!-- loio407d1266017f4b529b61665fa7408c41 -->

# Using Kyma Eventing with SAP Event Mesh

Learn more about the event service in Kyma runtime and how to use it with SAP Event Mesh.



<a name="loio407d1266017f4b529b61665fa7408c41__context_fhs_qf3_3rb"/>

## Context

You can send and receive events in Kyma thanks to the built-in Eventing infrastructure. By default, Kyma clusters have an Eventing backend based on the [NATS](https://nats.io/) technology. However, it is possible to switch this backend to [SAP Event Mesh](https://help.sap.com/viewer/product/SAP_EM/Cloud/en-US).

For more details, see the Kyma documentation on [Eventing](https://kyma-project.io/docs/kyma/latest/01-overview/main-areas/eventing/).

To learn more about using events in Kyma, see these development tutorials:

-   [Trigger a Microservice with an Event](https://developers.sap.com/tutorials/cp-kyma-microservice-trigger.html)

-   [Trigger a Function with an Event](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-eventing/)


You can switch the Kyma Eventing backend from NATS to SAP Event Mesh by following these steps:



<a name="loio407d1266017f4b529b61665fa7408c41__steps_afw_5f3_3rb"/>

## Procedure

1.  Log in to Kyma Dashboard. The URL is in the *Overview* section of your subaccount.

2.  To generate a SAP Event Mesh secret, select a namespace and go to**Service Management \> Catalog** and search for Event Mesh.

3.  Select **Add** and use the following sample config.json file, replacing **\{EVENT\_MESH\_NAME\}** and **\{EVENT\_MESH\_NAMESPACE\}** with your own values:

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

    > ### Note:  
    > The **\{EVENT\_MESH\_NAMESPACE\}** field cannot exceed 64 characters, or begin or end with a dot or hyphen. This is because it's necessary to follow the SAP Event Specification, which is based on the [CloudEvents Specification](https://github.com/cloudevents/spec/blob/v1.0/spec.md). For more information, read the [SAP Event Mesh documentation](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/00d56d697c7549408cfacc8cb6a46b11.html).

4.  Go to *Service Management* \> *Instances* and select the new Service Instance.

5.  Select *Credentials* \> *Create Credentials*.

6.  In your Namespace, go to *Configuration* \> *Secrets*.

7.  Select *Edit* and label the Secret with `kyma-project.io/eventing-backend: beb`.

    In the editor, you should see the following:

    ```
      labels:
          kyma-project.io/eventing-backend: beb
    ```




<a name="loio407d1266017f4b529b61665fa7408c41__result_fr1_4g3_3rb"/>

## Results

You can use SAP Event Mesh.

There can be only one labeled SAP Event Mesh Secret in the whole Kyma cluster. If there are multiple Secrets, the Eventing infrastructure is marked as not ready.

> ### Note:  
> To switch the Eventing backend from SAP Event Mesh back to the NATS default, select your Namespace, go to *Configuration* \> *Secrets*, and delete \(or unlabel\) the `kyma-project.io/eventing-backend=beb` Secret.

