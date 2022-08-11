<!-- loio3cd5085104bf406290b711db328fe3ed -->

# How to Monitor Asynchronous SOAP Calls

Learn how to use the Message Monitor Overview App to monitor asynchronous SOAP calls.



<a name="loio3cd5085104bf406290b711db328fe3ed__prereq_ey2_h25_h5b"/>

## Prerequisites

-   Roles based on the following business catalogs are assigned to your user in Fiori Launchpad:

    -   `SAP_CA_BC_COM_ERR_PC`
    -   `SAP_CA_BC_COM_CONF_PC`

    See [Maintain Business Roles](../50-administration-and-ops/maintain-business-roles-8980ad0.md) and [Business Catalogs](../50-administration-and-ops/business-catalogs-dd0abf5.md) for more information.

-   The user is a recipient of the `/SPRX` namespace. You can manage this in the Assign Recipients to Users app. See [Assign Recipients to Users](../50-administration-and-ops/assign-recipients-to-users-576fa8d.md) for more information.




## Context

When calling asynchronous SOAP services as described in [SOAP Communication via Communication Arrangements](soap-communication-via-communication-arrangements-2133e15.md), you can check if the call has been sent to the receiver using the Message Monitor Overview app. See [Message Monitoring Overview](../50-administration-and-ops/message-monitoring-overview-503c823.md) for more information.



## Procedure

1.  Create a Service Consumption Model \(SRVC\) of type `Web Service` as described in .

2.  Activate the SRVC. This creates a so-called AIF interface in the Message Monitor Overview app.

    > ### Note:  
    > For every operation in your Web service, a new AIF interface is generated.

3.  Open the Message Monitoring Overview app.

4.  Select the relevant AIF interface.




<a name="loio3cd5085104bf406290b711db328fe3ed__result_k4h_yww_35b"/>

## Results

You've created an AIF interface for each operation in your asynchronous Web service. When you call an operation, you can monitor it in the Message Monitor Overview app.

**Related Information**  


[Set Up SOAP Communication](set-up-soap-communication-8b6723b.md "Developers can consume SOAP-based Web services for outbound communication from the ABAP environment.")

