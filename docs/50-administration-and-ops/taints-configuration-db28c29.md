<!-- loiodb28c29b313d40bcb5e4836eb34c9a75 -->

# Taints Configuration

Learn how to use taints to schedule your workloads to nodes in additional worker node pools.

The [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools) \(`additionalWorkerNodePools`\) parameter supports an optional *Taints* list. Use it to control which workloads are scheduled to nodes in a given worker pool.



## Taints Parameters

The *Taints* \(`taints`\) parameter includes three nested parameters: *Key\**, *Value*, and *Effect\**.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Taints Nested Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Key\**

btp CLI parameter: `key`

</td>
<td valign="top">

Identifies the taint.

</td>
<td valign="top">

String

</td>
</tr>
<tr>
<td valign="top">

*Value*

btp CLI parameter: `value`

</td>
<td valign="top">

Provides additional context.

</td>
<td valign="top">

String

</td>
</tr>
<tr>
<td valign="top">

*Effect\**

btp CLI parameter: `effect`

</td>
<td valign="top">

Defines what happens to workloads that do not tolerate the taint.

</td>
<td valign="top">

`NoSchedule`, `PreferNoSchedule`, `NoExecute`

</td>
</tr>
</table>

For each taint within a single worker node pool, the combination of the *key* and *effect* parameters must be unique. However, using the same *key* value with different *effect* values is allowed.



## Provisioning a Cluster with Taints

To provision a cluster with taints in an additional worker node pool, provide your values and run the following command:

```
curl --request PUT "https://$BROKER_URL/oauth/v2/service_instances/$INSTANCE_ID?accepts_incomplete=true" \
  --header 'X-Broker-API-Version: 2.14' \
  --header 'Content-Type: application/json' \
  --header "$AUTHORIZATION_HEADER" \
  --data-raw "{
    \"service_id\": \"47c9dcbf-ff30-448e-ab36-d3bad66ba281\",
    \"plan_id\": \"4deee563-e5ec-4731-b9b1-53b42d855f0c\",
    \"context\": {
      \"globalaccount_id\": \"$GLOBAL_ACCOUNT_ID\"
    },
    \"parameters\": {
      \"name\": \"$NAME\",
      \"region\": \"$REGION\",
      \"additionalWorkerNodePools\": [
        {
          \"name\": \"worker-1\",
          \"machineType\": \"Standard_D2s_v5\",
          \"haZones\": true,
          \"autoScalerMin\": 3,
          \"autoScalerMax\": 20,
          \"taints\": [
            {
              \"key\": \"dedicated\",
              \"value\": \"gpu\",
              \"effect\": \"NoSchedule\"
            },
            {
              \"key\": \"dedicated\",
              \"value\": \"gpu\",
              \"effect\": \"NoExecute\"
            }
          ]
        }
      ]
    }
  }"
```



## Updating Taints

You can't preserve existing taints without explicitly providing them in the update request.

To update or overwrite the existing taints for your worker node pool, provide a complete list of desired taints.

For example:

```
curl --request PATCH "https://$BROKER_URL/oauth/v2/service_instances/$INSTANCE_ID?accepts_incomplete=true" \
  --header 'X-Broker-API-Version: 2.14' \
  --header 'Content-Type: application/json' \
  --header "$AUTHORIZATION_HEADER" \
  --data-raw "{
    \"service_id\": \"47c9dcbf-ff30-448e-ab36-d3bad66ba281\",
    \"plan_id\": \"4deee563-e5ec-4731-b9b1-53b42d855f0c\",
    \"context\": {
      \"globalaccount_id\": \"$GLOBAL_ACCOUNT_ID\"
    },
    \"parameters\": {
      \"additionalWorkerNodePools\": [
        {
          \"name\": \"worker-1\",
          \"machineType\": \"Standard_D2s_v5\",
          \"haZones\": true,
          \"autoScalerMin\": 3,
          \"autoScalerMax\": 20,
          \"taints\": [
            {
              \"key\": \"dedicated\",
              \"value\": \"gpu\",
              \"effect\": \"NoSchedule\"
            }
          ]
        }
      ]
    }
  }"
```



## Removing Taints

To remove existing taints for a worker node pool, either omit the `taints` field in the update request or set it to an empty list \(`[]`\).

For example:

```
curl --request PATCH "https://$BROKER_URL/oauth/v2/service_instances/$INSTANCE_ID?accepts_incomplete=true" \
  --header 'X-Broker-API-Version: 2.14' \
  --header 'Content-Type: application/json' \
  --header "$AUTHORIZATION_HEADER" \
  --data-raw "{
    \"service_id\": \"47c9dcbf-ff30-448e-ab36-d3bad66ba281\",
    \"plan_id\": \"4deee563-e5ec-4731-b9b1-53b42d855f0c\",
    \"context\": {
      \"globalaccount_id\": \"$GLOBAL_ACCOUNT_ID\"
    },
    \"parameters\": {
      \"additionalWorkerNodePools\": [
        {
          \"name\": \"worker-1\",
          \"machineType\": \"Standard_D2s_v5\",
          \"haZones\": true,
          \"autoScalerMin\": 3,
          \"autoScalerMax\": 20,
          \"taints\": []
        }
      ]
    }
  }"
```

