<!-- loio3884bc38209843ac900d92adb9c2a863 -->

# Set Up HTTP Communication

To set up HTTP communication, use the corresponding communication management apps.



<a name="loio3884bc38209843ac900d92adb9c2a863__section_hpd_zmc_gzb"/>

## Context

The communication management is done by the administrator in SAP Fiori launchpad.



<a name="loio3884bc38209843ac900d92adb9c2a863__section_tpq_zmc_gzb"/>

## Procedure

1.  Create a communication system. A communication system determines which target system is called and which authentication methods are used. It also provides the user that is required to register at the target system. For more information, see [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md).
2.  In the communication system, create an outbound communication user.
3.  Create a communication arrangement. The communication arrangement is based on the communication scenario, that is created by the developer in ABAP Development Tools for Eclipse. For more information, see [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).



<a name="loio3884bc38209843ac900d92adb9c2a863__section_hbz_mnc_gzb"/>

## Result

The communication management established a connection to the system from which you want to consume the HTTP service. You can now perform the service call as described in [HTTP Communication via Communication Arrangements](http-communication-via-communication-arrangements-3047582.md).

