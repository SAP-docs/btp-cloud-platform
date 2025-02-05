<!-- loio9f76a684aaac4bddbe0da4f9c682df14 -->

# Integrating Communication Management Data \(Read and Write\)

You can use this communication scenario to read and write communication arrangement, communication system and communication user data.



<a name="loio9f76a684aaac4bddbe0da4f9c682df14__Communication_Arrangement_Integration_ReadWrite_context"/>

## Context

This communication scenario allows you to read and write communication arrangements, communication systems and communication users.

**Authentication Methods**

This communication scenario can be configured with the following inbound authentication methods:

-   *Basic Authentication* \(user and password\)

-   *X.509* \(certificates\)



<a name="loio9f76a684aaac4bddbe0da4f9c682df14__Communication_Arrangement_Integration_ReadWrite_steps"/>

## Procedure

1.  Check if a communication user already exists for this scenario. If not, create a communication user in the *Maintain Communication Users* app.

    For more information, see the *Related information* section.

2.  Check if a communication system already exists for this scenario. If not, create a communication system in the *Communication Systems* app.

3.  Check if a communication arrangement already exists for this scenario. If not, create a communication arrangement for the *Communication Management Integration* scenario \(SAP\_COM\_0A48\) in the *Communication Arrangements* app.

    For more information, see the *Related information* section.


**Related Information**  


[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

