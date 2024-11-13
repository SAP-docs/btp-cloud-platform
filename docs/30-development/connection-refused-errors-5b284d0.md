<!-- loio5b284d0938ea46ad8ebc2130768b4288 -->

# Connection Refused Errors



<a name="loio5b284d0938ea46ad8ebc2130768b4288__section_u5c_fnw_tcc"/>

## Symptom

You get either the ***Connection reset by peer*** response or the ***GOAWAY*** response when you attempt to establish the connection between a service without a sidecar and a service with a sidecar.



<a name="loio5b284d0938ea46ad8ebc2130768b4288__section_rzv_knw_tcc"/>

## Cause

By default, mutual TLS \(mTLS\) is enabled in the service mesh. As a result, every element of the service mesh must have an Istio sidecar with a valid TLS certificate to allow communication.



<a name="loio5b284d0938ea46ad8ebc2130768b4288__section_tqc_4nw_tcc"/>

## Solution

-   To add a service without a sidecar to the allowlist and disable mTLS traffic for it, create a `DestinationRule` resource. See [DestinationRule](https://istio.io/docs/reference/config/networking/destination-rule/).
-   To allow connections between a service without a sidecar and a service with a sidecar, create a `PeerAuthentication` resource in the *PERMISSIVE* mode. See [PeerAuthentication](https://istio.io/latest/docs/reference/config/security/peer_authentication/).

