<!-- loio3943c74328df43ad9a1fd22c39882aae -->

# Configuring the ATC Developer Scenario

You can use a system in SAP Business AI Platform, ABAP environment as a central check system to run ATC checks from an on-premise system against this system \(ATC Developer Scenario\).



<a name="loio3943c74328df43ad9a1fd22c39882aae__prereq_hzn_gys_zyb"/>

## Prerequisites

-   You’ve defined communication arrangement [SAP\_COM\_0464](../50-administration-and-ops/sap-com-0464-34e52b1.md) \(SAP Custom Code Migration Integration\) to enable communication from your ABAP environment to your on-premise systems using remote function calls \(RFC\). For more information, see [Maintaining Communication Arrangements](maintaining-communication-arrangements-7849aa4.md).

-   You’ve implemented [SAP Note 3358660 - Developer Scenario Cloud](https://me.sap.com/notes/3358660/E) in your checked system.



## Procedure

**Central Check System \(SAP Business AI Platform, ABAP environment system\)**

To enable the ATC Developer Scenario, you've to define communication arrangement `SAP_COM_0936` for your cloud system.

1.  Log on to the *SAP Fiori launchpad* of your ABAP environment.

2.  In the *Communication Management* section, select the *Communication Arrangements* tile.

3.  Choose *New*.

4.  Use the value help to choose the `SAP_COM_0936` scenario.

5.  Define and enter an *Arrangement Name*.

6.  If not yet available or defined, create a new communication system for the communication arrangement to define an endpoint for your checked system.

    1.  For the *Communication System*, choose *New*.

    2.  In the *New Communication System* dialog, enter the *System ID* and *System Name* of the checked system.

    3.  Choose *Create*.

    4.  In the *Technical Data* tab under *General*, select the *Inbound Only* check box.

        Only select the *Inbound Only* check box if you're using a new communication system. Don't check this box when you're re-using a communication scenario.

    5.  In the *Users for Inbound Communication* tab, choose *\+* to add a new inbound communication user.

    6.  Choose *User Name and Password* as *Authentication Method*, and enter a user name, description, and password for the user.

    7.  Choose *Create*.


7.  In the Communication Arrangement in the *Inbound Communication* tab, enter the *User Name* you’ve previously defined as described in step 6.

8.  In the *Additional Properties* tab, select the *Object Provider* you’ve defined in `SAP_COM_0464`.

9.  Choose *Save*.


**Checked System \(on-premise system\)**

Once you've defined communication arrangement `SAP_COM_0936` for your ABAP environment system, you have to define an RFC connection from your on-premise system to the cloud system.

10. If not yet available or defined, create a new RFC destination in transaction `SM59`. To do this, proceed as follows \(see also [Maintaining Remote Destinations](https://help.sap.com/docs/ABAP_PLATFORM_NEW/8f3819b0c24149b5959ab31070b64058/488965b484b84e6fe10000000a421937.html)\):

    > ### Note:  
    > To set up your RFC connection, you first need to open a **service channel** \(on-premise to cloud connection\) in your respective Cloud Connector. See [Configure a Service Channel for RFC](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-service-channel-for-rfc?version=Cloud) to learn how to create one.

    1.  Choose connection type "3" \(ABAP Connection\) or connection type "W" \(WebSocket RFC\) to connect to your cloud system via [Cloud Connector](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector?version=Cloud).

    2.  In the *Technical Settings* tab, enter the host of your Cloud Connector as *Target Host*. As instance number, choose the instance number that you've defined for your service channel.

    3.  In the *Logon & Security* tab, enter the correct client of your cloud system. The user to be entered here's the inbound communication user that you've assigned to communication scenario `SAP_COM_0936`. Here you need to enter the **alias name** of this user. The alias name is limited to 12 characters.

    4.  As an optional step, you can run a connection test, which should be successful.

    5.  Save your destination.


11. Run transaction `ATC` and choose *ATC Administration* \> *Setup* \> *Basic Settings*.

12. In the *Code Inspector* section, enter the RFC destination as *Reference Check System* and save.

13. Go to transaction `SCI` and create a proxy variant \(as described in step 2 in [Configuring the Checked System](https://help.sap.com/docs/ABAP_PLATFORM_NEW/ba879a6e2ea04d9bb94c7ccd7cdac446/17eb1a1d504442b3ad438451197b937b.html)\).

    You can reference one of the SAP delivered ATC variants in your cloud system, for example `SLIN_SEC`, or one of your own variants that you've created in the cloud system. Go to [Creating ATC Check Variants](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/creating-atc-check-variants) for guidance on how to create ATC check variants.

14. Go back to transaction `ATC` and choose *ATC Administration* \> *Setup* \> *Basic Settings*. In the *Code Inspector* section, enter the name of the proxy variant as *Global Check Variant* and save.




<a name="loio3943c74328df43ad9a1fd22c39882aae__result_snj_hct_zyb"/>

## Results

You've enabled a cloud system as the central check system for remote ATC checks from an on-premise system against the cloud system. In SAP GUI or ABAP development tools for Eclipse, you can now run ATC checks in your checked system. In ABAP development tools for Eclipse in the *ATC Problems* view, you can create exemptions that you can then manage in the [Approve ATC Exemptions](https://help.sap.com/docs/btp/sap-business-technology-platform/approve-atc-exemptions) app.

> ### Note:  
> If you want to connect additional checked systems to the central check system, repeat steps 3–14 for each checked system. Communication arrangement `SAP_COM_0464` and the corresponding object provider need to be defined for every checked system. In step 10c, make sure to enter the alias name of the communication user that you created for this specific checked system in the dedicated communication arrangement of communication scenario `SAP_COM_0936`.
> 
> **Each checked system requires its own dedicated communication arrangement with its own communication user.**

