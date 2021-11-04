<!-- loio3a7a0bece0d044eca59495965d8a0237 -->

# Developing Node.js in the Cloud Foundry Environment

This section offers selected information for Node.js development on the SAP BTP, Cloud Foundry environment and references to more detailed sources.



In this section about Node.js development, you get information about the buildpack supported by SAP and about the Node.js packages, and how you consume them in your application.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wzk_sdp_rdb"/>

## Node.js Buildpack

 SAP BTP uses the standard Node.js buildpack provided by Cloud Foundry to deploy Node.js applications.

To get familiar with the buildpack and how to deploy applications with it, take a look at the [Cloud Foundry Node.js Buildpack documentation](https://docs.cloudfoundry.org/buildpacks/node/index.html).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_ndw_lxz_pdb"/>

## SAP Node.js Packages

You can download and consume SAP developed Node.js packages via the SAP NPM Registry. There is an overview of Node.js packages developed by SAP, what they are meant for, and where they are included in the SAP HANA Developer Guide for XS Advanced Model. As the Node.js packages used for development in the Cloud Foundry are similar or the same as those in SAP HANA XS advanced, the links guide you to the SAP HANA Developer Guide for XS Advanced Model.

**Additional information:**

-   [The SAP NPM Registry](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/726e5d41462c4eb29eaa6cc83ff41e84.html)

-   [Standard Node.js Packages](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/54513272339246049bf438a03a8095e4.html)

-   [Download and Consume SAP Node.js Packages](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/ddcff14e28384810a352bb6512cd3448.html)




<a name="loio3a7a0bece0d044eca59495965d8a0237__section_w1d_tr1_krb"/>

## Supported Versions

The standard SAP `nodejs_buildpack` supports the following versions:

-   **Node.js 14** - recommended version
-   **Node.js 12** - it's supported but not recommended to use, due to its upcoming removal as per the [Node.js release roadmap](https://nodejs.org/en/about/releases/).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_o5d_4t1_krb"/>

## Release Notes

To see the latest news and updates about the Node.js System Buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/doc/43b304f99a8145809c78f292bfc0bc58/Cloud/en-US/98bf747111574187a7c76f8ced51cfeb.html?sel1=Node%5C.js%20System%20Buildpack&from=2021-01-01&to=2021-12-31).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wc2_5xz_pdb"/>

## Tips and Tricks

For selected tips and tricks for your Node.js development, see [Tips and Tricks for Node.js Applications](Tips_and_Tricks_for_Node.js_Applications_3a5fe88.md).

