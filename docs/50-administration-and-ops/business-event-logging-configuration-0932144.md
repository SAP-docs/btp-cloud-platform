<!-- loio0932144a40ef4538bd93ce57d6d26139 -->

# Business Event Logging Configuration



<a name="loio0932144a40ef4538bd93ce57d6d26139__section_s32_44c_crb"/>

## Prerequisites

To configure business event logging, create a business role and assign the catalog `SAP_BCR_CA_IC_LND_BEL_BCO_PC` to the role. For instructions, refer to [How to Create a New Business Role](how-to-create-a-new-business-role-f65e51a.md). You can also create a business role using the template `SAP_BR_BPC_EXPERT`. For instructions, refer to [How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md) .



<a name="loio0932144a40ef4538bd93ce57d6d26139__section_ldx_4vl_tsb"/>

## Configure the Application



### Activate Business Event Logging

To activate logging for your objects:

1.  Open the *Custom Business Configurations* app. You’ll see a list of all business configurations that can be adapted.
2.  Search for*Activate Business Event Logging* using the search bar.

3.  Select the custom business configuration from the list and choose *Edit*.
4.  To activate logging for an object, select the *Activate Logging* checkbox and choose *Save*.
5.  \(Optional\) To enable logging for all business event data, select the *Log All Data* checkbox for the object.

    > ### Caution:  
    > When you enable logging for all business event data, it consumes additional storage.

6.  To create a new entry, choose *New Entries*.
7.  Enter the *Object* and select the *Activate Logging* checkbox.
8.  Choose *Save*.

For documentation about this item, refer to *Show Documentation*.

