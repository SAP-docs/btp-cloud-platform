<!-- loio9be64407119e4765942085663048b870 -->

# Fiori Elements Integration OData V4

You can implement the reusable component from the **Reuse Library** in a Fiori Elements app in order to display an application log.



<a name="loio9be64407119e4765942085663048b870__section_cfw_vr5_lfc"/>

## Context

To implement the reusable component in a Fiori Elements app, you first have to add the application log reuse component to your manifest.



<a name="loio9be64407119e4765942085663048b870__section_z5j_xr5_lfc"/>

## Procedure

1.  Open the `manifest.json` file of the application and locate the `sap.ui5` section.
2.  Add the `sap.nw.core.changedocs.lib.reuse` library under dependencies:

    > ### Sample Code:  
    > ```
    > "sap.ui5": {
    >     "dependencies": {
    >       "libs": {
    >         " sap.nw.core.changedocs.lib.reuse": {
    >         "lazy": true
    >         }
    >     }
    >   }
    > }
    > 
    > ```

3.  Next, **create a view extension** by adding a custom section to your object page using the **Guided Development** tool or by manually adjusting the`manifest.json file`:
    -   Right-click on your projects root folder and click **Open Guided Development**
    -   Choose the guide **Add a custom section to an object page using extensions**

        ![](images/61b8b0f0faa245c89853fbb3968605b9.image)

    -   In your `manifest.json file`, you should now be able to see something similar to the following:

        > ### Sample Code:  
        > ```
        >       "targets": {
        >         "ZC_BV_SZD_BOOKList": {
        >           "type": "Component",
        >           "id": "ZC_BV_SZD_BOOKList",
        >           "name": "sap.fe.templates.ListReport",
        >           "options": {
        >             "settings": {
        >               "contextPath": "/ZC_BV_SZD_BOOK",
        >               "variantManagement": "Page",
        >               "navigation": {
        >                 "ZC_BV_SZD_BOOK": {
        >                   "detail": {
        >                     "route": "ZC_BV_SZD_BOOKObjectPage"
        >                   }
        >                 }
        >               },
        >               "controlConfiguration": {
        >                 "@com.sap.vocabularies.UI.v1.LineItem": {
        >                   "tableSettings": {
        >                     "type": "ResponsiveTable"
        >                   }
        >                 }
        >               }
        >             }
        >           }
        >         },
        >         "ZC_BV_SZD_BOOKObjectPage": {
        >           "type": "Component",
        >           "id": "ZC_BV_SZD_BOOKObjectPage",
        >           "name": "sap.fe.templates.ObjectPage",
        >           "options": {
        >             "settings": {
        >               "editableHeaderContent": false,
        >               "contextPath": "/ZC_BV_SZD_BOOK",
        >               "content": {
        >                 "body": {
        >                   "sections": {
        >                     "myCustomSection": {
        >                       "template": "chdbookproject.custom.fragment.chdFragmentExtension",
        >                       "title": "chdBookExt",
        >                       "position": {
        >                         "placement": "After",
        >                         "anchor": "idIdentification"
        >                       }
        >                     }
        >                   }
        >                 }
        >               }
        >             }
        >           }
        >         }
        >       }
        > 
        > ```


4.  Open the fragment that was created from the **Guided Development** tool and add a component container:

    > ### Sample Code:  
    > ```
    > <core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" >
    >     <core:ComponentContainer id="ChdContainer"/>
    > </core:FragmentDefinition>
    > 
    > ```

5.  As a next step, **create a controller extension**. First, open the `manifest.json file` of the application and locate the `sap.ui5` section. Then, add an object page controller extension:

    > ### Sample Code:  
    > ```
    > 
    > "extends": {
    >       "extensions": {
    >         "sap.ui.controllerExtensions": {
    >           "sap.fe.templates.ObjectPage.ObjectPageController": {
    >             "controllerName": "chdbookproject.ext.controller.ChdControllerExt"
    >           }
    >         }
    >       }
    >     }
    > 
    > ```

6.  Create the controller extension file with the specified name and path from the `manifest.json` file:

    ![](images/ceb5ed63062f4d39b82bb375fe3e9fdf.image)

7.  Adjust the controller extension coding by opening the `ObjectPageExt.controller.js` file you've created and adjust the coding like this:

    > ### Note:  
    > Make sure to adjust the names and paths accordingly.

    > ### Sample Code:  
    > ```
    > sap.ui.define(
    >   ['sap/ui/core/mvc/ControllerExtension', 'sap/ui/core/Core'],
    >   function (ControllerExtension, Core) {
    >     'use strict';
    > 
    >     return ControllerExtension.extend(
    >     'chdbookproject.ext.controller.ChdControllerExt', {
    >         _chdContainer: "chdbookproject::ZC_BV_SZD_BOOKObjectPage--fe::CustomSubSection::myCustomSection--ChdContainer",
    >         // this section allows to extend lifecycle hooks or hooks provided by Fiori elements
    >         override: {
    >       /**
    >        * Called when a controller is instantiated and its View controls
    >        * (if available) are already created.
    >        * Can be used to modify the View before it is displayed, to bind
    >        * event handlers and do other one-time initialization.
    >        * @memberOf chdbookproject.ext.controller.ChdControllerExt
    >        */
    >       onInit: function () {
    >             var that = this;
    >             // you can access the Fiori elements extensionAPI via this.base.getExtensionAPI
    >             var oViewId = this.getView().getId();
    >             if (oViewId === "chdbookproject::ZC_BV_SZD_BOOKObjectPage") {
    >         this._oComp = Core.createComponent({
    >                 name: "sap.nw.core.changedocs.lib.reuse.changedocscomponent",
    >                 id : "ChangeDocReuseComponent",
    >                 settings: {
    >           "objectClass": ["ZBVSZDBOOK"],
    >           "startDate": "2019-01-28T00:00:00.0000",
    >           "stIsAreaVisible": true
    >                 }
    >         });
    >          var oChdContainer = Core.byId(this._chdContainer);
    >          if (oChdContainer !== undefined) {
    >            oChdContainer.setComponent(this._oComp);
    >          }
    > 
    >          this._oComp.setStIsAreaVisible(true);
    >          this._oComp.stRefresh();
    >             }
    >       },
    >           editFlow: {
    >             onAfterSave: function () {
    >               var that = this;
    >               this._oComp.stRefresh();
    >             }
    >           },
    >           routing: {
    >             onAfterBinding: function (oBindingContext) {
    >               var that = this; 
    >               oBindingContext.requestProperty("Idnr").then(function (sObject) {
    >                 if (sObject) {
    >                   that._oComp.setObjectId([sObject]);
    >                 }
    > 
    >                 that._oComp.stRefresh();    
    >               });
    >             }
    >           },
    >           
    >     }
    >       }
    >     )
    >   });
    > 
    > ```

8.  To**refresh the logs**, you can use the edit flow hooks offered by the controller extension. See also [UI5 Demo Kit: Edit Flow Overview](https://sapui5.hana.ondemand.com/). An example:

    > ### Sample Code:  
    > ```
    > 
    > editFlow: {
    > 				onAfterSave: function () {
    > 					var that = this;
    > 			 		this._oComp.stRefresh();
    > 				}
    > 			},
    > 
    > ```


