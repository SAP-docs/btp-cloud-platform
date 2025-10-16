<!-- loio1ba3bffe9f1844c4a76e487a715028ac -->

# Integrating Business Role Data \(Read\)

You can use this communication scenario to read business role data.



<a name="loio1ba3bffe9f1844c4a76e487a715028ac__BusinessRoleReadIntegration_context"/>

## Context

The communication scenario SAP\_COM\_0A04 allows you to read business role data, such as business role ID or description, read business roles, read assigned business users, launchpad spaces and business catalogs, or filter for specific combinations.

**Authentication Methods**

This communication scenario can be configured with the following inbound authentication methods:

-   *Basic Authentication* \(user and password\)

-   *X.509* \(certificates\)



<a name="loio1ba3bffe9f1844c4a76e487a715028ac__BusinessRoleReadIntegration_steps"/>

## Procedure

1.  Check if a communication user already exists for this scenario. If not, create a communication user in the *Maintain Communication Users* app.

    For more information, see the *Related information* section.

2.  Check if a communication system already exists for this scenario. If not, create a communication system in the *Communication Systems* app.

3.  Check if a communication arrangement already exists for this scenario. If not, create a communication arrangement for the *Business Role Read Integration* scenario \(SAP\_COM\_0A04\) in the *Communication Arrangements* app.

    For more information, see the *Related information* section.


**Related Information**  


[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

