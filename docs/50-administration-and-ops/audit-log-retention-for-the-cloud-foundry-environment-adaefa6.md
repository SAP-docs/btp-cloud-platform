<!-- loioadaefa64228e49ddbe40c15f63a4f74b -->

# Audit Log Retention for the Cloud Foundry Environment

The audit log data is stored on a subaccount level. The access to the stored audit log data is strictly restricted - only authorized stakeholders can preview, retrieve, and download their audit log data.

For more information, see [Audit Log Retrieval API Usage for the Cloud Foundry Environment](audit-log-retrieval-api-usage-for-the-cloud-foundry-environment-30ece35.md).



<a name="loioadaefa64228e49ddbe40c15f63a4f74b__section_b3s_khk_dzb"/>

## Retention of Audit Data written from SAP BTP Applications and Services



### Free retention period

The securely stored audit log data for your account, which is written from SAP BTP Applications and Services, is retained for 90 days for free, after which it's deleted. Within this free default retention period, the authorized stakeholders can retrieve the audit data to store it in their own persistent storage.



### Configurable retention period

To be in compliance with the Industry and Business Regulations requirements for a longer retention and storage, you can enable the Audit Log service, premium edition service plan, and be able to configure a flexible retention period, longer than the free 90 days.

When you enable the Audit Log service, premium edition service plan, you can create a support ticket with component BC-CP-CF-SEC-AUDITLG to the Audit Log service to configure a flexible retention period for storing your audit data. The premium edition with its advanced functionalities is a commercialized consumption based service plan, which prices per GB you can check at [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/audit-log-service?region=all&tab=service_plan&commercialModel=cpea).



<a name="loioadaefa64228e49ddbe40c15f63a4f74b__section_nf1_jlk_dzb"/>

## Retention of Audit Data written from Customer BTP Applications

There is no free retention period for any audit data written from customer applications that are built on top of the BTP. When you enable the Audit Log service, premium edition service plan, you can create a support ticket with component BC-CP-CF-SEC-AUDITLG to the Audit Log service to configure a flexible retention period for storing your audit data. The premium edition with its advanced functionalities is a commercialized consumption based service plan, which prices per GB you can check at [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/audit-log-service?region=all&tab=service_plan&commercialModel=cpea).

