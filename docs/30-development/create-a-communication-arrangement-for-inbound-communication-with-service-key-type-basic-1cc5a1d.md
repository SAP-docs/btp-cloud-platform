<!-- loio1cc5a1da02594b93a70f6c0fe2bfdfe8 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Communication Arrangement for Inbound Communication with Service Key Type Basic

Learn how to quickly create a communication user and communication arrangement for an inbound communication scenario by using a service key of type basic.



<a name="loio1cc5a1da02594b93a70f6c0fe2bfdfe8__prereq_wzz_g1y_qjb"/>

## Prerequisites

-   You have created a communication scenario.
-   You have created a space. See [Create Spaces](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2f6ed22ccf424dae84345f4500c2d8ea.html).
-   You have the space developer role. See [Assigning the Space Developer Role to the Developer Users](https://help.sap.com/viewer/a96b1df8525f41f79484717368e30626/Cloud/en-US/967fc4e2b1314cf7afc7d7043b53e566.html).



## Procedure

1.  Log on to the cockpit and go to the subaccount that contains the space you'd like to navigate to. See [Navigate in the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0874895f1f78459f9517da55a11ffebd.html).

2.  In the navigation area, go to *Cloud Foundry* \> *Spaces* and choose your space.

3.  Select *Services* \> *Instances* from the navigation area and find your ABAP system service instance.

4.  Click on <span class="SAP-icons-V5"></span>and select *Create Service Key*.

5.  In the *New Service Key* dialog, enter a name for your service key and specify the parameters in JSON format as follows:

    ```
    {
       "scenario_id":"SAP_COM_XYZ",
       "type":"basic"
    }
    
    ```

    > ### Note:  
    > `SAP_COM_XYZ` is the ID of the communication scenario in your ABAP system.
    > 
    > `basic` is the type of service key that is needed to generate a communication user and communication arrangement for an inbound communication scenario.

6.  **\(Optional to step 5\)** If your communication scenario has additional custom properties, you can automatically assign values to them by using the optional parameter `additional_properties`.

    ```
    {
       "scenario_id":"SAP_COM_XYZ",
       "type":"basic",
       "additional_properties": [
                {
                      "technical_name": "CUSTOM_PROPERTY_1",
                      "value": "VALUE_1"
                },
                {
                      "technical_name": "CUSTOM_PROPERTY_2",
                      "value": "VALUE_2"
                }
        ]     
    }
    
    ```

    > ### Note:  
    > `CUSTOM_PROPERTY_1` and `CUSTOM_PROPERTY_2` are the technical names of the properties as specified in your communication scenario. You can add any number of additional properties to the array`additional_properties` \(`CUSTOM_PROPERTY_3`, `CUSTOM_PROPERTY_4`, and so on\).
    > 
    > `VALUE_1`, `VALUE_2`, and so on are the values that should be assigned to the properties.




<a name="loio1cc5a1da02594b93a70f6c0fe2bfdfe8__result_lfm_1dy_qjb"/>

## Results

The communication user is generated and the credentials, depending on the selected type, are returned in the service key. The communication user receives authorizations for all services included in the communication scenario.

