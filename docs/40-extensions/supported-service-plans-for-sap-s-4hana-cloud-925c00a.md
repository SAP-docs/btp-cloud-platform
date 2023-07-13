<!-- loio925c00ab99d849edb744e33001c0b2cf -->

# Supported Service Plans for SAP S/4HANA Cloud

The following service plans are available for subaccounts in SAP BTP paired with an SAP S4/HANA Cloud tenant.



<a name="loio925c00ab99d849edb744e33001c0b2cf__section_gcr_qsb_t3b"/>

## api-access

This service plan enables all communication scenarios, both predefined and custom, which allow you to consume SAP S/4HANA Cloud APIs and integrate your extension applications with the respective SAP S/4HANA Cloud functionality.

-   To access the specific documentation of these APIs, see [SAP S/4HANA Cloud APIs at SAP Business Accelerator Hub](https://api.sap.com/package/SAPS4HANACloud?section=Artifacts).

-   For more information about SAP S/4HANA Cloud communication scenarios see:

    -   [Communication Management](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/2e84a10c430645a88bdbfaaa23ac9ff7.html?q=Create%20Custom%20Communication%20Scenario)

    -   [Custom Communication Scenarios](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/41b6543c04864dc298123c3ef5efd7a3.html?q=communication%20scenario)



> ### Note:  
> These service plans have been deprecated:
> 
> -   *sap\_com\_0109*
> 
> -   *sap\_com\_0009*
> 
> -   *sap\_com\_0008*
> 
> 
> However, you can still enable these communication scenarios using the *api-access* service plan:
> 
> -   *Sales Order Integration \(SAP\_COM\_0109\)*: allows you to integrate your extension applications with sales order processing in SAP S/4HANA Cloud. For more information, see [https://api.sap.com/api/API\_SALES\_ORDER\_SRV/overview](https://api.sap.com/api/API_SALES_ORDER_SRV/overview).
> 
> -   *Product Integration \(SAP\_COM\_0009\)*: enables you to replicate product master data from client system to SAP S/4HANA system. For more information, see [https://api.sap.com/api/PRODUCTMDMBULKREPLICATEREQUEST/overview](https://api.sap.com/api/PRODUCTMDMBULKREPLICATEREQUEST/overview).
> 
> -   *Business Partner, Customer and Supplier Integration \(SAP\_COM\_0008\)*: allows you to consume the Business Partner API which enables you to create, read, update, and delete master data related to Business Partners, Suppliers, and Customers in an SAP S/4HANA system. For more information, see [https://api.sap.com/api/API\_BUSINESS\_PARTNER/overview](https://api.sap.com/api/API_BUSINESS_PARTNER/overview).
> 
> 
> For a sample JSON for these communication scenarios, see [Communication Arrangement JSON/YAML File - Properties](communication-arrangement-json-yaml-file-properties-553a4c6.md).



<a name="loio925c00ab99d849edb744e33001c0b2cf__section_x5z_wdz_khb"/>

## messaging

This service plan enables the *Enterprise Eventing Integration \(SAP\_COM\_0092\)* communication scenario which allows you to consume SAP S/4HANA Cloud events and create event-based extensions.

> ### Note:  
> This service plan has been renamed from *sap\_com\_0092*.

