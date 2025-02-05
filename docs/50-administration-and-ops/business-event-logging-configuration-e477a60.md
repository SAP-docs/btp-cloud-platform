<!-- loioe477a6054926477c92e248375f338508 -->

# Business Event Logging Configuration

You can configure business event logging using Configuration Items.



<a name="loioe477a6054926477c92e248375f338508__section_s32_44c_crb"/>

## Prerequisites

To configure business event logging, create a business role and assign the catalog `SAP_BCR_CA_IC_LND_BEL_BCO_PC` to the role. For instructions, refer to [How to Create a New Business Role](how-to-create-a-new-business-role-f65e51a.md). You can also create a business role using the template `SAP_BR_BPC_EXPERT`. For instructions, refer to [How to Create a Business Role from a Template](how-to-create-a-business-role-from-a-template-ec310a8.md) .



<a name="loioe477a6054926477c92e248375f338508__section_ldx_4vl_tsb"/>

## Configure the Application



### Activate Logging for SAP Object Types

To activate logging for your SAP Object Types:

1.  Open the *Custom Business Configurations* app. You’ll see a list of all business configurations that can be adapted.
2.  Search for*Activate Logging by SOT* using the search bar.

3.  Select the custom business configuration from the list and choose *Edit*.
4.  To activate logging for an SAP Object Type, select the *Activate Logging* checkbox and choose *Save*.
5.  \(Optional\) To enable logging for all business event data, select the *Log All Data* checkbox for the SAP Object Type.

    > ### Caution:  
    > When you enable logging for all business event data, it consumes additional storage.

6.  To create a new entry, choose *New Entries*.
7.  Enter the *SAP Object Type* and select the *Activate Logging* checkbox.
8.  Choose *Save*.

For documentation about this item, refer to *Show Documentation*.

> ### Note:  
> Ensure that you configure the retention period for SAP Object Types. For more information, refer to [Destroying Business Event Logging Objects Using BEL\_TIMESTAMP\_DESTRUCTION](destroying-business-event-logging-objects-using-bel-timestamp-destruction-4005b2f.md).

