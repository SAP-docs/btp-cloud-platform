<!-- loiof7a5543ecf8d47a4b8224f3b3aaed867 -->

# How to Handle Default Client Certificate Renewal

If you use the default client certificate for certificate-based authentication in outbound integration scenarios, you must update the trust between the systems when a new default client certificate is issued.



<a name="loiof7a5543ecf8d47a4b8224f3b3aaed867__section_qgh_4yz_xcc"/>

## Context

In outbound integration scenarios that use certificate-based authentication, the SAP BTP ABAP environment system needs to authenticate itself against the external system with a client certificate. You can use the default client certificate provided by SAP BTP ABAP environment for this purpose. This certificate will be rotated twice a year by SAP, regardless of its remaining validity.

The new certificate needs to be configured in your external system that communicates with SAP BTP ABAP environment.



<a name="loiof7a5543ecf8d47a4b8224f3b3aaed867__section_r2m_3yz_xcc"/>

## Rotation Process

The rotations occur every year on March 1 and September 1, and the process is divided into two stages.



<a name="loiof7a5543ecf8d47a4b8224f3b3aaed867__section_kgb_qyz_xcc"/>

## One Month Before Rotation

On the first day of the month preceding the rotation \(February 1 and August 1\), a new default client certificate will be issued.

The new default client certificate will be available for export in the **Maintain Client Certificates** app and will be labeled **Client Default**. The expiring certificate will be renamed to **Client Default Expiring**.

Once the new default client certificate is available, follow these steps:

1.  **Upload the New Certificate to the External System:**If the external system supports multiple certificates simultaneously, keep the old one until the replacement process is complete:

    -   Open the **Maintain Client Certificates** app.

    -   Export the new **Client Default** certificate in the format required by the external system.

    -   Upload the certificate to the external system.


2.  **Rotate the Used Certificate in the Communication System:**

    -   In the **Maintain Client Certificates** app you can see by which Communication Systems the **Client Default Expiring** certificate is used.

    -   Open the **Communication Systems** app.

    -   For each communication system using the **Client Default Expiring** certificate:

        -   Navigate to the **Users for Outbound Communication** section.

        -   Select the user associated with the **Client Default Expiring** certificate.

        -   In the dialog, change the**Client Certificate** value to **Client Default**.




> ### Note:  
> Switch to the new certificate as soon as possible. This ensures that if any issues arise, there will be time to troubleshoot within the 30-day overlap of the certificate validity periods.



<a name="loiof7a5543ecf8d47a4b8224f3b3aaed867__section_qt5_rzz_xcc"/>

## On the Rotation Date

Once the old certificate is rotated on either March 1 or September 1, it will be removed from the list in the **Maintain Client Certificates** app and all remaining Communication Systems using the old certificate will be migrated to the new Client Default certificate.



<a name="loiof7a5543ecf8d47a4b8224f3b3aaed867__section_dng_wzz_xcc"/>

## What Happens If You Don't Act

If you do not update your communication users and the new certificate in your external system, the outbound integration scenarios which use the default client certificate for authentication might break. You will get either the ***401 Unauthorized*** or the ***403 Forbidden*** HTTP status code message when trying to connect, depending on the implementation of the external system.

