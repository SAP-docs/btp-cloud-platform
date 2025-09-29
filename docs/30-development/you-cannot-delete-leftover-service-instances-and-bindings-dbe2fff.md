<!-- loiodbe2fff1a9ab4cc58bc7b3039f0a4644 -->

# You Cannot Delete Leftover Service Instances and Bindings



<a name="loiodbe2fff1a9ab4cc58bc7b3039f0a4644__section_ez3_m4j_tgc"/>

## Symptom

After your Kyma cluster has become unavailable, some orphaned service instances and service bindings are still present in the SAP Business Technology Platform \(BTP\).



<a name="loiodbe2fff1a9ab4cc58bc7b3039f0a4644__section_mvp_n4j_tgc"/>

## Cause

You cannot access your Kyma cluster where the service instances and bindings were created. Without access to the cluster, you cannot use standard deletion methods.



<a name="loiodbe2fff1a9ab4cc58bc7b3039f0a4644__section_pfl_44j_tgc"/>

## Solution

> ### Caution:  
> This cleanup procedure deletes all service instances and bindings associated with the inaccessible cluster.

1.  To access the SAP Service Manager API, perform the following actions:
    1.  In the SAP BTP cockpit, create an SAP Service Manager service instance with the `subaccount-admin` plan and its service binding. The `service-operator-access` plan does not have the necessary access level for performing the cleanup operation. See [Creating Instances in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-instances) and [Creating Service Bindings in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-bindings-in-other-environments).
    2.  To get an access token, run the following command. Replace the placeholders with the `url`, `clientid`, and `clientsecret` from the service binding you have created.

        ```
        curl '{url}/oauth/token' -X POST \
           -H 'Accept: application/json' \
           -d 'grant_type=client_credentials&client_id={clientid}&client_secret={clientsecret}'
        ```


2.  To prepare the DELETE request, identify the following parameters:
    -   `platformID` - the ID of the Service Manager instance with the `service-operator-access` plan.
    -   `clusterID` - the ID of your cluster. To get `it`, in the SAP BTP cockpit, go to *Services* \> *Instances and Subscriptions*. In the *Instances* section, copy the cluster ID from the `Scope` column in the row that provides information about the service instance\(s\) you want to delete.

3.  Send the following request:

    ```
    curl -X DELETE '{sm_url}v1/platforms/{platformID}/clusters/{clusterID}' \
       -H 'Authorization: Bearer {ACCESS_TOKEN}'
    ```

4.  Monitor the response. You can get one of the following options:
    -   `202 Accepted` - the request is accepted for processing.
    -   `404 Resource Not Found` - platform or cluster not found.
    -   `429 Too Many Requests` - the rate limit exceeded.

5.  For the operation status, review the following headers:
    -   `Location` - the path provided to monitor the status of the operation. For more information about operations, see [Service Manager operation API](https://api.sap.com/api/APIServiceManager/resource/getSingleOperation).
    -   `Retry_After` - indicates the time in seconds after which you can retry the request after hitting rate limits.


