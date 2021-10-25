<!-- loio7daed6d1dcfa4daba09cfb40fbab0b3b -->

# Propagate User Information Between Applications or Services

When a business application communicates with a service, you must decide whether you want to propagate the identity of the user that called the business application, or if a call from machine-to-machine is sufficient.



<a name="loio7daed6d1dcfa4daba09cfb40fbab0b3b__section_jxr_wqw_42b"/>

## Principal Propagation Versus Technical Communication

If the business application triggers an action of the service that should be auditable or requires that the identity of the user be known, use principal propagation. Principal propagation enables the identity of the user to be propagated from the business application to the service.

If the business application triggers an action of the service for which the identity of the user is unimportant, such as a regular clean-up task or the checking of a queue, then you can use technical communication. In technical communication, the service performs the action for the business application without knowing the identity of the user.



<a name="loio7daed6d1dcfa4daba09cfb40fbab0b3b__section_qpl_5fb_x4b"/>

## Cross-Application API Calls from an External System to Applications in the Cloud Foundry Environment

If applications from an external system must make API calls to applications running in the Cloud Foundry environment, administrators must make sure that these applications can communicate with the relevant applications in the external system. In this case, the bearer assertion flow or client credentials identify the external application at the UAA, which can then issue a JSON web token. The external application can use this JSON web token when it makes the API calls to applications in the Cloud Foundry environment.

No browser is involved here. Users are propagated in the following ways:

-   Using technical communication, for example, propagating scopes and authorities.

-   Using a bearer assertion or client credentials \(JSON web tokens\) to propagate named users.


**Related Information**  


[Principal Propagation with Tightly Coupled Developments](PP_closely_coupled.md "A scenario is tightly coupled when a business application calls a service within the same subaccount in the Cloud Foundry environment. The business application calls the service with principal propagation, meaning information about the current user is carried over with the service call.")

[Technical Communication with Tightly Coupled Developments](tech_comm_same_subacct.md "When a business application and a service are developed for the same subaccount, the two developments are tightly coupled together. The service is designed to be used with this particular application.")

[Principal Propagation](../60-security/Principal_Propagation_f70fcf1.md "Exchange user ID information between systems or environments in SAP BTP.")

