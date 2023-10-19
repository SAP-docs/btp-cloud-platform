<!-- loioddc2ef27293044679f8c795aba859446 -->

# How to Transport Business Roles



## Context

You can export business roles from your quality system to your productive system using customizing transports.

> ### Note:  
> -   Once you have transported a business role, no change documents will be written for this business role in the productive system. Change documents for transported business roles are only available in the quality system.
> 
> -   If you transport a derived business role, the leading business role and all other derived business roles need to be added as dependencies to the transport request as well.
> 
>     If you transport a leading business role, all derived business roles need to be added as dependencies to the transport request as well.
> 
> -   Please note that business roles that are pre-delivered by SAP \(business roles whose ID starts with SAP\*\) cannot be transported.



## Procedure

1.  In the *Business Roles* overview screen of the *Maintain Business Roles* app, select one or more business roles.

2.  Click *Add to Transport*. A list of available customizing transports appears.

    > ### Note:  
    > The default transport is always displayed as well as your own transports. If no transport exists, a confirmation dialog is shown. If you confirm, a new transport is created.

3.  Select the required transport and click *OK*. The selected business roles are then added to the transport.

4.  Open the *Export Customizing Transports* app and release your request. For more information, see [Export Customizing Transports](export-customizing-transports-a772a0f.md).

5.  Import your business role to the target system:

    1.  Open the *Manage Software Components* app.

    2.  Select *Business Configuration* in the *Type* dropdown and click *Go*.

    3.  Select the component to which the relevant configuration was exported.

    4.  In the detail view of the component, check out the change that contains your business role\(s\). For more information, see [How to Work with Branches](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/6b2f0bfc14cb47ef888f01784c92e1bf.html?version=Cloud).


    > ### Note:  
    > If you want to delete a business role that was previously transported or is currently included in an open transport request, the system offers you to add it directly to an available transport.
    > 
    > If the business role was previously transported and there is currently no transport available, a confirmation dialog is shown. If you confirm, a new transport is created.


**Related Information**  


 <?sap-ot O2O class="- topic/link " href="fa7366c3888848bd94566104ac52e627.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/ddc2ef27293044679f8c795aba859446.xml" ?> 

[Working in the Export Customizing Transports App](working-in-the-export-customizing-transports-app-cc16fd0.md "Find out how to create, release, or merge customizing requests using the Export Customizing Transports app.")

[Manage Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/3dcf76a072c9450eb46b99db947dab46.html?version=Cloud)

[How to Delete Previously Transported Business Roles](how-to-delete-previously-transported-business-roles-bd7e0f6.md "")

