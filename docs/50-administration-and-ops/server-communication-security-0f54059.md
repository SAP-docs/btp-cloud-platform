<!-- loio0f540598ff954f8caecdc31546d7f4f7 -->

# Server Communication Security

In integration scenarios, the SAP BTP ABAP environment backend exchanges data with other systems. These systems may be SAP or third-party systems in the cloud or on-premise.

To secure these system-system communication channels, authentication based on certificates can be used.

We distinguish between outbound and inbound integrations.



<a name="loio0f540598ff954f8caecdc31546d7f4f7__section_f21_j21_fbc"/>

## Outbound Integrations

In outbound integrations, the SAP BTP ABAP environment calls an external system. To establish the connection, the external system must present a trusted \(server\) certificate.

The SAP BTP ABAP environment may in turn authenticate towards the external system by presenting a client certificate that the external system trusts. Depending on the capabilities and configuration of the external system, other authentication methods like OAuth or user/password are possible.



<a name="loio0f540598ff954f8caecdc31546d7f4f7__section_t2c_m21_fbc"/>

## Inbound Integrations

In inbound integrations, an external system calls the SAP BTP ABAP environment backend system. The authentication method is specified as part of the communication arrangement. In case of certificate-based authentication, the external system must present a specific certificate that is maintained in the communication arrangement and signed by an approved CA.

