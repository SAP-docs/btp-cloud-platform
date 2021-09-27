<!-- loioc6d983a392fe487e9b4f57a14cab23a0 -->

# Uploading Users to Identity Authentication

When you configure the Identity Authentication service as the SAML identity provider for your SAP Cloud for Customer system, you have to make sure that all users from SAP Cloud for Customer will have an identity record in the Identity Authentication service. For this purpose, you have to export the user details in a CSV file format and then use this CSV file to import these users into the Identity Authentication tenant of your company that will be used as the identity provider.



<a name="loioc6d983a392fe487e9b4f57a14cab23a0__context_www_ddx_k2b"/>

## Context

To upload the users of your SAP Cloud for Customer company into Identity Authentication, you export the user base and import it into Identity Authentication in CSV format.



<a name="loioc6d983a392fe487e9b4f57a14cab23a0__steps_xww_ddx_k2b"/>

## Procedure

1.  Export the SAP Cloud for Customer users and save the data in CSV format. For more information, see [Exporting SAP Cloud for Customer Users](Exporting_SAP_Cloud_for_Customer_Users_096332d.md).

2.  Import the users \(user names and user IDs\) in the Identity Authentication tenant with the CSV file you have exported from your SAP Cloud for Customer system. For more information, see [Importing or Updating SAP Cloud for Customer Users in Identity Authentication](Importing_or_Updating_SAP_Cloud_for_Customer_Users_in_Identity_Authentication_7c4ce35.md).


-   **[Exporting SAP Cloud for Customer Users](Exporting_SAP_Cloud_for_Customer_Users_096332d.md "Use this procedure to export SAP Cloud for
                            Customer users and
		save the user data in CSV format.")**  
Use this procedure to export SAP Cloud for Customer users and save the user data in CSV format.
-   **[Importing or Updating SAP Cloud for Customer Users in Identity Authentication](Importing_or_Updating_SAP_Cloud_for_Customer_Users_in_Identity_Authentication_7c4ce35.md "As a tenant administrator of the Identity
                                Authentication, you can import
		new users or update existing ones for a specific application with a CSV file, and send
		activtation e-mails to the users that have not received activation e-mails for that
		application so far.")**  
As a tenant administrator of the Identity Authentication, you can import new users or update existing ones for a specific application with a CSV file, and send activtation e-mails to the users that have not received activation e-mails for that application so far.

