<!-- loio7d768f1ae1124dff9025bc5f1ffa12d0 -->

# Configure Units of Measurement

With this app, you can create, update, and delete units of measurement \(UoM\).



## Prerequisites

To configure units of measurement, create a business role and assign the catalog `SAP_CA_BC_IC_LND_UOM_BCO_PC` to the role. For more information, see [How to Create a New Business Role](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-business-role-from-scratch?version=Cloud). You can also create a business role using the `SAP_BR_BPC_EXPERT` template. For more information, see [How to Create a Business Role from a Template](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-business-role-from-template?version=Cloud).



## Key Features

Use this app to display, create, change, and delete:

-   Units of measurement

-   Dimensions for units of measurement

-   ISO codes for units of measurement




## Access Information

1.  To access the app, create a business role and assign it to your user as described in the prerequisites above.
2.  Open the `Custom Business Configurations` app. A list of all business configurations, which can be adapted, is displayed.

3.  Choose the *Settings* button.

4.  In the *View Settings* dialog window, go to the *Group* tab, group by *Configuration Group*, and choose *OK*.

    The three units of measurement configurations are now displayed together in the *Check Units of Measurement* group. Alternatively, you can use the regular search function to search for the UoM configurations individually, but we recommend using the group function to find them more easily.




## Procedure



### Configuring Units of Measurement

1.  In the `Custom Business Configurations` app, search and open *Units of Measurement*.

2.  To create a new entry, choose *Edit*, then *Create*.

3.  Enter the internal unit of measurement, select the dimension, and choose *Continue*.

4.  Fill in the required fields *Commercial Unit* and *Technical Unit*, and enter a text in the *Unit of Measurement Text* field for the new unit.

5.  Maintain the other configuration sections as needed: *Display*, *Conversion*, *ALE/EDI*, *Application Parameters*, and *Temperature/Pressure Specifications*.

6.  Save your entries.




### Configuring Dimensions for Units of Measurement

1.  In the `Custom Business Configurations` app, search and open *Dimensions for Units of Measurement*.

2.  To create a new entry, choose *Edit*, then *Create*.

3.  Enter the dimension and choose *Continue*.

4.  Enter a text in the *Dimension Text* field and fill in the configuration sections *Dependency* and *Dimension Exponents* as needed.
5.  Save your entries.

Once units are defined for a dimension, you can use the app to assign the official SI Unit to that dimension.



### Configuring ISO Codes for Units Measurement

1.  In the `Custom Business Configurations` app, search and open *ISO Codes for Units of Measurement*.

2.  To create a new entry, choose *Edit*, then *Create*.

3.  In the newly created row at the end, enter the ISO code and ISO code text.
4.  Save your entries.



## Supported Device Types

-   Desktop



## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-ASF-UOM`.



## Related Information

[Custom Business Configurations App](custom-business-configurations-app-76384d8.md)

