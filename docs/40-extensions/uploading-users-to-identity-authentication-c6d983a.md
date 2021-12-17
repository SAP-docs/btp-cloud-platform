<!-- loioc6d983a392fe487e9b4f57a14cab23a0 -->

# Uploading Users to Identity Authentication

When you configure the Identity Authentication service as the SAML identity provider for your SAP Cloud for Customer system, you have to make sure that all users from SAP Cloud for Customer will have an identity record in the Identity Authentication service. For this purpose, you have to export the user details in a CSV file format and then use this CSV file to import these users into the Identity Authentication tenant of your company that will be used as the identity provider.



<a name="loioc6d983a392fe487e9b4f57a14cab23a0__context_www_ddx_k2b"/>

## Context

To upload the users of your SAP Cloud for Customer company into Identity Authentication, you export the user base and import it into Identity Authentication in CSV format.



<a name="loioc6d983a392fe487e9b4f57a14cab23a0__steps_xww_ddx_k2b"/>

## Procedure

1.  Export the SAP Cloud for Customer users and save the data in CSV format. For more information, see [Exporting SAP Cloud for Customer Users](exporting-sap-cloud-for-customer-users-096332d.md).

2.  Import the users \(user names and user IDs\) in the Identity Authentication tenant with the CSV file you have exported from your SAP Cloud for Customer system. For more information, see [Importing or Updating SAP Cloud for Customer Users in Identity Authentication](importing-or-updating-sap-cloud-for-customer-users-in-identity-authentication-7c4ce35.md).


