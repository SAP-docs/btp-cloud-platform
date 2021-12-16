<!-- loio90b515d1b02f4a70bcf6c58a4a1155c6 -->

# ABAP System Sizing

This documentation describes the principles of how to perform system sizing for a custom application operated in the ABAP environment.



<a name="loio90b515d1b02f4a70bcf6c58a4a1155c6__section_bxc_nyl_frb"/>

## About this Documentation

This documentation introduces you to the following:

![From sizing fundamentals to sizing](images/ABAP_System_Sizing_Overview_e17ac02.png)

-   [Sizing Fundamentals](sizing-fundamentals-2c83fbf.md)
-   [Sizing Preparation](sizing-preparation-fb48310.md)
-   [Measurements for Sizing](measurements-for-sizing-186bc29.md)
-   [Sizing](sizing-00494e0.md)

1.  **Sizing fundaments**

    You learn more about sizing occasions and methods, especially about expert sizing and how sizing works for scalable applications in the ABAP environment.

2.  **Sizing preparation**

    Important preparatory steps are to identify the business processes that are relevant for sizing and to define test cases for them.

3.  **Measurements for sizing**

    You can perform measurements for sizing using the *Capture Request Statistics* app.

4.  **Sizing**

    You can use the *Perform System Sizing* app to perform the actual sizing of your ABAP system based on what you have measured before.


As the types of applications developed and operated in the ABAP environment are highly diverse, use this documentation as a rough guideline. This documentation assumes that in your business scenario, most business processes comprise the synchronous processing of single transactions. These business processes are the basis for measuring and calculating sizing values. If your business application mainly comprises other types of processing, for example, the mass processing of background jobs at specified dates and times, you need other sizing methods to achieve meaningful results.

This documentation focuses on the sizing of the ABAP layer. It doesn't include sizing for the SAP HANA database.

