<!-- loioc2234acd55774ebcbedb66744199273e -->

# How to Create Communication Systems



<a name="loioc2234acd55774ebcbedb66744199273e__HowToCreateCommSystems_context"/>

## Context

To create a communication system perform the following steps:



<a name="loioc2234acd55774ebcbedb66744199273e__HowToCreateCommSystems_steps"/>

## Procedure

1.  On the initial screen select *New*.

2.  In the *New Communication System* dialog define an ID and a name of the new system.

3.  Fill in the required fields under:

    -   *General Data*
    -   *Technical Data* 

        *General*

        If you want your communication system to be used for a communication arrangement based on a communication scenario that only contains inbound services, we recommend that you select the *Inbound Only* checkbox. If this checkbox is selected, the input fields that are only required for outbound communication disappear.

        If your communication system is intended for outbound communication, host, port, user and authentication method are used as specified in the destination service.

    -   *Destination Service* \(Only for Outbound Communication\)

        Because SAP BTP ABAP Environment uses destination services of SAP BTP for outbound communication, you need to enter the name of the required destination service. For more information, see [Set Up the Destination Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3fa7934f5a714bf88d8490958211382f.html). You also need to select the instance the destination service is based on. For more information, see [Creating the Service Instance for the ABAP Environment](https://help.sap.com/viewer/a96b1df8525f41f79484717368e30626/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).

        > ### Note:  
        > A predefined instance is selected by default. If you want to add your own instance, deselect this instance.

    -   *SAML Bearer Assertion Provider*

        Before you can authenticate using SAML2 Bearer assertions transmitted via the authorization header, you have to configure a trusted relationship to the required identity provider. Upload the signing certificate of the trusted provider and define the provider name.

        Define the required *User ID Mapping Mode* if it is unspecified and you don't use e-mail addresses, but either logon name or user UUID.

    -   *Contact Information*

        Enter name, e-mail or phone number of a contact person.


4.  Add technical users for inbound communication. You can either select a user from the list or create a new user. If you decide to create a new user, you will be redirected to the *Maintain Communication User* app.

    > ### Note:  
    > Inbound users are communication users provided by your system and are used by the communication system to call the inbound services.

5.  Save the changes.

    You can now establish a communication arrangement with the created system. Use the *Maintain Communication Arrangements* app for this purpose.


**Related Information**  


[Maintain Communication Systems](Maintain_Communication_Systems_15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")



[How to Create Communication Users](How_to_Create_Communication_Users_0377ade.md "")

