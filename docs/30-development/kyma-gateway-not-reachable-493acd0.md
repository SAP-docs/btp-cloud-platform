<!-- loio493acd02930d4f85a8765cdb5fe631ec -->

# Kyma Gateway Not Reachable



<a name="loio493acd02930d4f85a8765cdb5fe631ec__section_o5t_vx5_52c"/>

## Symptom

You cannot access Services or Functions exposed using APIRules. Kyma Gateway refuses the connection.



<a name="loio493acd02930d4f85a8765cdb5fe631ec__section_o13_wx5_52c"/>

## Cause

The issue occurs when the default `kyma-gateway` is either renamed or duplicated. Once you have multiple Gateway resources pointing to the same host, the Gateway CR created first takes precedence over the others.



<a name="loio493acd02930d4f85a8765cdb5fe631ec__section_xy3_wx5_52c"/>

## Solution

Having two Gateway resources pointing to the same host is not recommended. To resolve the issue, make sure the default `kyma-gateway` exists and is not renamed or duplicated. If there are multiple Gateway resources pointing to the same host, delete the duplicated Gateway. To delete the Gateway resource, run: `kubectl -n kyma-system delete gateway {DUPLICATED_GATEWAY_NAME}`.

