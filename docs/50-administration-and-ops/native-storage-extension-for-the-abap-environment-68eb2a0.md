<!-- loio68eb2a0a5b2c486590331bff11d79c6f -->

# Native Storage Extension for the ABAP Environment

You can use SAP HANA Native Storage Extension for selected database tables to save in-memory storage.



<a name="loio68eb2a0a5b2c486590331bff11d79c6f__section_yfk_wmr_lyb"/>

## SAP HANA Native Storage Extension

SAP HANA Native Storage Extension \(NSE\) is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.

For more information, see [SAP HANA Storage Extension](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/4efaa94f8057425c8c7021da6fc2ddf5.html) in the SAP HANA administration guide.



<a name="loio68eb2a0a5b2c486590331bff11d79c6f__section_lh1_zmr_lyb"/>

## Enabling Native Storage Extension for Selected Database Tables

When you create or alter database tables in the ABAP Development Tools, go to the technical table settings. In the *Load Unit* field, select *Page Enforced*.

