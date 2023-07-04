<!-- loiodde20aae98c84686a57b1e366acfae79 -->

# How to Activate or Deactivate the Correct Read Access Logging Configuration



## Context

To activate or deactivate Read Access Logging for certain apps, follow the steps described below.



## Procedure

1.  Go to the app for which you want to activate or deactivate Read Access Logging.

2.  Open the app and navigate to your user area \(*User Actions Menu*\).

3.  Click the *About* icon.

    -   If the app has an app ID such as `F1492`, please proceed with the steps in the section *Activating and Deactivating Read Access Logging for Apps with App ID*.


**Activating and Deactivating Read Access Logging for Apps with App ID:**

4.  Copy the app ID.

5.  Go to the [SAP Fiori apps reference library](https://fioriappslibrary.hana.ondemand.com/sap/fix/externalViewer/) and select *All Apps*.

6.  In the *Search* bar, paste the app ID you have just copied.

7.  Click the app entry in the results list.

8.  On the *App Details* screen, select *SAP S/4HANA Cloud* from the dropdown list.

9.  In the section *Implementation Information*, select your current SAP S/4HANA Cloud release.

10. Open the subsection *Configuration* and copy the OData service name/s and the OData service version of the app.

11. Go back to the SAP Fiori launchpad and open the app Read Access Logging Configuration.

12. Go to *Configuration*.

13. Select the channel *SAP Gateway*.

14. Paste the OData service name that you have just copied in the field *Service ID*.

    If you have copied more than one OData service name, you can add further *Service ID* fields to your search criteria.

15. Paste the OData service version that you have just copied in the field *Service Version*.

16. Click *Search*.

    In the search results list, you can see if Read Access Logging configurations exist for the service/s and, thus, for the app, and if the Read Access Logging is active or inactive.

17. To activate or deactive Read Access Logging, select the service/s, and click either *Activate* or *Deactivate*.

    Read Access Logging is now activated or deactivated for the respective app.


**Related Information**  


[How to Define What to Log](how-to-define-what-to-log-0eb5542.md "To define what to log, use a read access logging configuration.")

