<!-- loio664ea90a398d4cc091cc8c878a7ae1cc -->

# Integrating Communication User Data \(Read\)

You can use this communication scenario to read communication user data.



<a name="loio664ea90a398d4cc091cc8c878a7ae1cc__Communication_User_Integration_context"/>

## Context

This communication scenario allows you to read communication user data, such as read communication users, read assigned certificates, communication systems and communication arrangements.

**Authentication Methods**

This communication scenario can be configured with the following inbound authentication methods:

-   *Basic Authentication* \(user and password\)

-   *X.509* \(certificates\)



<a name="loio664ea90a398d4cc091cc8c878a7ae1cc__Communication_User_Integration_steps"/>

## Procedure

1.  Check if a communication user already exists for this scenario. If not, create a communication user in the *Maintain Communication Users* app.

    For more information, see the *Related information* section.

2.  Check if a communication system already exists for this scenario. If not, create a communication system in the *Communication Systems* app.

3.  Check if a communication arrangement already exists for this scenario. If not, create a communication arrangement for the *Communication User Read Integration* scenario \(SAP\_COM\_0A05\) in the *Communication Arrangements* app.

    For more information, see the *Related information* section.


**Related Information**  


[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

