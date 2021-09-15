<!-- loiofae8f0f1e4204e6e8c6ebca51da1b154 -->

# Define Specific Properties for Communication Scenarios

For some use cases, such as logical receiver determination based on arbitrary parameters, a communication scenario may require additional parameters that are not part of the standard fields of a communication scenario. Therefore, you can define additional properties in a communication scenario that can be maintained by the administrator in the *Communication Arrangements* app. These properties also support secure storage of data, such as passwords or API keys.



<a name="loiofae8f0f1e4204e6e8c6ebca51da1b154__section_i35_khn_bpb"/>

## Prerequisite

A data element that describes your property is required.

The following definitions are derived from the data element:

-   *Data Type* 
-   *Value Help*

-   *Field Label* \(long text\) for the *Communication Arrangements* app




Enter the name of property in the communication scenario and define the following:

-   *Default Value*: This value will be added automatically if you create a communication arrangement

-   *Data Element*: Describes the property \(please see above\)

-   *Is Multiple*: Indicates that one can maintain multiple values for the property in the *Communication Arrangements* app

-   *Is Secure*: Indicates that this property is stored within the secure store. You can use this to store add. Passwords or API Keys

-   *Is Hidden*: Indicates that this property is not displayed on the *Communication Arrangements* app and only used for internal usage

-   *Value Help*: Indicates that a value help shall be used in the *Communication Arrangements* app


