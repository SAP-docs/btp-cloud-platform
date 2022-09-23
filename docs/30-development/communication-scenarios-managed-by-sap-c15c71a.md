<!-- loioc15c71affb2243ec9abc071c1a62503c -->

# Communication Scenarios Managed by SAP

SAP provides ready-to-use communication scenarios. These scenarios can contain inbound and outbound services.

See [Overview of Communication Scenarios Managed by SAP](../50-administration-and-ops/overview-of-communication-scenarios-managed-by-sap-2d16f49.md).

To use a communication scenario provided by SAP, an administrator has to create a communication user, communication system, and communication arrangement for a communication partner.

There are also scenarios for integrating SAP BTP services where the arrangement can be created from a serivce key of a service instance. In that case, the communication system and user are automatically created from the service key. See [Create a Communication Arrangement for Inbound Communication with Service Key Type Basic](create-a-communication-arrangement-for-inbound-communication-with-service-key-type-basic-1cc5a1d.md).

When maintaining a communication system, you can:

-   Create a destination in the SAP BTP cockpit to maintain the host and port of the communication partner, and assign the destination to the communication system.

-   Maintain the host and port of the communication partner in the communication system if you do not use the destination service or


The credentials of the communication partners can be maintained as follows:

-   In your communication system

    This is the recommended approach to provide the credentials.

-   In a destination in your subaccount

    To maintain the credentials via a destination in your subaccount, the destination name needs to be provided in the communication system.

-   Within a destination service instance

    To maintain the credentials via a destination service instance, a communication arrangement for scenario `SAP_COM_0276` needs to be maintained to enable communication with the destination service instance. See [Create a Destination](create-a-destination-3fa7934.md). In this case, the destination name and the service instance name need to be maintained in the communication system.


![](images/In_Outbound_Communication_Managed_by_SAP_e3bc26e.png)

**Related Information**  


[Overview of Communication Scenarios Managed by SAP](../50-administration-and-ops/overview-of-communication-scenarios-managed-by-sap-2d16f49.md "Find a quick overview of all the communication scenarios in the ABAP environment.")

