<!-- loiob4eaa0a21db044248d684019cbe9cc5f -->

# Set Up RFC Communication

To set up RFC communication, use the corresponding communication management apps.



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_x5k_w3w_kzb"/>

## Context

The communication management is done by the administrator in SAP Fiori launchpad.

> ### Note:  
> If you've configured on-premise connectivity \(via Cloud Connector\) in the RFC settings of your communication system or destination service, use fast serialization. See SAP Note [2418683](https://me.sap.com/notes/2418683) for more information. For example, if you use a Service Consumption Model, data and structures containing includes can be transferred incorrectly because of displaced offsets. Fast serialization is set by default.



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_agt_w3w_kzb"/>

## Procedure

1.  Create a communication system. A communication system determines which target system is called and which authentication methods are used. It also provides the user that is required to register at the target system. For more information, see [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md).
2.  In the communication system, create an outbound communication user.
3.  Create a communication arrangement. The communication arrangement is based on the communication scenario, that is created by the developer in ABAP Development Tools for Eclipse. For more information, see [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).



<a name="loiob4eaa0a21db044248d684019cbe9cc5f__section_p11_x3w_kzb"/>

## Result

The communication management established a connection to the system from which you want to consume the RFC service. You can now perform the service call as described in [RFC Communication via Communication Arrangements](rfc-communication-via-communication-arrangements-fadc4a2.md).

