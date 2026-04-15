<!-- loio5481d594718f44c1ad7a63d154c342fd -->

# Register a Third-Party System

To connect a third-party systems, for example a Google system, with a global account in SAP BTP, you first need to create a system type for this system and then to add a system of this new type to the **Systems** page.



<a name="loio5481d594718f44c1ad7a63d154c342fd__prereq_l4m_s5b_fhb"/>

## Prerequisites

You are a global account administrator, or you are a system landscape administrator of the global account where you want to add your third-party system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).



<a name="loio5481d594718f44c1ad7a63d154c342fd__context_ihl_j3h_jlb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

To add a third-party system to the list in the *System Landscape* \> *Systems* page, you need to create a system type for this third-party system. At this point you provide all the required details for this system type: its name, namespace, and provider. Then, you add systems of this new type. For third-party systems, this completes the registration process and you have your third-party system registered with SAP BTP. Even though the third-party system is registered directly, no status is displayed.

When you have this system added in the *Systems* page, you can select it and open its system details. There, you specify in the consumption bundles the APIs, and the events. A consumption bundle organizes a set of related APIs and events into a single group for consumption purposes and expresses information about how the APIs and events that it contains can be accessed. All APIs and events that are part of the same consumption bundle need to be accessible through the same set of credentials.

> ### Note:  
> You cannot migrate the added third-party systems between global accounts.
> 
> If you want to start using another global account, you will have to add your systems again.

> ### Note:  
> When adding a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



<a name="loio5481d594718f44c1ad7a63d154c342fd__steps_qrt_jfd_dxb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  Go to the *System Types* tab, and choose *Create System Type*.

3.  In the *Create System Type* dialog:

    1.  In the *Name* field, enter the name of the system type you are creating. Later on, this name will appear in the *System Type* dropdown menu when you add a system of this type.

        Use a user-friendly name and reflect as best as possible the commercial name of the product or system. For example, **Google Workspace**.

    2.  In the *Namespace* field, specify the namespace of the system type. It must start with **customer.\***. For example, **customer.google.workspace**.

    3.  In the *Provider* field, enter the actual organization that provides the given system type. For example, **Google**.

    4.  Choose *Create*.


4.  Go to the *Systems* tab, and choose *Add System*.

5.  In the *Add System* wizard:

    1.  In the *System Type* dropdown list, select the system type you have created for your third-party system.

    2.  Enter a name for the system you want to register.

        > ### Note:  
        > Use only printable ASCII characters.

    3.  Choose *Add*.


6.  \(Optional\) Find this system in the *Systems* list and open its system details. Choose *Add Consumption Bundle* and fill in the following properties:

    -   *Consumption Bundle Name*: add a meaningful name

    -   *Description*:

    -   *Credentials Type*: choose between OAuth and Basic

        -   If you choose *OAuth*, fill in these properties:

            -   *Client ID*

            -   *Client Secret*

            -   *URL*: this is the token URL, that is used for obtaining OAuth tokens through the client ID and the client secret.


        -   If you choose *Basic*, fill in these properties:

            -   *User*

            -   *Password*




    Choose *Add*. Open the consumption bundle from the list.

7.  \(Optional\) If you want to add APIs, choose *Add API* and fill in the following properties:

    -   *API Name*: add a meaningful name.

    -   *Description*: this field is optional.

    -   *URL*

    -   *Specification*: this is the file containing the specification. The file format depends on the specification type. For OpenAPI, you can use YAML and JSON. For OData, you can use JSON and XML.

    -   *Type*: this is the type of the specification. The API specification type can be OpenAPI or OData.


8.  \(Optional\) If you want to add events, choose *Add Event* and fill in the following properties:

    -   *Event Name*: add a meaningful name.

    -   *Description*: this field is optional.

    -   *Specification*: this is the file containing the specification. The file format can be JSON and YAML.

    -   *Type*: this is the type of the specification. The event specification type can be only AsyncAPI.





<a name="loio5481d594718f44c1ad7a63d154c342fd__result_ytq_hrh_jlb"/>

## Results

The system has been added as a record to the list on the *Systems* page in the SAP BTP cockpit and you have added the respective APIs or events.

If you no longer need it, you can remove the system depending on its status. See [Deregister or Removе a System](deregister-or-remov-a-system-0c6f498.md).

