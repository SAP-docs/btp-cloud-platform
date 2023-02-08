<!-- loiobbbd14283e984d6aa7b05062f197ef5b -->

# Enable RFC Communication in Your ABAP Code



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_lw4_ngm_hwb"/>

## Context

To enable RFC outbound communication in the ABAP environment, you have the following options:

-   Communication arrangement approach: By specifying a destination based on a communication arrangement. See [Communication Arrangement](communication-management-5b8ff39.md#loio201de48e2f57404e9222181b019eff14).
-   Destination service approach \(deprecated\): By using a destination that is maintained in a destination service that resides in the SAP BTP, Cloud Foundry environment \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?version=LATEST)\).



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_ssz_tgm_hwb"/>

## Service Consumption Model

You can either configure an RFC connection with a Service Consumption Model \(SRVC\) or without SRVC using the standard CALL FUNCTION ... DESTINATION statement. See [Service Consumption Model as RFC Consumer](service-consumption-model-as-rfc-consumer-a69e99c.md) for more information.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_mwm_1hm_hwb"/>

## Related Information

