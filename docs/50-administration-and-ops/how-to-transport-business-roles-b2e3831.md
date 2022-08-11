<!-- copyb2e38319a2534cd485cd33404c61a8d5 -->

# How to Transport Business Roles



## Context

You can export business roles from your quality system to your productive system using customizing transports.

> ### Note:  
> -   Once you have transported a business role, no change documents will be written for this business role in the productive system. Change documents for transported business roles are only available in the quality system.
> 
> -   If you transport a derived business role, the leading business role and all other derived business roles need to be added as dependencies to the transport request as well.
> 
>     If you transport a leading business role, all derived business roles need to be added as dependencies to the transport request as well.



## Procedure

1.  In the *Business Roles* overview screen of the *Maintain Business Roles* app, select one or more business roles.

2.  Click *Add to Transport*. Your business role is added to the active customizing transport. If there is no active transport, the system automatically creates one and adds your role to it.

3.  Open the *Export Customizing Transports* app and release your request. For more information, see [Working in the Export Customizing Transports App](working-in-the-export-customizing-transports-app-cc16fd0.md).

4.  Import your business role to the target system:

    1.  Open the *Manage Software Components* app.

    2.  Select *Business Configuration* in the *Type* dropdown and click *Go*.

    3.  Select the component to which the relevant configuration was exported.

    4.  In the detail view of the component, check out the change that contains your business role\(s\). For more information, see [How to Work with Branches](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/6b2f0bfc14cb47ef888f01784c92e1bf.html?version=Cloud).



**Related Information**  




[Working in the Export Customizing Transports App](working-in-the-export-customizing-transports-app-cc16fd0.md "Find out how to create, release, or merge customizing requests using the Export Customizing Transports app.")

[Manage Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/3dcf76a072c9450eb46b99db947dab46.html?version=Cloud)

