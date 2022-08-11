<!-- loiob4eaa0a21db044248d684019cbe9cc5f -->

# Set Up RFC Communication



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_kl2_c3z_qsb"/>

## Overview

The RFC client allows to connect to RFC-enabled function modules in remote systems.

> ### Note:  
> Only synchronous RFC calls are supported.



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_fpg_23z_qsb"/>

## Feature Scope

There are two development approaches to provide configuration for RFC communication. Each development approach has different setup options:

-   Communication arrangement
    -   Provides APIs for receiver determination based on arbitrary properties \(see [Define Specific Properties for Communication Scenarios](define-specific-properties-for-communication-scenarios-fae8f0f.md)\).
    -   Local configuration via communication management UIs or central configuration in SAP BTP cockpit via SAP BTP destination service reference in the communication system \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\). See [Create RFC Destinations](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/9b3cc683cca944bd98346bef3181630e.html) and [How to Create Communication Systems](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/c2234acd55774ebcbedb66744199273e.html) for more information.
    -   Requires development of communication scenario artifacts.

-   Destination service \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\).
    -   Provides APIs to fetch connection information for a given destination name from the SAP BTP destination service.
    -   No additional development artifacts required.
    -   Central configuration in SAP BTP cockpit.


We recommend using the communication arrangement approach for the following reasons:

-   There are no hardcoded values/assumptions for a destination name in the destination service or destination service integration \(for example, only default integration\).
-   The communication system can also refer to a destination service. The destination name and destination service instance are then configured instead of hardcoded.

> ### Note:  
> The communication arrangement approach requires an existing communication scenario and outbound service. See [Communication Arrangement](communication-arrangement-201de48.md) and [RFC Communication via Communication Arrangements](rfc-communication-via-communication-arrangements-fadc4a2.md) for more information.



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_aqf_sjz_qsb"/>

## Service Consumption Model

Other than with OData, SOAP, or HTTP communication, you can either configure an RFC connection with a Service Consumption Model \(SRVC\) or without SRVC using the standard `CALL FUNCTION ... DESTINATION` statement. See [Service Consumption Model as RFC Consumer](service-consumption-model-as-rfc-consumer-a69e99c.md) for more information.



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_pfv_vjz_qsb"/>

## Comparison Between On-Premise and Cloud

There are no `SM59`-managed destinations \(destinations created via SAP transaction `SM59`\) available in the ABAP environment. The decoupling of code and configuration is done via generic RFC destinations. You can create these destinations by using connection information provided in one of the described ways.

> ### Note:  
> When using on-premise connectivity, make sure the called RFC function module is exposed in Cloud Connector.



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_qzt_hkz_qsb"/>

## Fast Serialization

If you've configured on-premise connectivity \(via Cloud Connector\) in the RFC settings of your communication system or destination service, use fast serialization. See SAP Note [2418683](https://launchpad.support.sap.com/#/notes/2418683) for more information. For example, if you use an SCM, data and structures containing includes can be transferred incorrectly because of displaced offsets.

**Related Information**  


[Enable RFC Communication in Your ABAP Code](enable-rfc-communication-in-your-abap-code-bbbd142.md)

