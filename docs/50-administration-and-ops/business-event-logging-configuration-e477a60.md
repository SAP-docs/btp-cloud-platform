<!-- loioe477a6054926477c92e248375f338508 -->

# Business Event Logging Configuration

You can configure business event logging using Configuration Items.



<a name="loioe477a6054926477c92e248375f338508__section_s32_44c_crb"/>

## Prerequisites

To configure business event logging, create a business role and assign the catalog `SAP_CA_BC_IC_LND_BEL_PC` to the role. For instructions, refer [here](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/f84e5ce53c754d799cffd0c724cbcdce.html). You can also create a business role using the template `SAP_BR_BPC_EXPERT`. For instructions, refer [here](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/87807ffd176c4dbca23d97ff1ec0705c.html).



<a name="loioe477a6054926477c92e248375f338508__section_ldx_4vl_tsb"/>

## Configure the Application



### Activate Business Event Logging

To activate logging for your objects:

1.  From SAP Fiori launchpad, go to *Implementation Cockpit \> Manage Your Solution \> Configure Your Solution*.
2.  On the *Configure Your Solution* screen, in the *Application Area* field, select *Application Platform and Infrastructure*. Then in the *Sub Application Area* field, select *Process Management and Integration*.
3.  In the *All Items* table, choose *Business Event Logging*.
4.  In the configuration step,**Activate Business Event Logging**, choose *Configure*.
5.  To activate logging for an object, select the *Enable Log* checkbox and choose *Save*.
6.  \(Optional\) To enable logging for all business event data, select the *All Data* checkbox for the object.

    > ### Caution:  
    > When you enable logging for all business event data, it consumes additional storage.

7.  To create a new entry, choose *New Entries*.
8.  Enter the *Object* and select the *Enable Log* checkbox.
9.  Choose *Save*.

For documentation about this item, refer to *Configuration Help*.

> ### Note:  
> Ensure that you configure the retention period for objects. For more information, refer to [Destroying Business Event Logging Objects Using BEL\_TIMESTAMP\_DESTRUCTION](destroying-business-event-logging-objects-using-bel-timestamp-destruction-4005b2f.md).

