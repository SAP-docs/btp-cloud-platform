<!-- loio5fbbd8cdafdd48679512842f3062f66c -->

# How to Transport Business User Groups



## Context

You can export business user groups from your quality system to your productive system using customizing transports.



<a name="loio5fbbd8cdafdd48679512842f3062f66c__steps_r4c_llt_vxb"/>

## Procedure

1.  In the *Business User Groups* overview screen of the *Maintain Business User Groups* app, select one or more business user groups.

2.  Click *Add to Transport*. A list of available customizing transports appears.

    > ### Note:  
    > The default transport is always displayed as well as your own transports. If no transport exists, a confirmation dialog is shown. If you confirm, a new transport is created.

3.  Select the required transport and click *OK*. The selected business user groups are then added to the transport.

4.  Open the *Export Customizing Transports* app and release your request. For more information, see [Export Customizing Transports](export-customizing-transports-a772a0f.md).

5.  Import your business user groups to the target system:

    1.  Open the *Manage Software Components* app.

    2.  Select *Business Configuration* in the *Type* dropdown and click *Go*.

    3.  Select the component to which the relevant configuration was exported.

    4.  In the detail view of the component, check out the change that contains your business user group\(s\). For more information, see [How to Work with Branches](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/6b2f0bfc14cb47ef888f01784c92e1bf.html?version=Cloud).


    > ### Note:  
    > If you want to delete a business user group that was previously transported or is currently included in an open transport request, the system offers you to add it directly to an available transport.
    > 
    > If the business user group was previously transported and there is currently no transport available, a confirmation dialog is shown. If you confirm, a new transport is created.


