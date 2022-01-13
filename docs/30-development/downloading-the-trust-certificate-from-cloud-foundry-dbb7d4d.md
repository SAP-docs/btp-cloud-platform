<!-- loiodbb7d4dcca15409e96f398d979f7a81e -->

# Downloading the Trust Certificate from Cloud Foundry

Download the trust certificate from the Cloud Foundry subaccount. You will need the certificate to set up OAuth 2.0 authentication to remote systems such as SAP S/4HANA Cloud.



<a name="loiodbb7d4dcca15409e96f398d979f7a81e__prereq_wrd_xtf_v2b"/>

## Prerequisites

You are a member of the corresponding global account. In addition, you are at least a subaccount viewer and destination admin \(or a subaccount admin, which covers both\).



<a name="loiodbb7d4dcca15409e96f398d979f7a81e__context_f4k_jrr_r2b"/>

## Context

As a first step to set up OAuth authentication for business services, you must establish a trust relationship between SAP S/4HANA Cloud and the Cloud Foundry subaccount containing your ABAP system. Therefore, you must download the certificate that uniquely identifies the Cloud Foundry subaccount as a trusted communication partner for remote systems such as SAP S/4HANA Cloud.



## Procedure

1.  As an administrator user, log on to the SAP BTP cockpit.

2.  Navigate to the subaccount containing your ABAP system in the Cloud Foundry environment.

3.  In the navigation area of the SAP BTP cockpit, choose *Connectivity* \> *Destinations*.

4.  Choose *Download Trust*.

5.  Save the trust certificate locally to your hard drive for later use.


