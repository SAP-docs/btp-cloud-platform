<!-- loio54d36ff122d64c59a10b803463d82f0b -->

# Using Client Certificate Authentication



## Context

To be able to use client certificate authentication, you need to configure both SAP S/4HANA Cloud and SAP BTP sides.

 <a name="loio54d36ff122d64c59a10b803463d82f0b loiod8e98a9d49b844479049208bf00593a1__loiod8e98a9d49b844479049208bf00593a1"/>

<!-- loiod8e98a9d49b844479049208bf00593a1 -->

# Set Up SAP S/4HANA Cloud Side



<a name="loiod8e98a9d49b844479049208bf00593a1__context_qrv_ljr_b2b"/>

## Context

To use client certificate authentication, you first start with creating and configuring the communication settings in the SAP S/4HANA Cloud tenant. To do that, you have to:



<a name="loiod8e98a9d49b844479049208bf00593a1__steps_rrv_ljr_b2b"/>

## Procedure

1.  Obtain a client certificate signed by a trusted certificate authority \(CA\) in *.pem* format.

    You can find a list of the trusted CA in the SAP S/4HANA Cloud tenant using the **Maintain Certificate Trust List** application. See [Maintain Certificate Trust List](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/1808.500/en-US/2b3c3f1e4007472883abe5226e84f05f.html).

2.  Create a communication user and upload the public key. See [Maintain Communication Users](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/1808.500/en-US/eef80dda3867461c92ac1273689ed36f.html).

3.  Create a communication system and add the communication user as *User for Inbound Communication* with an authentication method SSL Client Certificate.

    1.  Log into the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

    2.  Select the *Communication Systems* tile.

    3.  Choose *New* to create a new system.

    4.  Enter a system ID and a system name.

    5.  Choose *Create*.

    6.  Enter information about SAP BTP in the *Technical Data* section.

    7.  Choose *+* \(Add\) under *User for Inbound Communication*.

    8.  In the dialog box that appears, select *SSL Client Certificate* from the *Authentication Method* drop-down list.

        The username corresponds to the communication user.

    9.  Choose *OK* to confirm.

    10. Choose *Save*.

4.  Create a communication arrangement using an existing or create a new scenario that supports client certificate authentication. See [Maintain Communication Arrangements](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/1808.500/en-US/fab3fd449cf74c6384622b98831e989e.html).

    You can use the already created communication system. The settings in the *Inbound Communication* section are filled in automatically. Save the value from the *URL* field, you will need it when creating a destination in the subaccount in SAP BTP.


 <a name="loio54d36ff122d64c59a10b803463d82f0b loio311edbe5befa4e06b434c2130bc493b2__loio311edbe5befa4e06b434c2130bc493b2"/>

<!-- loio311edbe5befa4e06b434c2130bc493b2 -->

# Set Up SAP BTP Side



<a name="loio311edbe5befa4e06b434c2130bc493b2__prereq_yhj_m5w_3bb"/>

## Prerequisites

You have logged into the SAP BTP cockpit from the SAP BTP landing page for your subaccount.



<a name="loio311edbe5befa4e06b434c2130bc493b2__steps_vhq_fww_3bb"/>

## Procedure

1.  In the cockpit, navigate to your subaccount.

2.  Choose *Connectivity* \> *Destinations* in the navigation panel.

3.  Choose *New Destination* and fill in the following properties:


    <table>
    <tr>
    <th>

    Parameter


    
    </th>
    <th>

    Value


    
    </th>
    </tr>
    <tr>
    <td>

    `Name`


    
    </td>
    <td>

    Enter a meaningful name.


    
    </td>
    </tr>
    <tr>
    <td>

    `Type`


    
    </td>
    <td>

    ***HTTP***


    
    </td>
    </tr>
    <tr>
    <td>

    `Description`


    
    </td>
    <td>

    \(Optional\) Enter a meaningful description.


    
    </td>
    </tr>
    <tr>
    <td>

    `URL`


    
    </td>
    <td>

    The service URL from the communication arrangement.

    Make sure you use the HTTPS protocol, otherwise the *ClientCertificateAuthentication* option would not appear in the *Authentication* doropdown list.


    
    </td>
    </tr>
    <tr>
    <td>

    `Proxy Type`


    
    </td>
    <td>

     ***Internet*** 


    
    </td>
    </tr>
    <tr>
    <td>

    `Authentication`


    
    </td>
    <td>

    ***ClientCertificateAuthentication***

    > ### Note:  
    > Once you have selected this option, the system displays the *Upload and Delete Certificate* link.


    
    </td>
    </tr>
    </table>
    
4.  Choose *Upload and Delete Certificate* link to upload your keystore. The keystore format .jks. When you finish uploading, choose *Close*.

    The keystore contains the key/pair signed by the trusted certificate authority \(CA\) in [Set Up SAP S/4HANA Cloud Side](Using_Client_Certificate_Authentication_54d36ff.md#loiod8e98a9d49b844479049208bf00593a1), **step 1**.

    1.  From the *Key Store Location* drop-down menu, select your keystore.

    2.  In the *Key Store Password*, enter the keystore password.

5.  Select the *Use default JDK truststore* checkbox.

6.  Save your entries.


**Related Information**  


[Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html)

