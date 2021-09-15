<!-- loio587aec4da9e04aa1a5736996bffe452f -->

# Integrating SAP Analytics Cloud

SAP Analytics Cloud is used as analytics client consuming ABAP environment data exposed via ABAP environment analytical queries.



<a name="loio587aec4da9e04aa1a5736996bffe452f__prereq_xtl_hvd_k4b"/>

## Prerequisites

-   You have the *BI Admin* role in the SAP Analytics Cloud system. For more information, see [Requesting Roles](https://help.sap.com/viewer/00f68c2e08b941f081002fd3691d86a7/release/en-US/66c23636ffeb43a58b3b8e3ebc4488d5.html).

-   You have the *Administrator* role \(role template `ID SAP_BR_ADMINISTRATOR`\). For more information, see [Maintain Business Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8980ad05330b4585ab96a8e09cef4688.html).
-   Your end users' web browsers must be configured to:

    -   Allow pop-up windows from the SAP Analytics Cloud domain: `[*.]sapbusinessobjects.cloud`, if you'll be choosing the single sign-on \(SSO\) authentication method in step 2.
    -   Allow 3rd party cookies from the Tomcat server's domain. For example, in Internet Explorer 11, go to *Internet Options* \> *Security* \> *Trusted Sites*, add your domain name, then select *Enable Protected Mode*.



## Context

You can configure a live data connection in SAP Analytics Cloud and create an SAP Analytics Cloud model based on an ABAP environment analytical query to consume the result set in an SAP Analytics Cloud Story. The analytical query is delivered as CDS content and is exposed via the analytical engine and the InA protocol via the REST services under `/sap/bw/ina/...` to SAP Analytics Cloud.

SAP BTP destinations are created by the SAP Analytics Cloud app when you define an SAP Analytics Cloud connection of the type ABAP environment.

You set up the scenario using the following tasks:

1.  [Configure Identity Authentication](Configure_Identity_Authentication_70c9c8f.md)
2.  [Create a Communication System](Create_a_Communication_System_268ea65.md)
3.  [Create a Communication Arrangement](Create_a_Communication_Arrangement_0448835.md)
4.  [Configure Live Data Connection](Configure_Live_Data_Connection_e8cfea3.md)

-   **[Configure Identity Authentication](Configure_Identity_Authentication_70c9c8f.md "Configure your Identity Authentication tenant as the identity provider.")**  
Configure your Identity Authentication tenant as the identity provider.
-   **[Create a Communication System](Create_a_Communication_System_268ea65.md "You can create a communication system in the ABAP environment.")**  
You can create a communication system in the ABAP environment.
-   **[Create a Communication Arrangement](Create_a_Communication_Arrangement_0448835.md "You create a communication arrangement in the ABAP environment.")**  
You create a communication arrangement in the ABAP environment.
-   **[Configure Live Data Connection](Configure_Live_Data_Connection_e8cfea3.md "You configure a live data connection in SAP Analytics Cloud.")**  
You configure a live data connection in SAP Analytics Cloud.

