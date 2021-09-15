<!-- loio407d1266017f4b529b61665fa7408c41 -->

# Using Kyma Eventing with SAP Event Mesh

Learn more about Kyma runtime's event service and how to use it with SAP Event Mesh.



## Overview

You can send and receive events in Kyma thanks to the built-in Eventing infrastructure. By default, Kyma clusters have an Eventing backend based on the [NATS](https://nats.io/) technology. However, it is possible to switch this backend to SAP Event Mesh.

For more details, see the Kyma documentation on [Eventing](https://kyma-project.io/docs/components/eventing/).



## Development tutorials

To learn more about using events in Kyma, see these tutorials:

-   [Trigger a Microservice with an Event](https://developers.sap.com/tutorials/cp-kyma-microservice-trigger.html)

-   [Trigger a Function with an Event](https://kyma-project.io/docs/components/serverless/#tutorials-trigger-a-function-with-an-event)



## Switch the Kyma Eventing backend to SAP Event Mesh

You can switch the Eventing backend from NATS to SAP Event Mesh by following these steps:

1.  To generate a SAP Event Mesh secret, go to**Service Management \> Catalog** and search for Event Mesh.
2.  Click on**Add** and use this sample config.json file:

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

    In the file above, you need to replace**\{EVENT\_MESH\_NAME\}** and **\{EVENT\_MESH\_NAMESPACE\}** with your own values.

    > ### Note:  
    > The**\{EVENT\_MESH\_NAMESPACE\}** field cannot exceed 64 characters, or begin or end with a dot or hyphen. This is because it needs to follow the SAP Event Specification, which is based on the[Cloud Events Specification](https://github.com/cloudevents/spec/blob/v1.0/spec.md).

3.  Go to**Service Management \> Instances** and click on the newly-created Service Instance.
4.  Click on**Credentials \> Create Credentials**.
5.  In your Namespace, go to **Configuration \> Secrets**.
6.  Click on the**Edit** button next to your Secret and label the Secret with **kyma-project.io/eventing-backend: beb**. In the editor, this should look like:

    ```
      labels:
          kyma-project.io/eventing-backend: beb
    ```




<a name="loio407d1266017f4b529b61665fa7408c41__section_dj4_p22_ypb"/>

## Switch the Kyma Eventing backend back to the default

Follow these steps to switch the Eventing backend from SAP Event Mesh back to the NATS default:

1.  In your Namespace, go to **Configuration \> Secrets**.
2.  Delete the**kyma-project.io/eventing-backend=beb** Secret or unlabel the Secret.

    > ### Note:  
    > There can be only one SAP Event Mesh Secret in the whole Kyma cluster which is labeled. If there are multiple Secrets, the Eventing infrastructure will be marked as not ready.


