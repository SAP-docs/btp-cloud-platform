<!-- loiofbbffaa814ac41eca313be6449bdf976 -->

# Session Timeout

Both web applications in the SAP Fiori Launchpad and in SAP Cloud Identity Services - Identity Authentication log out users after a certain period of inactivity. The length of this period can be changed independently for the two.



<a name="loiofbbffaa814ac41eca313be6449bdf976__section_krx_mjt_2bc"/>

## SAP Fiori Launchpad

Users are automatically signed out from the SAP Fiori Launchpad after a period of inactivity that is configurable in the *Manage Launchpad Settings* app.

> ### Note:  
> The following timeout parameters are visible in the *Manage Launchpad Settings* app. If you need to make changes, we suggest you keep the value of the `SESSION_TIMEOUT_INTERVAL_IN_MINUTES` parameter synchronized with the timeout in your Identity Authentication tenant so as to avoid inconsistencies in session management.
> 
> -   `SESSION_TIMEOUT_INTERVAL_IN_MINUTES`
> 
> -   `SESSION_TIMEOUT_REMINDER_IN_MINUTES`
> 
> -   `SESSION_TIMEOUT_STOP_DATA_REFRESH`

**Related Information**  


[Manage Launchpad Settings](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/22d573aead754b80abca18ec71872fb7.html "") :arrow_upper_right:

[Signing In and Signing Out](https://help.sap.com/viewer/fd8f9fda63fa4c7a92bb1d4b4ac5582c/Cloud/en-US/d8154df2a4d5457ba94334b01ff35117.html "") :arrow_upper_right:

[Configuring the Automatic Sign-Out](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/77c06e9742644485850714e2399277e3.html "For security reasons, a user should be signed-out automatically after a certain time of inactivity. You can set the time for automatic sign-out and define if a warning before sign-out is displayed.") :arrow_upper_right:

[Configure Session Timeout \(SAP Cloud Identity Services - Identity Authentication\)](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/5ca23e44ec384760a3f68fceb93c6ecc.html)

