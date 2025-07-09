<!-- loiobbbd14283e984d6aa7b05062f197ef5b -->

# Enable RFC Communication in Your ABAP Code



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_gfh_hcd_gzb"/>

## Overview

The RFC client allows to connect to RFC-enabled function modules in remote systems.

> ### Note:  
> Only synchronous RFC calls are supported.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_rrz_3cd_gzb"/>

## Feature Scope

There are two development approaches to provide configuration for RFC communication. Each development approach has different setup options:

-   Communication arrangement
    -   Provides APIs for receiver determination based on arbitrary properties \(see [Define Specific Properties for Communication Scenarios](define-specific-properties-for-communication-scenarios-fae8f0f.md)\).
    -   Local configuration via communication management UIs or central configuration in SAP BTP cockpit via SAP BTP destination service reference in the communication system \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?locale=en-US&state=PRODUCTION&version=LATEST)\). For more information, see [Create RFC Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-rfc-destinations?locale=en-US&version=Cloud) and [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md).
    -   Requires the development of communication scenario artifacts.

-   Destination service \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?locale=en-US&state=PRODUCTION&version=LATEST)\).
    -   Provides APIs to fetch connection information for a given destination name from the SAP BTP destination service.No additional development artifacts required.
    -   Central configuration in SAP BTP cockpit.


> ### Note:  
> When using on-premise connectivity, make sure the called RFC function module is exposed in Cloud Connector.

We recommend using the communication arrangement approach for the following reasons:

-   There are no hardcoded values/assumptions for a destination name in the destination service or destination service integration \(for example, only default integration\).
-   The communication system can also refer to a destination service. The destination name and destination service instance are then configured instead of hardcoded.

> ### Note:  
> The communication arrangement approach requires an existing communication scenario and outbound service. See [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md) and [RFC Communication via Communication Arrangements](rfc-communication-via-communication-arrangements-fadc4a2.md) for more information.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_hsm_sdd_gzb"/>

## Service Consumption Model

Other than with OData, SOAP, or HTTP communication, you can either configure an RFC connection with a Service Consumption Model \(SRVC\) or without SRVC using the standard `CALL FUNCTION ... DESTINATION` statement. For more information, see [Service Consumption Model as RFC Consumer](service-consumption-model-as-rfc-consumer-a69e99c.md).

