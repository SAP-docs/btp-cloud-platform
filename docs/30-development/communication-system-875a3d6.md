<!-- loio875a3d6b20cb4934bcfea815e28afaa1 -->

# Communication System

A communication system is a specification of a system that represents a communication partner and the technical information required for the communication \(inbound/outbound\), such as the host name/IP address, user information \(inbound/outbound\), certificates, etc.

For outbound communication, you can either maintain the technical information in the communication system or in a destination. For inbound communication, you have to maintain this information in the communication system. You can use the maintained properties of the destination from your communication system by using the destination service communication scenario \(`SAP_COM_0267`\). See [Create a Destination](create-a-destination-3fa7934.md) and [Destination Service](destination-service-eeb0ec2.md).

The administrator of the ABAP environment creates the communication system in the SAP Fiori launchpad. Note that it is not transported between systems but created locally. If there are multiple systems, the communication partners can vary for each system. To maintain a communication system, business catalog `SAP_CORE_BC_COM` needs to be assigned to the corresponding user.

**Related Information**  


[Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[How to Create Communication Systems](../50-administration-and-ops/how-to-create-communication-systems-c2234ac.md "")

[Consuming the Destination Service](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html)

[Destination Service](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/daca64dacc6148fcb5c70ed86082ef91.html#loiodaca64dacc6148fcb5c70ed86082ef91__services)

[Business Catalogs and Business Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/da320654ed6e4e1e804a1a882cd461ea.html)

