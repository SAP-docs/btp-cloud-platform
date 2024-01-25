<!-- loio28db6888aa9a412e9a0e3ae8485b9db0 -->

# Set Up OData Communication

To set up OData communication, use the corresponding communication management apps.



## Context

The communication management is done by the administrator in SAP Fiori launchpad.



## Procedure

1.  Create a communication system. A communication system determines which target system is called and which authentication methods are used. It also provides the user that is required to register at the target system. For more information, see [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md).

2.  In the communication system, create an outbound communication user.

3.  Create a communication arrangement. The communication arrangement is based on the communication scenario, that is created by the developer in ABAP Development Tools for Eclipse. For more information, see [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).




<a name="loio28db6888aa9a412e9a0e3ae8485b9db0__result_x3f_qpd_lzb"/>

## Results

The communication management established a connection to the system from which you want to consume the OData service. You can now perform the service call as described in [OData Communication via Communication Arrangements](odata-communication-via-communication-arrangements-418787f.md)

