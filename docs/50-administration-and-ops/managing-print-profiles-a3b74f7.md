<!-- loioa3b74f72fe854a4d877332590fff5608 -->

# Managing Print Profiles

You can manage your print profiles for `SAP_COM_0466` and `SAP_COM_0467` in the *Maintain Print Queues* app.



## Procedure

1.  Assign a printer to a 0466 or 0467 print queue in your OMS or in the *SAP Cloud Print Manager for Pull Integration*. Mind that print profiles in the print manager are only supported when in PDF format. Make sure to ignore the print profile in the *PDF Settings* of your print manager in order to secure a correct runtime of the tool.

    > ### Note:  
    > If you've used SAP\_COM\_0467 to integrate your local printers to the SAP BTP ABAP environment system, you can only choose a local printer from your external OMS instead.

2.  Now, open the *Maintain Print Queues* app and select the print queue for which you want to define your print profiles.

3.  Select *Manage Print Profiles* in the taskbar to set your print profile.

4.  In the *Print Options* dialog, you can manage your print settings. After you've selected your individual print settings from the dropdown menu, select *Save As*.

5.  Choose a profile name. Select *Use as favorite* to save the settings of your print profile. If no favorite has been selected, a default will be used. Each print job going into the same print queue will use these same settings. Click *OK*. Your new print profile has now been created. To delete a print profile, select *Delete* from the *Print Options* dialog.

    > ### Note:  
    > You can only define print profiles if you have administrator rights.


**Related Information**  


[SAP\_COM\_0466](sap-com-0466-524c13a.md "This document describes the configuration steps that have to be carried out by customers to set up the integration between SAP BTP ABAP environment and local printers using SAP_COM_0466.")

[SAP\_COM\_0467](sap-com-0467-523eb80.md "This document describes the configuration steps that have to be carried out by customers to set up the integration between SAP BTP ABAP environment and local printers using SAP_COM_0467.")

