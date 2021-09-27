<!-- loioa10285362c204f859e1061c7fc46e534 -->

# Connect the ABAP Environment System to SAP Analytics Cloud

Connect your ABAP environment system to SAP Analytics Cloud \(SAC\) using communication scenario SAP\_COM\_0065. Here's how:





### Create a Communication System and Communication Arrangement

1.  Log on to the Fiori Launchpad and open the *Communication Systems* app.
2.  Click on the *New* button to create a communication system. Provide a *System ID* and *System Name* and click *Create*.
3.  Scroll down to the *Technical Data* section and fill in your *Host Name* for SAP Analytics Cloud \(e.g. <xxx\>.cloud.sap.\) and *Port*: 443. *Save* your changes.
4.  Now open the *Communication Arrangements* app.
5.  Click the *New* button to create a new communication arrangement. Select `SAP_COM_0065`as the *Scenario* using the value help and provide an *Arrangement Name*, then click *Create*.
6.  In the *Common Data* section, select the *Communication System* you created in step 2.
7.  In the *Additional Properties* section, fill in the tenant ID of your SAC tenant.

    > ### Note:  
    > The tenant ID can be found in the main menu of the SAC tenant under *System* \> *About* \> *System Name*.

8.  In the *Outbound Services* section, check the *Service Status* for *UI Link Navigation* as active. The *Service Status* for *Retrieve Stories* should be unchecked. Click *Save*.

    > ### Note:  
    > Please note that retrieving stories is not yet supported.




### Connect to SAP Analytics Cloud

1.  Login to your SAC tenant. In the main menu, click *Connection*.
2.  Click the *+* icon \(*Add Connection*\). Under *Connect to Live Data*, select *SAP S/4HANA*.
3.  In the *New S/4HANA Live Connection* dialog, maintain the following details:
    -   Name and Description
    -   Connection Type: Direct Connection
    -   Host: <ID\>.abap-web.stagingaws.hanavlab.ondemand.com
    -   HTTPS Port: 443
    -   Client: 100
    -   Authentication Method: SAML Single Sign-on \(Standard Compliant\)

