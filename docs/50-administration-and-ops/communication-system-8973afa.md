<!-- copy8973afa24520400f945acf8612b10aa5 -->

# Communication System

A communication system is a specification of a system that represents a communication partner and the technical information required for the communication \(inbound/outbound\), such as the host name/IP address, user information \(inbound/outbound\), certificates, etc.

Instead of storing user information by using outbound communication users, in some cases, credentials are stored in a destination in the subaccount of the ABAP system. This destination can then be referenced in the communication system. A Cloud Connector in the subaccount of the system can be referenced in the communication system as well via the location ID of the Cloud Connector.

For outbound and inbound communication, you have to maintain the technical information in the communication system. You can use the maintained properties of the destination from your communication system by using the destination service communication scenario \(`SAP_COM_0267`\). See [Create a Destination](../30-development/create-a-destination-3fa7934.md).

The administrator of the ABAP environment creates the communication system in the SAP Fiori launchpad. Note that it is not transported between systems but created locally. If there are multiple systems, the communication partners can vary for each system. To maintain a communication system, business catalog `SAP_CORE_BC_COM` needs to be assigned to the corresponding user.

**Related Information**  


[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[How to Create Communication Systems](how-to-create-communication-systems-c2234ac.md "")

[Business Catalogs and Business Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/da320654ed6e4e1e804a1a882cd461ea.html)

