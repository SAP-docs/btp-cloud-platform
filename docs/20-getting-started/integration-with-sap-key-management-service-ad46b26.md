<!-- loioad46b2654c404b5da75daffe7bff7e1a -->

# Integration with SAP Key Management Service

SAP BTP ABAP environment provides an optional integration of an ABAP environment instance and its SAP HANA Cloud database with the SAP Key Management Service \(KMS\).

The integration with SAP KMS is established on the level of the SAP BTP subaccount where the ABAP environment instance is created. Once this integration is enabled, the encryption keys of the SAP HANA Cloud database are manageable via SAP KMS. Key activities will affect the SAP HANA Cloud database and the ABAP environment instance.

For more information on SAP KMS, see [SAP Key Management Service](https://help.sap.com/docs/SAP_Key_Management_Service/b553377444b348789f63437ed18cb789/fe3d07c535414dbf90bc69f324a5f35e.html).

> ### Caution:  
> Once the integration is enabled, it can't be disabled anymore.
> 
> If access to the encryption keys is revoked, the linked ABAP environment instances and their SAP HANA Cloud databases will be stopped and the instances are no longer accessible. An ABAP environment instance can remain in this state for up to seven days only. Grant access to the encryption keys in SAP KMS again to bring the instances back online. Open a service request to restart the instances on component `BC-CP-ABA` within seven days after the revocation of key access. There is no automatic restart once access to the keys is given again. If no restart was requested via a service request within seven days after the revocation of key access, the affected ABAP environment instances and their SAP HANA Cloud databases are no longer supported. The only supported operation at this time will be the deletion of the instances, which can be done using SAP BTP Cockpit, for example.

> ### Restriction:  
> The *Customer-Managed Keys* parameter is available in the **standard** and **build-runtime** service plans only. It's not available in the **free** and **saas-oem** service plans.
> 
> The new procedures for a reduced technical downtime of release upgrades and the import of hotfix collections will not be applied to an ABAP environment instance which is integrated with SAP KMS.

