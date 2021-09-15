<!-- loio04488354490349f989871c5d555a2926 -->

# Create a Communication Arrangement

You create a communication arrangement in the ABAP environment.



<a name="loio04488354490349f989871c5d555a2926__prereq_trr_bpz_k4b"/>

## Prerequisites

You have the *Administrator* role \(role template `ID SAP_BR_ADMINISTRATOR`\).



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment.

2.  Open the *Communication Arrangement* app.

3.  Choose *New*.

4.  Select the communication scenario `SAP_COM_0065`.

5.  Enter a name for the arrangement.

6.  Choose *Create*.

7.  In the *Common Data* section, select the *Communication System* that you created in the previous section.

8.  Under *Additional Properties* \> *Tenant ID* maintain the tenant ID that is visible in the URL of the SAP Analytics Cloud app.

    When you call `https://xxx.sapanalytics.cloud`, you will be redirected to the full URL where you can find the tenant ID as shown in this example: `https://xxx.sapanalytics.cloud/sap/fpa/ui/tenants/«tenant ID»/app.html`. You can also find the tenant ID under *Menu* \> *SAC Tenant* \> *System* \> *About* \> *System Name*.

9.  Under *Outbound Services* \> *UI Link Navigation*, check the *Service Status* as *Active*.

10. Under *Retrieve Stories*, uncheck the *Service Status*.

    > ### Note:  
    > Retrieving stories is not supported.

11. Choose *Save*.

    > ### Note:  
    > Do not create more than one communication arrangement with communication scenario `SAP_COM_0065` in your ABAP Environment tenant.


