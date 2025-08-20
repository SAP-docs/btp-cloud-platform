<!-- loioc9a406970bb84b37ae8a5a5620ae0739 -->

# Transporting Multitarget Applications in Cloud Foundry using CTS+

You can enable transport of SAP BTP applications and application content that is available as Multitarget Applications \(MTA\) using the Enhanced Change and Transport System \(CTS+\).



<a name="loioc9a406970bb84b37ae8a5a5620ae0739__prereq_uqs_5ts_wfb"/>

## Prerequisites

-   You have configured your SAP BTP subaccounts for transport with CTS+ as described in the document [How to...Configure SAP BTP, Cloud Foundry environment for CTS](https://help.sap.com/doc/9aad207e90fa4da793d34114113e9254/Cloud/en-US/HowToCTS%2B_Guide_SCP_CF.pdf).
-   The content that you want to transport can be made available as a Multitarget Application \(MTA\) archive as described in [Multitarget Applications in the Cloud Foundry Environment](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md).



<a name="loioc9a406970bb84b37ae8a5a5620ae0739__context_o2w_vts_wfb"/>

## Context

You use the Change and Transport System \(CTS\) of ABAP to transport and deploy your applications running on SAP BTP in the form of MTAs, for example, from development to a test or production subaccount. Proceed as follows to be able to transport an SAP BTP application:



<a name="loioc9a406970bb84b37ae8a5a5620ae0739__steps_m5c_grg_1y"/>

## Procedure

1.  Package the application in a Multitarget Application \(MTA\) archive using the Archive Builder Tool as described in [Defining Multitarget Application Archives](defining-multitarget-application-archives-33a0e0e.md).

2.  Attach the MTA archive to a CTS+ transport request as described in `How to...Configure SAP BTP, Cloud Foundry environment for CTS`.

3.  Trigger the import of an SAP BTP application as described in `How to...Configure SAP BTP, Cloud Foundry environment for CTS`.


**Related Information**  


[Resources on CTS+](https://wiki.scn.sap.com/wiki/pages/viewpage.action?pageId=448469096)

[Setting up a CTS+ enabled transport landscape in SAP BTP](https://blogs.sap.com/2017/03/29/setting-up-a-cts-enabled-transport-landscape-in-sap-cloud-platform/)

