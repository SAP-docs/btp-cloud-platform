<!-- loio5eb70fb003954619b09224167a0afaa4 -->

# Landscape Portal



<a name="loio5eb70fb003954619b09224167a0afaa4__section_jgb_4qp_qmb"/>

## Context

Multitenancy allows providers to host different consumers \(tenants\) on a single shared system. But how do you, as a provider, keep track of all your tenants and systems? This is where the *Landscape Portal* comes in. The *Landscape Portal* acts as a central tool to allow service providers to perform lifecycle management operations such as building and updating product versions, configuring and deploying multitenant SaaS solutions, managing system hibernations, and more.



<a name="loio5eb70fb003954619b09224167a0afaa4__section_pfdb_bfm_rqp_qmb"/>

## Key Features

You can currently use the *Landscape Portal* to do the following:

-   get an overview of all your ABAP systems and tenants
-   create new namespaces and install them in your ABAP system
-   schedule \(regularly occuring\) system hibernation periods for specific systems
-   register specific ABAP systems for a pre-upgrade
-   restore deleted consumer tenants that are still in retention time
-   create test tenants
-   create support users to access consumer tenants
-   create a new product and register your product for your global accounts
-   build a product version via pipelines based on templates for different use cases \(e.g. new release deliveries, support packages, patches\)
-   check a product version to see if it's ready for delivery
-   deploy or update a product version in specific systems
-   configure and deploy your solution
-   monitor your operations in the Landscape Portal

> ### Note:  
> Keep in mind that a consumer subscription-based multitenancy is only possible in those systems in which you provide your software as a service \(SaaS\) solution to consumers, i.e. your production and test systems that are created via the ABAP Solution service on first subscription. It is not available in development systems. However, in development systems, in addition to your development tenant, you can create further test tenants within the *Landscape Portal* if required, see [Manage Test Tenants](manage-test-tenants-dd7d8e8.md).

**Related Information**  


[Accessing the Landscape Portal](accessing-the-landscape-portal-2e1e393.md)

