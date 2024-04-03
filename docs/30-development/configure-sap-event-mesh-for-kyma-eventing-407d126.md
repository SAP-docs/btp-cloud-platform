<!-- loio407d1266017f4b529b61665fa7408c41 -->

# Configure SAP Event Mesh for Kyma Eventing

If you want to use SAP Event Mesh as backend for Kyma Eventing, you must first set up the credentials.



<a name="loio407d1266017f4b529b61665fa7408c41__prereq_uvp_3w3_dzb"/>

## Prerequisites

-   The Kyma Eventing module is added to your cluster. See [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   The Kyma SAP BTP Operator module is added to your cluster.

-   You are using an enterprise account.




<a name="loio407d1266017f4b529b61665fa7408c41__steps_afw_5f3_3rb"/>

## Procedure

1.  Log in to Kyma dashboard. The URL is in the *Overview* section of your subaccount.

2.  To generate an SAP Event Mesh Secret, select a namespace and go to *Service Management* \> *BTP Service Instance*.

3.  Choose *Create Service Instance +*, and enter the following information:

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

5.  Replace *<\{EVENT\_MESH\_NAME\}\>* and *<\{EVENT\_MESH\_NAMESPACE\}\>* with your own values.

    > ### Note:  
    > The *<\{EVENT\_MESH\_NAMESPACE\}\>* field cannot exceed 64 characters, or begin or end with a dot or hyphen: It must follow the [SAP Event Specification](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/00d56d697c7549408cfacc8cb6a46b11.html).

6.  Go to *Service Management* \> *BTP Service Bindings* and choose *Create Service Binding +*.

7.  Provide the name of your binding, select the name of your instance from the list, and choose *Create*.




<a name="loio407d1266017f4b529b61665fa7408c41__result_fr1_4g3_3rb"/>

## Results

You have set up SAP Event Mesh for Kyma Eventing.



<a name="loio407d1266017f4b529b61665fa7408c41__postreq_idx_hwx_5zb"/>

## Next Steps

Choose SAP Event Mesh as your backend for Kyma Eventing.

**Related Information**  


[Choose a Backend for Kyma Eventing](choose-a-backend-for-kyma-eventing-08dfcdc.md "The event service in Kyma runtime supports two backends: NATS and SAP Event Mesh. Learn how to set up your preferred eventing backend.")

