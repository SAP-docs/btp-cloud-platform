<!-- loiocef1ada754154d11b5701ab60e6ab412 -->

# Enable HTTP Communication in Your ABAP Code

The HTTP client allows to connect to HTTP endpoints.



<a name="loiocef1ada754154d11b5701ab60e6ab412__section_u14_kjc_gzb"/>

## Feature Scope

-   Communication arrangement
    -   Provides APIs for receiver determination based on arbitrary properties \(see [Define Specific Properties for Communication Scenarios](define-specific-properties-for-communication-scenarios-fae8f0f.md).
    -   Local configuration via communication management UIs or central configuration in SAP BTP cockpit via SAP BTP destination service reference in the communication system \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/PRODUCT_ID/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?state=PRODUCTION&version=latest&locale=en-US)\). See [Create HTTP Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-http-destinations?version=Cloud) and [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md).
    -   Requires development of communication scenario artifacts.

-   Destination service \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/PRODUCT_ID/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?state=PRODUCTION&version=latest&locale=en-US)\).
    -   Provides APIs to fetch connection information for a given destination name from the SAP BTP destination service.
    -   No additional development artifacts required.
    -   Central configuration in SAP BTP cockpit.
    -   Comparable to `create_by_destination` in on-premise ABAP.

-   Static configuration in code \(only recommended for public services and test purposes\).

We recommend using the communication arrangement approach for the following reasons:

-   There are no hardcoded values/assumptions for a destination name in the destination service or destination service integration \(for example, only default integration\).
-   The communication system can also refer to a destination service. The destination name and destination service instance are then configured instead of hardcoded.

> ### Note:  
> When using on-premise connectivity, make sure the called ICF service is exposed in Cloud Connector.

