<!-- loio0932144a40ef4538bd93ce57d6d26139 -->

# Business Event Logging Configuration



<a name="loio0932144a40ef4538bd93ce57d6d26139__section_s32_44c_crb"/>

## Prerequisites

To configure business event logging, create a business role and assign the catalog `SAP_CA_BC_IC_LND_BEL_BCO_PC` to the role. For instructions, refer to [How to Create a New Business Role](how-to-create-a-new-business-role-f65e51a.md). You can also create a business role using the template `SAP_BR_BPC_EXPERT`. For instructions, refer to [How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md) .



<a name="loio0932144a40ef4538bd93ce57d6d26139__section_ldx_4vl_tsb"/>

## Configure the Application



### Activate Business Event Logging

To activate logging for your objects:

1.  Open the *Custom Business Configurations* app. You’ll see a list of all business configurations that can be adapted.
2.  Search for*Activate Business Event Logging* using the search bar.

3.  Select the custom business configuration from the list and choose *Edit*.
4.  To create a new entry, choose *New Entries*.
5.  Enter the *Object* and select the *Activate Logging* checkbox to activate logging for the object.

    > ### Note:  
    > When you activate logging for an object, the keys and metadata such as event type, performed by, performed at, and other details of the object are logged and displayed in the business event logging apps. When you enable logging for all business event data, all changes made to the object is logged by the system. The fields captured by the system depend on how the event has been defined. For more information on the fields that get logged, refer to the SAP Business Accelerator Hub.

6.  Choose *Save*.

For documentation about this item, refer to *Show Documentation*.

