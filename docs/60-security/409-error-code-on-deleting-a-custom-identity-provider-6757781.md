<!-- loio67577815d0874a738c3d41d9aa0d5837 -->

# 409 Error Code on Deleting a Custom Identity Provider



## Symptom

-   On deleting a custom identity provider \(origin: *sap.custom*\) in the SAP BTP cockpit, you get an error.
-   If you open the developer console \(F12\) and try again, you will see a more detailed error message.



## Reason and Prerequisites

-   This issue occurs when there are applications still present in the Identity Authentication service \(IAS\). For example, this can happen if you have created an identity service instance.



## Solution

1.  Check the IAS tenant for which you want to delete the trust configuration in the SAP BTP cockpit.
2.  You need to delete all the applications of the error message.

**Note**: Delete only those applications that you are sure are not needed anymore.

See [SAP Note 3148626](https://me.sap.com/notes/0003148626) for more information.

