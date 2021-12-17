<!-- loio252df8501f224b668e9d2b00ffd7b5e9 -->

# Access to System Structure SY

Access to the system structure `SY` is restricted to read access to the following components:

`BATCH`, `DBCNT`, `FDPOS`, `INDEX`, `LANGU`, `MSGID`, `MSGNO`, `MSGTY`, `MSGV1`, `MSGV2`, `MSGV3`, `MSGV4`, `SUBRC`, `TABIX`, and ``UNAME``.

> ### Note:  
> Access to all other components is **not** allowed because they are related to either obsolete or unsupported features.

For more information, see [ABAP System Fields](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm?file=abensystem_fields.htm) in the ABAP Keyword Documentation.

You can use class `CL_ABAP_CONTEXT_INFO` to retrieve information about the user session, for example, technical user name, business user name, time zone, and so on. The built-in function `utclong_current` generates a UTC time stamp from the current system time and the current system date in accordance with POSIX standards.

