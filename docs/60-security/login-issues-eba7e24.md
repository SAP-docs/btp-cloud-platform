<!-- loioeba7e242c1294a92ba04cc6d884e7099 -->

# Login Issues



## Symptom

You log on to SAP BTP via the Cloud Foundry CLI or the browser and you get an HTTP 401 error or see messages on the screen that indicate that your login attempt has failed.



## Reason and Prerequisites

Authentication in Cloud Foundry runs through the UAA service which tunnels the credentials supplied \(such as username and password\) towards a trusted Open ID Connect Identity Provider \(IdP\). SAP's default IdP is the SAP ID service, which is available at [https://accounts.sap.com](https://accounts.sap.com/) for SAP ID Service, or at[https://account.sap.com](https://account.sap.com/) for SAP Universal ID.

To narrow down the origin of the issue, you need to check the individual components involved in the login process.



## Solution



### Identify whether a second factor \(a one-time token\) is mandatory for this user/landscape

1.  Open the UAA service in the browser directly, depending on your region: For example, for the European region, go to [https://uaa.cf.eu10.hana.ondemand.com/](https://uaa.cf.eu10.hana.ondemand.com/) \(For an overview of all Cloud Foundry landscape URLs, see [Regions](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html#loiof344a57233d34199b2123b9620d0bb41)\).

    If you are redirected to [https://accounts.sap.com](http://accounts.sap.com/) asking for two-factor authentication and a passcode, a second factor in the form of a one-time TOTP token is mandatory.

2.  See [Activate TOTP Two-Factor Authentication](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/ab8a3237cd424a0c97b921100d263b8a.html?version=Cloud) for information about how to configure a device to generate TOTP tokens; for example, with an authenticator app.
3.  Log on to your Cloud Foundry environment using two-factor authentication.
    1.  Type `cf login`.
    2.  Enter your e-mail address.
    3.  Enter your password in the following format: <your global password\><one-time-token\>


