<!-- loio3884bc38209843ac900d92adb9c2a863 -->

# Set Up HTTP Communication

The HTTP client allows to connect to HTTP endpoints.



<a name="loio3884bc38209843ac900d92adb9c2a863__section_acy_wlx_qsb"/>

## Feature Scope

There are three different development approaches to provide configuration for HTTP communication. Each development approach has different setup options:

-   Communication arrangement

    -   Provides APIs for receiver determination based on arbitrary properties \(see [Define Specific Properties for Communication Scenarios](define-specific-properties-for-communication-scenarios-fae8f0f.md)\).

    -   Local configuration via communication management UIs or central configuration in SAP BTP cockpit via SAP BTP destination service reference in the communication system \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\).
    -   Requires development of communication scenario artifacts.

-   Destination service \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\).
    -   Provides APIs to fetch connection information for a given destination name from the SAP BTP destination service.

    -   No additional development artifacts required.
    -   Central configuration in SAP BTP cockpit.
    -   Comparable to `create_by_destination` in on-premise ABAP.

-   Static configuration in code \(only recommended for public services and test purposes\).

We recommend using the communication arrangement approach for the following reasons:

-   There are no hardcoded values/assumptions for a destination name in the destination service or destination service integration \(for example, only default integration\).

-   The communication system can also refer to a destination service. The destination name and destination service instance are then configured instead of hardcoded.

> ### Note:  
> The communication arrangement approach requires an existing communication scenario and outbound service. See [Communication Arrangement](communication-arrangement-201de48.md) and [HTTP Communication via Communication Arrangements](http-communication-via-communication-arrangements-3047582.md) for more information.



<a name="loio3884bc38209843ac900d92adb9c2a863__section_k1x_bnx_qsb"/>

## Comparison Between On-Premise and Cloud

There are no `SM59`-managed destinations \(destinations created via SAP transaction `SM59`\) available in the ABAP environment. The decoupling of code and configuration is done via generic HTTP destinations. You can create these destinations by using connection information provided in one of the three described ways.

> ### Note:  
> When using on-premise connectivity, make sure the called ICF service is exposed in Cloud Connector.

**Related Information**  


[Enable HTTP Communication in Your ABAP Code](enable-http-communication-in-your-abap-code-cef1ada.md "")

