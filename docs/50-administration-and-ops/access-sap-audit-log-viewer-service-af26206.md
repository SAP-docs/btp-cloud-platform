<!-- loioaf26206cac0b4af0afb0367af4a57949 -->

# Access SAP Audit Log Viewer service 



<a name="loioaf26206cac0b4af0afb0367af4a57949__context_v5p_cvr_pdc"/>

## Context

To retrieve the audit logs for your subaccount using the Audit Log Viewer service, you need to have proper authorizations. See [https://docs.cloudfoundry.org/concepts/roles.html\#permissionsInformation](https://docs.cloudfoundry.org/concepts/roles.html#permissionsInformation), published on a non-SAP site.



<a name="loioaf26206cac0b4af0afb0367af4a57949__steps_ntt_1vr_pdc"/>

## Procedure

1.  Create a RoleCollection.

2.  Search for roles with the name "Auditlog\_Auditor" and select both entries with the following application identifiers:

    -   auditlog-management!b\*
    -   auditlog-viewer!t\*

3.  Assign the role to a user or create a rule to assign it to users based on the SAML Assertion coming from the IDP.

    > ### Note:  
    > Only account members with the Security Administrator role are authorized to edit application authorizations.


