<!-- loiof871712b816943b0ab5e04b60799e518 -->

# Developing External Service Consumption \(Outbound Communication\)

Get more information about consuming external services.

In the ABAP Environment, the following three options are available to consume services from the internet or to enable integration between the ABAP environment and your on-premise systems:

1.  Refer to a communication arrangement, such as `CL_HTTP_DESTINATION_PROVIDER=>create_by_comm_arrangement`

2.  Refer to a destination in the destination service, such as `CL_HTTP_DESTINATION_PROVIDER =>create_by_cloud_destination`

3.  Directly specify the URL of the respective service, such as `CL_HTTP_DESTINATION_PROVIDER=>create_by_url`


**Create\_by\_comm\_arrangement**

To use a communication arrangement for outbound communication, the following two additional development objects need to be created:

-   Communication scenario

-   Outbound communication service


Usage of communication arrangements is generally recommended for new developments. When setting up a new communication arrangement as an administrator, the following options are available to grant full flexibility:

-   Refer to a destination in a destination service

-   Use an outbound communication user \(restricted to authentication methods without user propagation\)


To enable simple receiver determination, you as a developer can allow multiple instances of communication arrangements of the same communication scenario. By using CL\_COM\_ARRANGEMENT\_FACTORY, you can evaluate the customer-specific properties of a communication arrangement to decide at runtime, which communication system should be chosen for outbound communication.

**Create\_by\_cloud\_destination**

This is a quick way of developing integrations in the ABAP environment without developing additional development objects. During development, the name of the destination and optionally the name of the destination service instance has to be specified explicitly. If no destination service instance is maintained, the destinations of the Cloud Foundry subaccount are used by default.

Only relevant for HTTP connections: if an authentication method without user propagation should be used in the destination service, the `authn_mode` needs to be specified explicitly as ***service\_specific***.

Note however that supportability and flexibility are impacted, since the administrator needs to set up a specific destination name \(or even a specific destination service instance name\).

**Create\_by\_url \(available for HTTP + SOAP\)**

This option should only be used to access public services to avoid storing credentials in unsafe places. Credentials should either be stored in the destination service or in the communication arrangement framework.

**Related Information**  


[Service Consumption via Communication Arrangements](service-consumption-via-communication-arrangements-86aece6.md "")

