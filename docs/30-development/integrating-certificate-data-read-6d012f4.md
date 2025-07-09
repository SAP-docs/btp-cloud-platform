<!-- loio6d012f4fe6af4440ab530e7bce06ed7c -->

# Integrating Certificate Data \(Read\)



<a name="loio6d012f4fe6af4440ab530e7bce06ed7c__CertificateData_context"/>

## Context

You can use this communication scenario to read certificate data.

The communication scenario SAP\_COM\_0A13 allows you to read certificate data, such as client certificates and certificate trust lists.

**Authentication Methods**

This communication scenario can be configured with the following inbound authentication methods:

-   *Basic Authentication* \(user and password\)

-   *X.509* \(certificates\)



<a name="loio6d012f4fe6af4440ab530e7bce06ed7c__CertificateData_steps"/>

## Procedure

1.  Check if a communication user already exists for this scenario. If not, create a communication user in the *Maintain Communication Users* app.

    For more information, see the *Related Information* section.

2.  Check if a communication system already exists for this scenario. If not, create a communication system in the *Communication Systems* app.

3.  Check if a communication arrangement already exists for this scenario. If not, create a communication arrangement for the *Certificate Read Integration* scenario \(SAP\_COM\_0A13\) in the *Communication Arrangements* app.

    For more information, see the *Related Information* section.


**Related Information**  


[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

