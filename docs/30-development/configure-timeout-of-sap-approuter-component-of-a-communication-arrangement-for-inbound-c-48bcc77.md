<!-- loio48bcc77bf94341a4846ba694b7fd6e1c -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Timeout of @sap/approuter Component of a Communication Arrangement for Inbound Communication with Service Key OAuth

By default, communication between the approuter and connected services is timed out after 30 seconds. This default value is suitable for most applications. However, for long-lasting data transfer, communication lasts longer. If you experience timeouts, you can set the service key parameter `abap_endpoint_timeout` to a value higher than 30 seconds.



<a name="loio48bcc77bf94341a4846ba694b7fd6e1c__prereq_wzz_g1y_qjb"/>

## Prerequisites

-   You have created a space. See [Create Spaces](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2f6ed22ccf424dae84345f4500c2d8ea.html).
-   You have the space developer role. See [Assigning the Space Developer Role to the Developer Users](https://help.sap.com/viewer/a96b1df8525f41f79484717368e30626/Cloud/en-US/967fc4e2b1314cf7afc7d7043b53e566.html).



<a name="loio48bcc77bf94341a4846ba694b7fd6e1c__steps_w2g_5rf_fpb"/>

## Procedure

1.  Log on to the cockpit and go to the subaccount that contains the space you'd like to navigate to. See [Navigate in the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0874895f1f78459f9517da55a11ffebd.html).

2.  In the navigation area, go to *Cloud Foundry* \> *Spaces* and choose your space.

3.  Select *Services* \> *Instances* from the navigation area and navigate to your ABAP system service instance.

4.  Click on <span class="SAP-icons"></span>  and select *Create Service Key*.

5.  In the *New Service Key* dialog, enter a name for your service key and specify the parameter in JSON format as follows:

    ```
    {
          "abap_endpoint_timeout": 600000
    }
    
    ```

    > ### Note:  
    > You can use s \(seconds\) or m \(minutes\) to define the value.
    > 
    > If no unit is defined, the value is interpreted as seconds.
    > 
    > The maximum value is 600s or 10m.


**Related Information**  


[Integration with Business Services](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f6337cd6065a42b59579c069256072ec.html)

