<!-- loio3a7a0bece0d044eca59495965d8a0237 -->

# Developing Node.js in the Cloud Foundry Environment

This section offers selected information for Node.js development on the SAP BTP, Cloud Foundry environment and references to more detailed sources.



You'll get information about the buildpack supported by SAP, the Node.js packages, and how to consume them in your application.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wzk_sdp_rdb"/>

## Node.js Community Buildpack

 SAP BTP uses the standard [Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack) provided by the Cloud Foundry community to deploy Node.js applications.

To get familiar with the buildpack and how to deploy applications with it, take a look at the [Cloud Foundry Node.js Buildpack documentation](https://docs.cloudfoundry.org/buildpacks/node/index.html).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_ndw_lxz_pdb"/>

## SAP Node.js Packages

You can download and consume SAP developed Node.js packages via the SAP NPM Registry. There is an overview of Node.js packages developed by SAP, what they are meant for, and where they are included in the SAP HANA Developer Guide for XS Advanced Model. See:

-   [Download and Consume SAP Node.js Packages](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/ddcff14e28384810a352bb6512cd3448.html)

-   [Standard Node.js Packages](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/54513272339246049bf438a03a8095e4.html)

-   [The SAP NPM Registry](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/726e5d41462c4eb29eaa6cc83ff41e84.html)




<a name="loio3a7a0bece0d044eca59495965d8a0237__section_kfn_ldv_f5b"/>

## Buildpack Versioning

The SAP BTP, Cloud Foundry environment provides one recent version of the Node.js buildpack as part of its system buildpacks. You can check this version by executing:

```
cf buildpacks
```

To learn about changes in Node.js versions and features, regularly check the latest [buildpack releases](https://github.com/cloudfoundry/nodejs-buildpack/releases) in the GitHub community page.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_w1d_tr1_krb"/>

## Supported Versions

The SAP `nodejs_buildpack` supports the following versions:

-   Node.js **14** – recommended version
-   Node.js **16** – supported but not recommended to use, due to current issues with the *@sap/xsjs* library. Therefore, if you use this library, bear in mind that it will be incompatible with the Node.js 16 runtime.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_o5d_4t1_krb"/>

## What's New

To see the latest news and updates about the Node.js System Buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=Node.js%20System%20Buildpack).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_iwr_zxf_hvb"/>

## Troubleshooting

-   Guided Answers: [Node.js Buildpack](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51218/?version=current)
-   SAP Note: [3100002](https://launchpad.support.sap.com/#/notes/3100002) *How to pin the new nodejs\_buildpack\_migratе solution*



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_jnl_4xz_pdb"/>

## Node.js Tutorial

The following tutorial will guide you through creating a Node.js application in Cloud Foundry Command Line Interface \(cf CLI\), consuming a Cloud Foundry service, and setting up authentication and authorization checks. See: [Create a Node.js Application via CF CLI](https://developers.sap.com/tutorials/btp-cf-buildpacks-node-create.html)



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wc2_5xz_pdb"/>

## Tips and Tricks

For selected tips and tricks for your Node.js development, see [Tips and Tricks for Node.js Applications](tips-and-tricks-for-node-js-applications-3a5fe88.md).

