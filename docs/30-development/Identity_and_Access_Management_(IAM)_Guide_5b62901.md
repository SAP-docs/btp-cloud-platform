<!-- loio5b6290112008456b9e9400faebb8cd33 -->

# Identity and Access Management \(IAM\) Guide

This guide introduces you to the basic concepts and procedures for defining authorizations for business services that you create in the ABAP environment. You also learn to provide access to a Fiori application based on a business service.



<a name="loio5b6290112008456b9e9400faebb8cd33__section_xxr_1hr_cmb"/>

## Target Group

If you’re an SAP customer developer or partner developer and you create business services in the ABAP environment using ABAP Development Tools \(ADT\), this guide is for you. It guides you through an example of a business service based on a service binding. Note that http services work in a similar way.

In addition, the guide also covers activities that need to be performed by an administrator, such as assigning users to business roles.



<a name="loio5b6290112008456b9e9400faebb8cd33__section_fbd_1m4_nlb"/>

## Overview and Goals

The guide starts with an overview of the basic authorization concepts. It then leads you step by step through the design and implementation of your authorization model using an example.

Why should you care about access control and authorizations? You must know that every new service is automatically available to all developers in a development system, provided the system administrator has assigned them a role that is derived from the developer role `SAP_BR_DEVELOPER` \(which is typically the case\). However, business users in nondevelopment systems can only access the business service if a developer has developed the appropriate authorizations and an administrator grants the business users access for each relevant system. The same is true for communication users that are needed in scenarios where you work with an API business service \(inbound or outbound\) from or into the ABAP environment.

The guide outlines the following main scenarios how you can implement and provide authorizations for your services:

-   Under *Providing \(Unrestricted\) Access*, you learn how to provide users in a nondevelopment system access to the service.

    Providing unrestricted access is the simplest scenario with only a few steps. The access is unrestricted, though, which means, for example, that you can't differentiate between write and read access.

-   Under *Providing Access Based on Activities*, you learn how to implement access for different activities, for example, separate read and write authorizations.

-   Under *Providing Access Based on Field Values*, you learn how to fine-tune your access restrictions depending on field values.


OData services that you develop using ADT can also be consumed in SAP Fiori applications \(developed using the Business Application Studio\). In this guide, you also learn how to provide access to an SAP Fiori application that consumes a business service.

